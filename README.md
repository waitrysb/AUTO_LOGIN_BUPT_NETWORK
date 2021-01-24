* 通电自动启动电脑需要修改bios设置，可搜到
* 将远程桌面软件设置为开机自启动
* windows下开机自启动脚本参考：https://blog.csdn.net/hailang86/article/details/103701329
* windows下自动登录脚本
```
@echo off
:loop
for /f %%i in ('curl --connect-timeout 3 -m 5 -I "www.dy2018.com" 2^>^&1 ^| findstr /c:"301" /c:"200" /c:"curl"') do set res=%%i
echo res=!res!
echo %res%
if %res% == HTTP/1.1 (
    echo access ipv4 successful
) else (
    curl -X POST -d  "user=*******&pass=******" http://10.3.8.211/login
    echo login bupt
)
ping -n 3 127.1>nul
goto loop
```