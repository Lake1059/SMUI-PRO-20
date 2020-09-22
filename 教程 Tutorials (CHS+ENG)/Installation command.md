## 安装命令 Installation command
安装命令（常简称为：命令）是管理器的核心内容，程序本身并不会做什么  
程序通过用户编写的命令才能知道 MOD 要如何安装以及有没有安装

The installation command (often abbreviated as: command) is the core content of the manager, the program itself does not do anything.  
The program knows how to install the MOD and whether it is installed through the commands written by the user.

所有 MOD 就两大类  
All mods fall into two categories
|  类型 Type  | 传统安装方法 Traditional installation method |
|  :----  | :----  |
| SMAPI MOD  | 将 manifest.json 文件所在的文件夹复制到游戏 Mods 文件夹<br>Copy the folder where the manifest.json file is located to the game Mods folder |
| XNB MOD  | 替换游戏的 xnb 文件<br>Replace the xnb file of the game |

安装命令根据这些安装方法设计并扩展使得能够应对各种情况  
如果合理使用，你会发现管理器不仅仅能够管理 MOD，甚至可以做些其他的

The installation commands are designed and expanded according to these installation methods to be able to deal with various situations.  
If used reasonably, you will find that the manager can not only manage mods, but can even do other things.

### 书写格式 Writing format
+ 命令是从上到下顺序执行的代码段，命令的参数紧跟着下一行
+ 所有命令都不区分大小写并且就算你多打了空格也可以正常识别
+ 但是参数不可以，因为参数是路径的一部分，所以不允许有任何字符错误
+ 一个命令和另一个命令之间可以空行以帮助增加可读性
+ 但是命令与它的参数之间不允许空行，必须紧挨着下一行
+ Command is a code segment executed sequentially from top to bottom, and the parameters of the command follow the next line
+ All commands are not case sensitive and can be recognized normally even if you type more spaces
+ But the parameter is not allowed, because the parameter is part of the path, so no character errors are allowed
+ There can be a blank line between one command and another to help increase readability
+ But no blank line is allowed between the command and its parameters, it must be next to the next line

### 文件 File
+ 安装命令保存于该项目录下的 UI_Code 无后缀文件中
+ 使用 UTF-8 编码（BOM 不影响），使用 CRLF 换行符
+ 不需要手动打开，请在管理器中编辑，程序能自动处理上述要求
+ The installation command is saved in the UI_Code file without suffix under the directory
+ Use UTF-8 encoding (BOM does not affect), use CRLF newline
+ No need to open manually, please edit in the manager, the program can automatically handle the above requirements

### 所有命令 All commands
这些表格显示了 SMUI PRO 20 中的所有命令，上一代的字体命令已不再支持  
These tables show all the commands in SMUI PRO 20, the previous generation font commands are no longer supported.
| 动作命令<br>Action command | 简单描述<br>Quick description |
|  :---- | :----  |
| CDCP | 将文件夹复制到游戏 Mods 文件夹<br>Copy the folder to the game Mods folder |
| CDCP-EXP | CDCP 的变体，将文件夹复制到游戏的任意新位置<br>A variant of CDCP, copy the folder to any new location in the game |
| CDAP | 覆盖游戏 Mods 文件夹中的同名文件夹<br>Overwrite the folder with the same name in the game Mods folder |
| CDRF | 替换游戏的单个文件<br>Replace a single file of the game |
| CDRF-SHA | CDRF 的变体，通过计算 SHA256 来判断是否已安装<br>A variant of CDRF, which calculates SHA256 to determine whether it is installed |
| CDRF-EXT | CDRF 的变体，只要文件存在就认定已安装<br>A variant of CDRF, as long as the file exists, it is assumed to be installed |
| CDVD | 覆盖游戏的 Content 文件夹<br>Overwrite the Content folder of the game |

| 控制命令<br>Control commands | 简单描述<br>Quick description |
|  :---- | :----  |
| UN-OFF | 声明禁止执行卸载操作<br>Declare that uninstallation is prohibited |

| 条件判断命令<br>Conditional judgment command | 简单描述<br>Quick description |
| :----  | :----  |
| RqFolder | 当指定的文件夹存在时才能继续操作<br>The operation can only be continued when the specified folder exists |
| RqFolder-IN | RqFolder 的变体，功能相同，仅在安装时生效<br>A variant of RqFolder, which has the same functions and only takes effect when installed |
| RqFolder-UN | RqFolder 的变体，功能相同，仅在卸载时生效<br>A variant of RqFolder, which has the same functions and only takes effect when uninstalled |
| RqFile | 当指定的文件存在时才能继续操作<br>The operation can only be continued when the specified file exists |
| RqFile-IN | RqFile 的变体，功能相同，仅在安装时生效<br>A variant of RqFile, which has the same function and only takes effect during installation |
| RqFile-UN | RqFile 的变体，功能相同，仅在卸载时生效<br>A variant of RqFile, which has the same function and only takes effect when uninstalled |

## 所有命令详细说明 Detailed description of all commands
注意：程序判断每个项使用哪种安装方法以及有没有安装时只会以第一个动作命令为准  
在有多个动作命令的情况下请合理安排命令顺序，合理的命令顺序往往能带来优质的体验

