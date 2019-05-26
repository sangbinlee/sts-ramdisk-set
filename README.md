# sts-ramdisk-set
sts-ramdisk-set



# bat
sc config imdisk start= auto
net start imdisk


imdisk -a -t vm -s 4G -m d:
format d: /q /Y
label d: JDK-RAMDISK
call xcopy C:\tools\Java\jdk1.8.0_211 D:\jdk1.8.0_211\ /S /E /Y /Q
call xcopy C:\tools\sts-4.2.1.RELEASE D:\sts-4.2.1.RELEASE\ /S /E /Y /Q
call xcopy C:\tools\apache-tomcat-9.0.20 D:\apache-tomcat-9.0.20\ /S /E /Y /Q


 

imdisk -a -t vm -s 400m -m n:
format n: /q /Y
label n: CHROME-CACHE


REM C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp
REM shell:common startup
REM  --disk-cache-dir="N:\TEMP\chrome_cache"


# make bat .lnk

# open folder by   shell:common startup  

# drag and drop bat .lnk file to  [C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp] 
