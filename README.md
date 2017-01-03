# PowershellShortcutArgs

## Description

**ShortcutArgs**


This project was made to add the ability to parse files to powershell script that is not running off of a '.ps1' file. The file itself can be parsed to a windows shorcut that refrences powershell.


The reason for this could be that script execution is not enabled on the target device and therfore you cannot use '.ps1' files, instead we simply make a shorcut that points to powershell.exe and parse the code straight from the text box.

**Example of Windows Powershell Shortcut:**


- Create a new windows shortcut.
- In the 'Target' text box, simply type: powershell.exe
- After this you can type any code (within the shortcut character limit), that you would like to be executed when you click this shortcut.
  - This could be anything from starting command prompt with certain commands pre-entered (similar to a batch file), or it could start a custom application and notify the user with Write-Output.


The problem occurs when you want to actually provide that shortcut with a file, this could be to read the contents or maybe to just get the name and add it to a list of some sort. Because of that, I have created a semi-hacky way of dealing with file parsing to powershell shortcuts, you can use one of the pre-made shortcuts in the 'Shortcuts' zip folder or make your own following one as a template.



## Bugs / Potential Problems

Because you are parsing the file path as no particular type (e.g. it is not a string or a path), a form of command injection is present, for example: if the file you are trying to load is named like this: **helloworld.txt;Write-Output 'Command Injection'**, then the script will try and process the file 'helloworld.txt' but it will also execute the following command 'Write-Output' with the supplied arguments, I cannot currently find a way around this but bare this in mind if you would not like to face that issue.
