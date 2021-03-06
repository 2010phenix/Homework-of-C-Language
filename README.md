# Homework-of-C-Language
C/C++ code examples of my blog.

---

### SetProcessCritical.cpp

Set the selected process as critical or not.

If the process is critical,when exit the process,the system will cause BSOD.

And it can also be used to turn a critical process into normal.

### CheckCriticalProess.cpp

Check the selected process is critical or not.

### FindCriticalProcess.cpp

Look through all the process and find the critical processes.

---

###  CreateRemoteThread.cpp

Use CreateRemoteThread to inject dll,usually used under WinXP.

### NtCreateThreadEx + LdrLoadDll.cpp

Use NtCreateThreadEx + LdrLoadDll to inject dll.

Note:

You need use release mode to build it.

### FreeDll.cpp

Use NtCreateThreadEx to free dll.

Use to inject Dll into a process at many times.

---

### EnumerateProcess&GetFile'sHandle&CloseHandle(XP).cpp

Enumerate all processes and get specified file's handle,then choose whether to close it or not.

Support absolute path and relative path.

Support WinXP and later.

Note:

- WinXP and Win7,ObjectTypeNumber = 0x1c
- Win8 and later,ObjectTypeNumber = 0x1e

### EnumerateProcess&GetFile'sHandle&CloseHandle(Win7).cpp

Enumerate all processes and get specified file's handle,then choose whether to close it or not.

Support absolute path and relative path.

Support Win7 and later.

Note:

- WinXP and Win7,ObjectTypeNumber = 0x1c
- Win8 and later,ObjectTypeNumber = 0x1e

---

### GetPIDandHandle(evt).cpp

Get Eventlog Service PID and search evt file's Handle.

Use NtQuerySystemInformation to query SystemExtendedHandleInformation.

Support WinXP and later.

Note:

- WinXP and Win7,ObjectTypeNumber = 0x1c
- Win8 and later,ObjectTypeNumber = 0x1e

### GetPIDandHandle(evtx).cpp

Get Eventlog Service PID and search evtx file's Handle.

Use NtQuerySystemInformation to query SystemHandleInformation.

Support Win7 and later.

Note:

- WinXP and Win7,ObjectTypeNumber = 0x1c
- Win8 and later,ObjectTypeNumber = 0x1e

---

### GetProcessAuthority.cpp

Look through all the process and detect whether the process runs as admin.

---

### MasqueradePEBtoCopyfile.cpp

Masquerade current process' PEB into exploer.exe and use IFileOperation to copy file.

You can use this to copy file into "C:\\windows\\System32" with normal user permissions.

### DisableFirewall.cpp

Use to disable Windows Firewall with normal user permissions.

Expand on IFileOperation of UAC bypass.

---

### CreateFileMapping.cpp

Create 2 file mapping object.

Use to share data between multiple processes.

### OpenFileMapping.cpp

Open the 2 file mapping object.

Use to share data between multiple processes.

### DeleteRecordbyTerminateProcess(ReplaceFile).cpp

Kill the eventlog service's process and replace the eventlog file,then restart the Eventlog Service.

---

### EnablePrivilegeandGetTokenInformation.cpp

Enable the SeDebugPrivilege of current process and then get the full privileges of current process.

It can also enable other privileges.

### EnableSeImpersonatePrivilege.cpp

Enable the SeImpersonatePrivilege of current process and then create an impersonation token.

Call the CreateProcessWithToken function, passing the current process token to get a process.

Using with RottenPotato,we will have full privilege on the system.

### EnableSeAssignPrimaryTokenPrivilege.cpp

Enable the SeAssignPrimaryTokenPrivilege of current process and then call the CreateProcessAsUser function, passing the current process token to get a process.

Using with RottenPotato,we will have full privilege on the system.

### EnableSeTcbPrivilege.cpp

Enable the SeBackupPrivilege of current process and then we can call LsaLogonUser with SeTcbPrivilege and add arbitrary groups to the resulting token returned by this call. 

We will add the group SID “S-1-5-18” to the token, this is the SID for the Local System account and if we are using a token that possesses it, we will have full privilege on the system. 

It will create a reg key at HKEY_LOCAL_MACHINE\SOFTWARE\testtcb.

We will have full privilege on the system.

### EnableSeBackupPrivilege.cpp

Enable the SeBackupPrivilege of current process and then read the password hashes of local Administrator accounts from the registry.

The file will be saved as `C:\\test\\SAM`,`C:\\test\\SECURITY` and `C:\\test\\SYSTEM`.

We will have read access on the system.

### EnableSeRestorePrivilege.cpp

Enable the SeRestorePrivilege of current process and then create a reg key at HKEY_LOCAL_MACHINE\SOFTWARE\testrestore.

We will have write access on the system.

### EnableSeCreateTokenPrivilege.cpp

Enable the SeCreateTokenPrivilege of current process and then create primary tokens via the ZwCreateToken API.

After that enable the local administrator group on the token and enable SeDebugPrivilege and SeTcbPrivilege.

We will have all access on the system.

### EnableSeLoadDriverPrivilege.cpp

Enable the SeLoadDriverPrivilege of current process and then load the driver into the kernel.

First you need to add two reg keys,the command is:

`reg add hkcu\System\CurrentControlSet\CAPCOM /v ImagePath /t REG_SZ /d "\??\C:\test\Capcom.sys"`

`reg add hkcu\System\CurrentControlSet\CAPCOM /v Type /t REG_DWORD /d 1`

Then run me to load the driver(C:\test\Capcom.sys) into the kernel.

We will have all access on the system.

### EnableSeTakeOwnershipPrivilege.cpp

Enable the SeTakeOwnershipPrivilege of current process and then have write access to a registry key "hklm\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options".
Then we can write it in "Medium" permission.

Eg.

`reg add "hklm\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options" /v takeownership /t REG_SZ /d "C:\\Windows\\System32\\calc.exe"`

We will have write access on the system' registry key.

### EnableSeDebugPrivilege.cpp

Enable the SeDebugPrivilege of current process and then we can inject a dll into the process. 

We will have full privilege on the system.

---

