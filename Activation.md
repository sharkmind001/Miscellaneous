Office Activation


===================================================

Step 1.Open command prompt in administrator mode.

Step 2: Open location of the Office installed on your PC.

cd /d %ProgramFiles%\Microsoft Office\Office16
cd /d %ProgramFiles(x86)%\Microsoft Office\Office16

Step 3: Convert your retail license to volume one.(If your Office is got from Microsoft, this step is required. On the contrary, if you install Office from a Volume ISO file, this is optional so just skip it if you want.)

for /f %x in ('dir /b ..\root\Licenses16\ProPlus2019VL*.xrm-ms') do cscript ospp.vbs /inslic:"..\root\Licenses16\%x"

Step 4: Activate your Office using KMS client key.
Make sure your PC is connected to the internet, then run the following command.

cscript ospp.vbs /setprt:1688
cscript ospp.vbs /unpkey:6MWKP >nul
cscript ospp.vbs /inpkey:NMMKJ-6RK4F-KMJVX-8D9MJ-6MWKP
cscript ospp.vbs /sethst:e8.us.to
cscript ospp.vbs /act

Step 5: Disable Office update

Go to any product word, exel, powerpoint 

Click on File tab> Account> Update> select Disable update from dropdown
