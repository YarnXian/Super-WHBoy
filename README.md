Super WHBoy
=
Project Introduction
-
* It is written in easy language.
* There are some files: self starting.e is the program after the virus is added and started; main.e is the main body of the program, which runs only once;Killwhboy.e is the source code of antivirus program;killwhboy.exe Is the compiled antivirus program;unknow:Necessary files for compiling or running virus Ontology.For more information, see wiki.
* Viral behavior:
  * a. Release self boot file and icon file in the root directory of the system; 
  * b. Modify the registry to change the default icon of EXE file to the icon file released under the root directory;
  * c.Destroy the opening mode of some files so that they cannot be opened; 
  * d. Shut down the computer after 10 minutes;
  * e.Open a web page every 18 seconds; 
  * f.Close CMD, tasklist and regedit every 1 second; 
  * g.Destroy the hard disk host Main Boot Record.(It doesn't happen on the 1st day of every month.)
  * h.The screen will be blue on the 1st of every month.
* Detoxification method: first use disk tool to search for the lost partition and recover it, then rebuild the boot record and enter the system, then run the detoxification program. Or contact the author.If it is No.1, please adjust the time under PE or do not use the poisoned computer on the same day.
* The virus also has some vulnerabilities:
>You can call up the file extension through the folder option in the control panel, and change the suffix of CMD, tasklist or regedit to com, so that you can open the program and use it.
