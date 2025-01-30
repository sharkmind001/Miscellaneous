# Connect remote ssh with windows client.

Windows 10 and later versions come with an **OpenSSH client** pre-installed, allowing you to use SSH via **Command Prompt (cmd) or PowerShell**.

### **Step 1: Locate Your AWS Key Pair**

*   When you launched your AWS EC2 instance, you downloaded a `.pem` key file.
*   Make sure you have the **private key (`.pem`)** stored securely on your Windows machine.
*   Example: `C:\Users\YourUser\Downloads\aws_key.pem`

---

### **Step 2: Open Windows Terminal (PowerShell or CMD)**

1.  Press `Win + R`, type `cmd` (or `powershell`), and press **Enter**.
2.  Navigate to the directory where your `.pem` file is stored:

```
cd C:\Users\YourUser\Downloads
```


### **Step 3: Change Key File Permissions**

By default, AWS requires that your **private key** (`.pem` file) has restricted permissions.

Run the following command in **PowerShell**:

```
icacls "aws_key.pem" /inheritance:r
icacls "aws_key.pem" /grant:r "%USERNAME%:R"
icacls "aws_key.pem" /deny "Everyone:F"
```

This ensures only your user has read access.



### **Step 4: Connect to AWS via SSH**

Use the following command:

```
ssh -i "C:\\Users\\YourUser\\Downloads\\aws\_key.pem" ubuntu@<Your-EC2-Public-IP>
```

*   Replace `<Your-EC2-Public-IP>` with your **EC2 instance's public IP address** (found in AWS console).
*   Example:

```
ssh -i "aws\_key.pem" ubuntu@3.110.117.181
```

### **Step 5: Verify Connection**

Once connected, you should see a terminal prompt like:

```
ubuntu@ip-172-31-XX-XX:~$
```

You are now inside your AWS Linux machine!

### Step 6: Create aws.bat file to open by double click.

Create `aws.bat` file and write following code and place `ssh_key.pem` file in the same directory.
```
cd C:\custom_tools\
ssh -i "ssh_key.pem" ubuntu@3.110.117.180
```



