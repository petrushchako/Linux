# `chrontab`

### Purpose 

Submits, edits, lists or removed cron jobs.

### Syntax
`chrontab` [`-e` [UserName]| `-l` [UserName] | `-r` [UserName] | `-v` [UserName] | File ]] 

### Description
The crontab command submits, edits, lists, or removes cron jobs. A cron job is a command run by the cron daemon at regularly scheduled intervals. To submit a cron job, specify the crontab command with the -e flag. The crontab command invokes an editing session that allows you to create a crontab file. You create entries for each cron job in this file. Each entry must be in a form acceptable to the cron daemon.

When you finish creating entries and exit the file, the crontab command copies it into the `/var/spool/cron/crontabs` directory and places it in a file named for your current user name. If a file with your name already exists in the crontabs directory, the crontab command overwrites it.

Alternatively, you can create a **crontab** file by specifying the *File* parameter. If the file exists, it must be in the format the cron daemon expects. If the file does not exist, the crontab command invokes the editor. If the EDITOR environment variable exists, the command invokes the editor it specifies. Otherwise, the crontab command uses the vi editor.

To list the contents of your crontab file, specify the `crontab` command with the `-l` flag. To remove an existing file, use the `-r` flag.

The optional **UserName** parameter can be used by the owner of the crontab file or by the root user to edit, list, remove, or verify the status of the cron jobs for the specified user. If the UserName is invalid, an error message is generated and the program exits.

If the optional UserName parameter is not specified, the crontab flags are available for the root user and the current user.