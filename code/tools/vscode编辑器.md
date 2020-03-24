#### 调试c#
如果调试c# ，可以安装 C# for Visual Studio Code (powered by OmniSharp) 插件
启动调试，失败的话，修改launch.json 文件下的 program 指定目录

```
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": ".NET Core Launch (console)",
            "type": "coreclr",
            "request": "launch",
            "preLaunchTask": "build",
            "program": "${workspaceRoot}/bin/Debug/netcoreapp2.0/myweb.dll", //此处
            "args": [],
            "cwd": "${workspaceRoot}",
            "stopAtEntry": false,
            "console": "internalConsole"
        },
        {
            "name": ".NET Core Launch (web)",
            "type": "coreclr",
            "request": "launch",
            "preLaunchTask": "build",
            "program": "${workspaceRoot}/bin/Debug/netcoreapp2.0/myweb.dll", //此处
            "args": [],
            "cwd": "${workspaceRoot}",
            "stopAtEntry": false,
            "launchBrowser": {
                "enabled": true,
                "args": "${auto-detect-url}",
                "windows": {
                    "command": "cmd.exe",
                    "args": "/C start ${auto-detect-url}"
                },
                "osx": {
                    "command": "open"
                },
                "linux": {
                    "command": "xdg-open"
                }
            },
            "env": {
                "ASPNETCORE_ENVIRONMENT": "Development"
            },
            "sourceFileMap": {
                "/Views": "${workspaceRoot}/Views"
            }
        },
        {
            "name": ".NET Core Attach",
            "type": "coreclr",
            "request": "attach",
            "processId": "${command:pickProcess}"
        }
    ]
}

```

vscode 找不到路径的时候，${workspaceRoot} 改成 绝对路径试试
#### vscode安装插件或者环境 无效，重启试试

#### 乱码问题
https://github.com/Microsoft/vscode/issues/10108

1.解决vccode调试控制台官方内容乱码
点击菜单栏的任务 配置任务 点击 打开task.json文件
修改task.json
为以下内容就好了
{ "version": "0.1.0", "tasks": [ { "taskName": "build", "command": "cmd", "suppressTaskName": true, "args": [ "/c chcp 65001 >nul && dotnet build ${workspaceRoot}/mailserver.csproj" ], "isBuildCommand": true, "problemMatcher": "$msCompile" } ] }
2.解决控制台自己输出的乱码
static void Main(string[] args) { //解决输出中文乱码的问题 Console.OutputEncoding = Encoding.UTF8; // Console.WriteLine("Message :{0} ", "請求成功1"); }