### **1\. Verify the Server Configuration**

Ensure the server is set up correctly to keep the connection alive:

1.  **Check the Server's SSH Daemon Config:**
    *   On the server (AWS instance), edit the SSH configuration file:
```
sudo nano /etc/ssh/sshd_config
```
*   Look for these parameters, and set them as follows if not already configured:
```
ClientAliveInterval 120
ClientAliveCountMax 0
```
*   ClientAliveInterval: Time in seconds to wait before sending a keep-alive packet.
*   ClientAliveCountMax: Number of times the server waits for a response before disconnecting (0 means never).

1.  **Restart SSHD on the Server:**
```
sudo systemctl restart sshd
```
### **2\. Update the Client Configuration**

Update the client configuration to send keep-alive messages more frequently than the server's timeout setting:

1.  **Increase `ServerAliveInterval`:**
    *   Go to `C:\Users\SuperUser\.ssh` and open `config` file.
    *   Set a smaller interval, e.g., 30 seconds:  

```
  Host 3.110.117.180
  HostName 3.110.117.180
  IdentityFile C:\custom_tools\ssh_key.pem
  User ubuntu
  ServerAliveInterval 30
  ServerAliveCountMax 0
```
This ensures the client sends keep-alive packets every 30 seconds.

**Option 2 :**
      - Here we will set 3000000 seconds for long alive time.
```
  Host 3.110.117.180
  HostName 3.110.117.180
  IdentityFile C:\custom_tools\ssh_key.pem
  User ubuntu
  ServerAliveInterval 3000000
  ServerAliveCountMax 0
```
This will keep-alve for 833.33 hours.
**2.  Test the Connection Again:**
```
ssh 3.110.117.180
```