## CDCP
### 作用 Function 
将文件夹复制到游戏的 Mods 文件夹，并支持读取清单信息，只要文件夹存在就判定为已安装  
Copy the folder to the Mods folder of the game, and support reading the manifest, as long as the folder exists, it will be judged as installed.  
### 注意 Note 
在使用此命令时文件夹不能套娃，否则程序无法读取文件夹下的 manifest.json 清单文件  
When using this command, the folder cannot be set with multiple folders, otherwise the program cannot read the manifest.json manifest file in the folder.  
```
CDCP
[参数1：要复制的文件夹，从当前位置算起的相对路径]

CDCP
[Parameter 1: The folder to be copied, the relative path from the current location]
```
### 举例 For example
**[Content Patcher](https://www.nexusmods.com/stardewvalley/mods/1915)**
```
CDCP
ContentPatcher
```

## CDCP-EXP
将文件夹复制到游戏文件夹的任何位置，只要文件夹存在就判定为已安装  
这个命令适用于原本游戏没有的文件夹，切勿用于游戏本身就有的文件夹，沙雕后果自负

Copy the folder to any location of the game folder, as long as the folder exists, it will be judged as installed.  
This command is suitable for folders that the original game does not have. Do not use it for folders that the game itself has, otherwise you will be at your own risk.
```
CDCP-EXP
[参数1：要复制的文件夹，从当前位置算起的相对路径]
[参数2：目标文件夹位置，从游戏目录算起的相对路径]

CDCP-EXP
[Parameter 1: The folder to be copied, the relative path from the current location]
[Parameter 2: Target folder location, relative path from the game directory]
```

## CDAP
覆盖在 Mods 中已存在的同名文件夹，不支持卸载，无法判断已安装，自动检查是否已经存在要被覆盖的文件夹  
Overwrite the existing folder with the same name in Mods. Uninstallation is not supported.  
It cannot be judged to be installed. It will automatically check whether there is a folder to be overwritten.
```
CDAP
[参数1：被覆盖的同名文件夹，从当前位置算起的相对路径]

CDAP
[Parameter 1: The folder with the same name to be overwritten, the relative path from the current location]
```

## CDRF
将文件复制或替换到游戏文件夹中的任何位置的单个文件，无法判断已安装  
Copy or replace the file to a single file anywhere in the game folder, unable to determine whether it is installed.
```
CDRF
[参数1：要复制的文件，从当前位置算起的相对路径]
[参数2：目标文件位置，从游戏目录算起的相对路径]

CDRF
[Parameter 1: The file to be copied, the relative path from the current location]
[Parameter 2: Target file location, relative path from the game directory]
```
### 变体 Variants
要使 CDRF 实现判断是否已复制或替换文件，请使用它的变体  
To enable the CDRF implementation to determine whether a file has been copied or replaced, use its variant.

**CDRF-SHA**：通过计算文件的 SHA256 效验值来判断是否已安装  
**CDRF-EXT**：只要目标文件存在就判定为已安装

**CDRF-SHA**: Determine whether it is installed by calculating the SHA256 validation value of the file.  
**CDRF-EXT**: As long as the target file exists, it is judged to be installed.

CDRF-EXT 适用于原本游戏没有的文件，切勿用于游戏本身就有的文件，沙雕后果自负  
CDRF-EXT is suitable for files that the original game does not have.  
Do not use it for files that the game itself has, otherwise the consequences.

## CDVD
使用一个 Content 文件夹去覆盖游戏的 Content 文件夹，最适合用来替换一大堆 xnb 文件  
Use a Content folder to overwrite the game's Content folder, which is most suitable to replace a lot of xnb files.
```
CDVD
```
要使用此命令，请创建一个 Content 文件夹，将你要替换的 xnb 文件按照原游戏的相对位置放置，然后在配置项窗口中拖入这个你创建的 Content 文件夹  
To use this command, create a Content folder, place the xnb file you want to replace in the relative position of the original game.  
And then drag the Content folder you created in the configuration item window

## UN-OFF
禁止执行卸载操作，如果你有特殊需求的话。在进行卸载操作时，此命令之后的所有命令都不会被执行  
It is forbidden to perform uninstallation, if you have special needs. During the uninstall operation, all commands after this command will not be executed
```
UN-OFF
```

### RqFolder
在游戏文件夹中指定一个文件夹路径，必须存在此文件夹才能继续操作  
Specify a folder path in the game folder, this folder must exist to continue operation
```
RqFolder
[参数1：指定的文件夹，从游戏目录算起的相对路径]

RqFolder
[Parameter 1: The specified folder, the relative path from the game directory]
```
### 变体 Variants
如果要只在安装或者卸载时才进行检查，请使用它的变体  
If you want to check only when installing or uninstalling, please use its variant.

**RqFolder-IN**：只在安装时生效  
**RqFolder-UN**：只在卸载时生效  

**RqFolder-IN**: only takes effect during installation  
**RqFolder-UN**: only takes effect when uninstalling

## RqFile
在游戏文件夹中指定一个文件路径，必须存在此文件才能继续操作
Specify a file path in the game folder, this file must exist to continue operation.
```
RqFolder
[参数1：指定的文件，从游戏目录算起的相对路径]

RqFolder
[Parameter 1: The specified file, the relative path counted from the game directory]
```
### 变体 Variants
If you want to check only when installing or uninstalling, please use its variant. 

**RqFile-IN**：只在安装时生效  
**RqFile-UN**：只在卸载时生效  

**RqFile-IN**: only takes effect during installation  
**RqFile-UN**: only takes effect when uninstalling
