# `crontab`

### Purpose 

Submits, edits, lists or removed cron jobs.

### Syntax
`crontab` [`-e` [UserName]| `-l` [UserName] | `-r` [UserName] | `-v` [UserName] | File ]] 

### Description
The crontab command submits, edits, lists, or removes cron jobs. A cron job is a command run by the cron daemon at regularly scheduled intervals. To submit a cron job, specify the crontab command with the -e flag. The crontab command invokes an editing session that allows you to create a crontab file. You create entries for each cron job in this file. Each entry must be in a form acceptable to the cron daemon.

When you finish creating entries and exit the file, the crontab command copies it into the `/var/spool/cron/crontabs` directory and places it in a file named for your current user name. If a file with your name already exists in the crontabs directory, the crontab command overwrites it.

Alternatively, you can create a **crontab** file by specifying the *File* parameter. If the file exists, it must be in the format the cron daemon expects. If the file does not exist, the crontab command invokes the editor. If the EDITOR environment variable exists, the command invokes the editor it specifies. Otherwise, the crontab command uses the vi editor.

To list the contents of your crontab file, specify the `crontab` command with the `-l` flag. To remove an existing file, use the `-r` flag.

The optional **UserName** parameter can be used by the owner of the crontab file or by the root user to edit, list, remove, or verify the status of the cron jobs for the specified user. If the UserName is invalid, an error message is generated and the program exits.

If the optional UserName parameter is not specified, the crontab flags are available for the root user and the current user.

<br>

### Security
Only the root user or the owner of the crontab file can use UserName following the -e, -l, -r, and -v flags to edit, list, remove, or verify the crontab file of the specified user.

- **The cron Daemon**

    The cron daemon runs commands according to the crontab file entries. Unless you redirect the output of a cron job to standard output or error, the cron daemon mails you any command output or errors. If you specify a cron job incorrectly in your crontab file, the cron daemon does not run the job.

    The cron daemon examines crontab files only when the cron daemon is initialized. When you make changes to your crontab file using the crontab command, a message indicating the change is sent to the cron daemon. This eliminates the overhead of checking for new or changed files at regularly scheduled intervals.

- **Controls on Using the crontab Command**

    The `/var/adm/cron/cron.allow` and `/var/adm/cron/cron.deny` files control which users can use the crontab command. A root user can create, edit, or delete these files. Entries in these files are user login names with one name to a line. If your login ID is associated with more than one login name, the crontab command uses the first login name that is in the `/etc/passwd` file, regardless of which login name you might actually be using. Also, to allow users to start cron jobs, the daemon attribute in the `/etc/security/user` file should be set to `TRUE` , using the `chuser` command.

    The following is an example of an cron.allow file:

    ```
    root
    nick
    dee
    sarah
    ```

    If the cron.allow file exists, only users whose login names appear in it can use the crontab command. The root user's log name must appear in the cron.allow file if the file exists. A system administrator can explicitly stop a user from using the crontab command by listing the user's login name in the cron.deny file. If only the cron.deny file exists, any user whose name does not appear in the file can use the crontab command.

- **A user cannot use the crontab command if one of the following is true:**

  - The cron.allow file and the cron.deny file do not exist (allows root user only).
  - The cron.allow file exists but the user's login name is not listed in it.
  - The cron.deny file exists and the user's login name is listed in it.

    If neither the cron.allow nor the cron.deny file exists, only someone with root user authority can submit a job with the crontab command.

<br>

### The crontab File Entry Format

A crontab file contains entries for each cron job. Entries are separated by newline characters. Each crontab file entry contains six fields separated by spaces or tabs in the following form:

  `minute  hour  day_of_month  month  weekday  command`

These fields accept the following values:
|Item|Description|
|---|---|
|minute|0 through 59
|hour|	0 through 23
|day_of_month|	1 through 31
|month|	1 through 12
|weekday|	0 through 6 for Sunday through Saturday
|command|	a shell command

You must specify a value for each field. Except for the command field, these fields can contain the following:

- A number in the specified range. To run a command in May, specify 5 in the month field.
- Two numbers separated by a dash to indicate an inclusive range. To run a cron job on Tuesday through Friday, place 2-5 in the weekday field.
- A list of numbers separated by commas. To run a command on the first and last day of January, you would specify 1,31 in the day_of_month field.
- A combination of two numbers separated by a dash to indicate an inclusive range and a list of numbers separated by commas can be used in conjunction. To run a command on the first, tenth to sixteenth and last day of January, you would specify 1,10-16,31 in the day_of_month field. The above two points can also be used in combination.
- An * (asterisk), meaning all allowed values. To run a job every hour, specify an asterisk in the hour field.

<br>

### Files

|File|Description|
|---|---|
|`/var/adm/cron/FIFO`|A named pipe that sends messages to the cron daemon when new jobs are submitted with the crontab or at command.|
|`/var/spool/cron/crontabs`|Specifies the crontab spool area.
|`/var/adm/cron/cron.allow`|Specifies a list of users allowed access to the crontab command.|
|`/var/adm/cron/cron.deny`|Specifies a list of users denied access to the crontab command.|

<br><br>

### Usage Examples

1. To copy a file called mycronjobs into the `/var/spool/cron/crontabs` directory, enter the following:
    ```sh
    crontab mycronjobs
    ```

    The file will be copied as:

    ```sh
    /var/spool/cron/crontabs/<username>
    ```

    where <username> is your current user name.

2. To write the time to the console every hour on the hour, enter:

    ```sh
    0 * * * * echo The hour is `date` . 
    >/dev/console
    ```

3. To run the calendar command at 6:30 a.m. every Monday, Wednesday, and Friday, enter:

    ```sh
    30 6 * * 1,3,5 /usr/bin/calendar
    ```

4. To run the calendar command every day of the year at 6:30, enter the following:

    ```sh
    30 6 * * * /usr/bin/calendar
    ```

5. To run a script called maintenance every day at midnight in August, enter the following:
  
    ```sh
    0 0 * 8 * /u/harry/bin/maintenance
    ```

6. To define text for the standard input to a command, enter:
  
    ```sh
    0 16 * 12 5 /usr/sbin/wall%HAPPY HOLIDAY!%Remember to turn in your time card.
    ```

    The text following the % (percent sign) defines the standard input to the wall command as:
  
    ```txt
    HAPPY HOLIDAY!
  
    Remember to turn in your time card.
    ```