# VSCode配置C++开发环境

以配置C++环境为例，一通百通。

前置环境：安装并配置C/C++编译器MinGW-w64。

注：VSCode会保存打开前的环境变量，所以需要修改环境变量后再打开VSCode或修改后重启VSCode。

## 测试文件：

在工作区编写测试文件test.cpp。

```C++
#include <iostream>
using namespace std;
int main() {
    cout << "Hello World!" << endl;
    return 0;
}
```

其实配置好C/C++的环境变量之后既可以通过命令行编译运行C/C++文件了，以下步骤仅仅是为了方便调试添加的调试文件。且C/C++插件也很重要，是VSCode对C/C++的语言支持，需要安装。

## 调试文件：

调试C/C++程序需要用到gdb.exe程序，该程序在MinGW-w64安装路径的bin目录里，配置好环境变量直接使用即可。

官方文档：[Configuring C/C++ debugging](https://code.visualstudio.com/docs/cpp/launch-json-reference)

1. **点击左侧栏"运行与调试"运行测试文件。会弹出警告弹窗：**

   > 没有用于调试C++的扩展，我们是否应在市场中找到C++扩展？



2. **点击"查找C++扩展"，在扩展商店中找到相应C++扩展并下载。**

   > 名称：C/C++`v1.5.1`
   >
   > 描述：C/C++ IntelliSense, debugging, and code browsing.



3. **重复第一步，点击"运行与调试"后在VSCode顶部选择 C++(GDB/LLDB)，再选择 g++.exe， 会自动生成 launch.json。**

   ```json
   {
       //使用 IntelliSense 了解相关属性。 
       //悬停以查看现有属性的描述。
       //欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
       "version": "0.2.0",
       "configurations": [
           {
               "name": "g++.exe - 生成和调试活动文件",                           // 配置名称，将会在启动配置的下拉菜单中显示  
               "type": "cppdbg",                                             // 配置类型，这里只能为cppdbg  
               "request": "launch",                                          // 请求配置类型，可以为launch（启动）或attach（附加）  
               "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",  // 将要进行调试的程序的路径  
               "args": [],                                                   // 程序调试时传递给程序的命令行参数，一般设为空即可  
               "stopAtEntry": false,                                         // 设为true时程序将暂停在程序入口处，一般设置为false  
               "cwd": "${fileDirname}",                            // 调试程序时的工作目录，一般为${workspaceFolder}即代码所在目录  
               "environment": [],
               "externalConsole": false,                           // 调试时是否显示控制台窗口，一般设置为true显示控制台   
               "MIMode": "gdb",
                // miDebugger的路径，注意这里要与MinGw的路径对应  
               "miDebuggerPath": "D:\\Program Files\\mingw-w64-v8.1.0\\mingw64\\bin\\gdb.exe",
               "setupCommands": [
                   {
                       "description": "为 gdb 启用整齐打印",
                       "text": "-enable-pretty-printing",
                       "ignoreFailures": true
                   }
               ],
               "preLaunchTask": "C/C++: g++.exe 生成活动文件"      //和tasks中label保持一致
           }
       ]
   }
   ```

   生成的同时会启动调试程序，同时在终端可以看到输出：“Hello World！”

   

4. **上述步骤一般会同时生成tasks.json文件**，如果没有生成可以返回test.cpp文件，按F5进行调试，会弹出找不到任务"task g++"，选择 "配置任务"，会自动生成 tasks.json 文件。

   ```json
   {
       "tasks": [
           {
               "type": "cppbuild",
               "label": "C/C++: g++.exe 生成活动文件",  // 这里应该与launch.json的preLaunchTask保持一致
               "command": "D:\\Program Files\\mingw-w64-v8.1.0\\mingw64\\bin\\g++.exe",
               "args": [   // 编译参数
                   "-g",
                   "${file}",
                   "-o",
                   "${fileDirname}\\${fileBasenameNoExtension}.exe"
               ],
               "options": {
                   "cwd": "${fileDirname}"
               },
               "problemMatcher": [
                   "$gcc"
               ],
               "group": {
                   "kind": "build",
                   "isDefault": true
               },
               "detail": "调试器生成的任务。"
           }
       ],
       "version": "2.0.0"
   }
   ```

   完成！现在就可以按F5对文件进行调试了。



## 关于：

关于"prelaunchtask g++已终止,退出代码为1"，排除tasks.json文件生成问题，请不要在待调试文件的路径及文件名中出现中文！！！

关于"Unable to start debugging. Program path XXX is missing or invalid"，同样的，VSCode调试无法支持中文路径，同上路径中请不要出现中文。

硬刚方法一：[使用vscode调试中文路径文件出错的解决办法](https://blog.csdn.net/xdfsa/article/details/105174254)

硬刚方法二：[关于VSCode调试无法支持中文路径的曲线救国方法](https://blog.csdn.net/weixin_42067548/article/details/108304307) （推荐）

