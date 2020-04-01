# lwrpa-uip-moveoldfiles

This xaml is under giip RPA orchestrator.

Preparing related git repository

```sh
# Initialize giip environment
git clone https://github.com/LowyShin/giipAgentWin.git
# gip Agent for UiPath
git clone https://github.com/LowyShin/giipAgentUIP.git
# This repository
git clone https://github.com/LowyShin/lwrpa-uip-moveoldfiles.git
```

Add giip job

* JobType : json
  * Script Source
    * Be careful writing `\` of JSON standard format.
    ```json
    {
    "Execxaml" : "lwrpa-uip-moveoldfiles\\Main.xaml"
    , "PathSource" : "D:\\MyWork\\conf\\MoveOldFile.csv"
    , "PathTarget" : "D:\\MyWork\\WorkHistory\\work-old"
    }
    ```

* Write target path on `MoveOldFile.csv`
  * format : `Directory Path, Term`
    * Directory Path : CSV format not JSON(different special character like `\`)
    * Term : days
    ```
    D:\MyWork\WorkHistory\working, 8
    D:\Logs, 8
    ```
## File Structure

* Main.xaml
  * It called from giipAgentUIP and read giip job data and invoke MoveOldFiles.xaml
* MoveOldFiles.xaml
  * Main code of file move
