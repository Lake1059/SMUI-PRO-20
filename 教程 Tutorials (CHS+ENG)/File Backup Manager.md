CDRF（含变体） 和 CDVD 支持卸载自动还原，在使用之前你应该提前备份要被替换的文件，否则程序在卸载时直接删除目标文件
如果文件已经被删了，请通过 Steam 检查文件完整性

CDRF (including variants) and CDVD support automatic restoration after uninstallation.  
You should back up the files to be replaced before use, otherwise the program will directly delete the target files when uninstalling. 
If the file has been deleted, please check the integrity of the file through Steam

从开始菜单或在主程序中的 “应用”菜单中打开文件备份管理器
自定义备份规则文件和备份的文件均保存在 C 盘的本地资料夹（C:\Users\Public\SMUI PRO 20）下（可从内容菜单中打开本地资料夹）
上一代产品的规则文件可以直接在这一代中使用

Open the file backup manager from the start menu or from the "Application" menu in the main program
Customized backup rule files and backed up files are saved in the Local Data folder (C:\Users\Public\SMUI PRO 20) on the C disk (you can open the local folder from the Content menu)
The rule file of the previous generation product can be used directly in this generation

要创建自定义规则文件，请在本地资料夹的 BackupRules 文件夹中创建任意后缀的文本文档，使用 UTF-8 编码
在其中输入从游戏目录开始的相对路径，程序会自动识别是文件夹还是文件（文件夹具有优先级别）

To create a custom rule file, please create a text file with any suffix in the BackupRules folder of the Local Data folder, using UTF-8 encoding
Enter the relative path starting from the game directory, the program will automatically identify whether it is a folder or a file (folders have priority)

备份的文件位于本地资料夹的 GameBackup 文件夹中  
The backed up files are located in the GameBackup folder of the Local Data folder.
