# WinBoost
Execute Mimikatz with different technique.

This PoC illustrate different technique to successfully excute Mimikatz with process injection:

1) Embed Mimikatz as C# class, Mimikatz is converted to shellcode and converted to 3 digits format
2) Each syscall is obfuscated
3) Use C# Console.WriteLine to masquerade our intention

BEFORE COMPILING, IF ONE CHANGE SOURCE CODE, REMEMBER TO CHANGE: int idx = 0x4aa73; the idx represent the index where Mimikatz begins
Compile as .dll use https://github.com/mobdk/compilecs 
Compile as .exe change DllMain to Main and: csc.exe /platform:x64 /target:exe /unsafe winboost.cs

Execution:

Start one new cmd like this:

cmd version

from another run rundll32 winboost.dll,DllMain

ZwGetNextProcess is used to find process cmd.exe with argument version, ZwGetNextThread is used after the rigth PID is found.

