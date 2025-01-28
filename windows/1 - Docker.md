### How To Install Docker on Windows 11?
1. To start docker desktop, first you need to download the [docker](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?_gl=1*fkamid*_ga*OTA1Nzg5NTE1LjE2OTc0NDEzMTQ.*_ga_XJWPQMJYHQ*MTY5Nzc3MTQ0OS4zLjEuMTY5Nzc3MTQ1Mi41Ny4wLjA.) file on windows. 
2. Turn on Hyper-V and Containers Windows features.
3. Enable hardware virtualization in BIOS. For more information, see [Virtualization](https://docs.docker.com/desktop/troubleshoot/topics/#virtualization).
4. If Hyper-V missing in your system (Windows home version Hyper-V not installed) install instruction:
    ```
    pushd "%~dp0"
    dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
    for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
    del hyper-v.txt
    Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL
    pause
    ```
    Note: Create a .bat file then run it administration mode
5. 