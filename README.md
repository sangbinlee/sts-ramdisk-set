# sts-ramdisk-set
sts-ramdisk-set



# bat
@echo off
sc config imdisk start= auto
net start imdisk


imdisk -a -t vm -s 4G -m d:
format d: /q /Y
label d: JDK-RAMDISK
call xcopy C:\tools\Java\jdk1.8.0_211 D:\jdk1.8.0_211\ /S /E /Y /Q
call xcopy C:\tools\sts-4.2.1.RELEASE D:\sts-4.2.1.RELEASE\ /S /E /Y /Q
call xcopy C:\tools\apache-tomcat-9.0.20 D:\apache-tomcat-9.0.20\ /S /E /Y /Q
call xcopy C:\tools\apache-tomcat-7.0.94 D:\apache-tomcat-7.0.94\ /S /E /Y /Q


 

imdisk -a -t vm -s 400m -m n:
format n: /q /Y
label n: CHROME-CACHE
 

start /D "D:\sts-4.2.1.RELEASE\" SpringToolSuite4.exe

REM C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp
REM shell:common startup
REM  --disk-cache-dir="N:\TEMP\chrome_cache"

rem shell:common startup  
rem copy ramdisk-bat - 바로 가기 to [C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp]

 


















# make bat .lnk

# open folder by   shell:common startup  

# drag and drop bat .lnk file to  [C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp] 



#  chrome link edit
"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" --disk-cache-dir="N:\TEMP\chrome_cache"











# SpringToolSuite4.ini


-vm
D:/jdk1.8.0_211/bin
-startup
plugins/org.eclipse.equinox.launcher_1.5.300.v20190213-1655.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.win32.win32.x86_64_1.1.1000.v20190125-2016
-product
org.springframework.boot.ide.branding.sts4
--launcher.defaultAction
openFile
-vmargs
-Dosgi.requiredJavaVersion=1.8
-Xms2048m
-Xmx2048m
-XX:+UseG1GC
-XX:+UseStringDeduplication
--add-modules=ALL-SYSTEM
-javaagent:D:\sts-4.2.1.RELEASE\lombok.jar













