
#### **Step 1**. Create SSH keys on your local machine.

- Create a .ssh directory in your home directory 
	(note: ~ = your home directory)
	![[Pasted image 20240927182303.png](.\assets\1.png)]
	 run "**cd ~**" in PowerShell to double check your home directory
	![[Pasted image 20240927182904.png](.\assets\2.png)]
	-t = type (this is the type of encryption used for the key)
	-f = filename (specify filename and location)
	-C = comment (attaches a comment to a key)

	The command above will create two plain text files in the .ssh directory.

	"do-key" This is your private key
	"do-key.pub" This is your public key. The public key is the one that you copy to your server.
	![[Pasted image 20240927183019.png](.\assets\3.png)]
	![[Pasted image 20240927184057.png](.\assets\4.png)]
	 Windows PowerShell users: In PowerShell tilde expansion doesn't always work, so you may have to enter the full path. Replace "your-user-name" with your Windows user name.
	 
	![[Pasted image 20240927183954.png](.\assets\5.png)]
	



#### **Step 2**. Add a custom Arch Linux image using the web console

- Download required Arch Linux image online, for this course we need the **clouding version** that ending with **.qcow2** extension. ![[Pasted image 20240927185539.png](.\assets\6.png)]
- Login to your **digital-ocean account** and create a **new project**. ![[Pasted image 20240927192832.png](.\assets\7.png)]
-  Click the green **Create** then click **Droplets** to create a new cloud servers. ![[Pasted image 20240927185944.png](.\assets\8.png)]
- Select **San Francisco** for region given it is the closest city towards Vancouver for better performance and lower latency. ![[Pasted image 20240927190604.png](.\assets\9.png)]
- Select **SFO3** for the same reason above. ![[Pasted image 20240927190857.png](.\assets\10.png)]
- Click **Custom images** under **Choose an image**, then click the blue **+ Add image** ![[Pasted image 20240927191350.png](.\assets\11.png)]
- Click the blue button Upload Image ![[Pasted image 20240927191807.png](.\assets\12.png)]
- Open the required image ![[Pasted image 20240927192012.png](.\assets\13.png)]
- Choose **Arch Linux** for **DISTRIBUTION** and the **same region** as above. Then click the blue button **Upload Image**.![[Pasted image 20240927192340.png](.\assets\14.png)]![[Pasted image 20240927192447.png](.\assets\15.png)]
- Wait for 1-2 min until the Uploading finished![[Pasted image 20240927192624.png](.\assets\16.png)]
- Select **Basic** under Choose Size for educational purpose. ![[Pasted image 20240927193132.png](.\assets\17.png)]
- Select either the **$7** option under Premium AMD or **$8** option under Premium Intel.  ![[Pasted image 20240927193253.png](.\assets\18.png)]![[Pasted image 20240927193303.png](.\assets\19.png)]
- Select **SSH Key** under **Choose Authentication Method**, since SSH Key provide stronger authentication, are immune to brute-force attacks, and eliminate the risk of password theft or reuse. ![[Pasted image 20240927194126.png](.\assets\20.png)]
- Click the New SSH Key button to add the new SSH Key.
- ![[Pasted image 20240927201551.png](.\assets\21.png)]
- Use the following code in Powershell to copy your SSH KEY:
```
Get-Content C:\Users\your-user-name\.ssh\do-key.pub | Set-Clipboard
```
![[Pasted image 20240927202030.png](.\assets\22.png)]

- Paste the SSH key in the **SSH key content** box and Create a Name, then click on **Add SSH Key**. You should see your new SSH Key in this case the ACIT-2420, select this SSH Key. 
![[Pasted image 20240927202417.png](.\assets\23.png)]
![[Pasted image 20240927202841.png](.\assets\24.png)]


- Change **Host Name** to something shorter, like BCIT. It will appear in your prompt when you are connected to your server. ![[Pasted image 20240927194747.png](.\assets\20240927194747.png)]
- Leave the rest setting in **default** and click the blue button **Create Droplet** at the right corner. After a few second you will see your new Droplet's **host name** and it's **IP address**.
- ![[Pasted image 20240927195141.png](.\assets\25.png)] ![[Pasted image 20240927195306.png](.\assets\26.png)]
- [!Warning] Be careful when you select a CPU and Size Some configurations offer pretty powerful setups, these are expensive. We only need a basic configuration.
- After you have created this key pair you need to add your public key to your DigitalOcean account.

#### **Step 3**. Connect to your server using your SSH keys.
- After you have created a droplet you can connect to it via SSH by running it through your terminal. When you see [arch@yourhostname ~]$ means login successfully.
```
ssh -i .ssh/do-key arch@your-droplets-ip-address
```

- **note**: `-i` = identity_file, the path to the private key file
		arch = your username. The image that we used contains a regular user named "arch"

![[Pasted image 20240927212647.png](.\assets\27.png)]

- To **exit** your SSH connect just type `exit` and press enter.!![[Pasted image 20240927212718.png](.\assets\28.png)]