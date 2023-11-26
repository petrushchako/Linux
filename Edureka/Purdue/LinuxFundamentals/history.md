#### History

* **history** command generates list of commands executed previously in terminal session
* If you have to much output generates, you can use one of two following options:
  - Pipe content into **more** command:
    ```shell
    history | more
    
    ```
  - Output content into multiple files using **split**:
    ```shell
      history | split -l 100 -d - history_chunk
    
    ```
    Note: "-d" will add 01-02-etc at the end of a file. "-" will add letters a-b-c-etc
