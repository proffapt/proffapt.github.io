[^1]: It is the path to the `.pem` file which you downloaded just before deploying the VM.
[^2]: Name of the user given while creating the virtual machine.
[^3]: Public IP address of the machine.
[^4]: Name of the client you specified in the script.

# Setup OpenVPN Server on Azure

- [Get Microsoft Azure](#step-1-get-microsoft-azure)
- [Create an EC2 instance](#step-2-create-an-ec2-instance)
- [SSH into the remote server](#step-3-ssh-into-the-remote-server)
	- [Windows](#sshing-via-a-windows-machine)
	- [Linux & MacOS](#sshing-via-a-linux-or-macos-machine) 
- [Setup OpenVPN Access Server](#step-4-setup-openvpn-access-server)
	- [Gaming Configuration](#configuration-for-gaming) 
- [Download ovpn files](#step-5-download-ovpn-files)
	- [Windows](#windows)
	- [Linux & MacOS](#linux--macos)
- [Connecting to the VPN on client devices](#step-6-connecting-to-the-vpn-on-client-devices)
- [Budget Control](#step-7-budget-control)
- [Authors](#authors)

***

### Step 1: Get Microsoft Azure

- Avail the [Github Student Developer Pack](https://docs.github.com/en/education/explore-the-benefits-of-teaching-and-learning-with-github-education/github-global-campus-for-students/apply-to-github-global-campus-as-a-student#applying-to-github-global-campus). 
- Now navigate to the benefits page and apply a filter for `cloud` or just [click here](https://education.github.com/pack/offers?sort=popularity&tag=Cloud). Follow the steps to sign up for Azure, and you will receive **$100 credits**.
> **Note** Although, we could have done it [directly using Institute ID on Microsoft Azure](https://signup.azure.com/studentverification?offerType=1&correlationId=bd79ce7e43aa48319516e398c31f47bd). But the afore-mentioned method exposes you to various other possibilities which you might have not even thought of. We chose Microsoft Azure here, if you want you can also choose DigitalOcean or any other cloud platform of your preference.

### Step 2: Create an EC2 instance

- Goto [Azure portal](https://portal.azure.com/#home) 
- Click on the `hamburger` menu > `Create a resource` > `Compute` > `Ubuntu Server 22.04 LTS`. Fill in the necessary details in the `Basics` section.<br>
  <img width="550" alt="image" src="https://user-images.githubusercontent.com/86282911/221249596-69fbc2bb-61fc-40c3-82a8-931a99a49885.png">
  <img width="375" alt="image" src="https://user-images.githubusercontent.com/86282911/221250228-8a9ace9d-bc1e-4587-9a5b-bc3529e331a9.png">
  <img width="930" alt="image" src="https://user-images.githubusercontent.com/86282911/221250519-a08d12a1-2adb-4817-bbe8-df8e4cc4c1ba.png">

  - Create a new `Resource Group` & give your virtual machine a name.<br>
    <img width="480" alt="image" src="https://user-images.githubusercontent.com/86282911/221341942-9ce58f0b-5cab-4d17-a6ff-ead7492fb958.png">
  
  - Now about __region__ & __disk size__.<br>
  __First select the cheapest size and then select the region from the available options__. A standard B1s size is going to be good enough and will last around 11 months using free credits. Now choose the closest region where the said size is available, which in our case will be `South-East Asia`. A bigger (aka more costly) size would probably be available in Indian regions.<br>
    <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221341981-ba4b771f-ac7f-48d1-9ddf-283c60ffbb4e.png"><br>
    <img width="900" alt="image" src="https://user-images.githubusercontent.com/86282911/221342020-1c5acc86-fa42-45f7-b525-e030bd344960.png"><br>
    <img width="900" alt="image" src="https://user-images.githubusercontent.com/86282911/221342094-a3e467a1-3eba-4028-bb78-5defd6a6cb0d.png"><br>
    <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221342129-ca8773e2-6e37-409c-b958-b71f59ee12d8.png">
  
  - Now choose an __Authentication method__ according to your preference.
    - Using `ssh keys` is _more secure but hard to follow_.
      <details>
      <summary>
	  Using SSH keys
      </summary>
	
      - Select `SSH public key` as the Authentication Method and fill in the required fields.<br>
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/222965735-37722163-583e-433b-8629-2a1ca65acebd.png">

      - Choose **HTTPS(443)** in `Select inbound ports`.<br>
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221342161-4e366833-a82c-4cf7-9246-7220ab2465b8.png">
  
      - Leave the rest of the settings as default in other sections and click `Review+Create`.
      - Now you will be prompted to `Generate a new key pair`, select `Download private key and create Resource`. This step will download a `.pem` file onto your local machine.<br>
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221342181-ac62d29d-9727-4b57-a6c8-57082f2ce1e0.png"><br>
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221342234-1336e5ec-5e9c-431e-9649-2bb1c5cb144f.png">

      </details>
    - Using `password` is _easy to follow but less secure_.
      <details>
      <summary>
	  Using password
      </summary>
	
      - Select `Password` as the Authentication Method and fill in the required fields.<br>
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/222967213-92d8fc30-153d-40dd-84b4-879a8c112a97.png">

      - Choose **HTTPS(443)** in `Select inbound ports`.<br>
        <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221342161-4e366833-a82c-4cf7-9246-7220ab2465b8.png">

      - Leave the rest of the settings as default in other sections and click `Review+Create`.
      </details>


- Now, wait for the VM to be deployed. Once the VM is deployed
  - Click `Goto Resource`.<br>
    <img width="420" alt="image" src="https://user-images.githubusercontent.com/86282911/221343236-d97058dd-587e-4703-911d-438eac1458ee.png">

  - Click `Configure` for the *DNS* option under `Networking`.<br>
    <img width="800" alt="image" src="https://user-images.githubusercontent.com/86282911/221343386-27e889fe-4962-4a2f-8ced-2b3f49b3bca7.png">

  - Type in any DNS name like your username in the `DNS name label` field and press `Save`.<br>
    <img width="420" alt="image" src="https://user-images.githubusercontent.com/86282911/221343478-3821765f-f1d0-4c13-b56f-d0ee9324cd80.png">
	
### Step 3: SSH into the Remote Server

> **Warning**

For this step you will need to __switch__ to a _network other than that of campus_ as __PORT 22(default port for SSH) IS BLOCKED ON CAMPUS NETWORK__.

SSH steps are drastically different for a Windows client & a Linux/MacOS (`*nix`) client.<br>
Click on the following links to read about the steps for the client of your interest: 
- [Windows](#sshing-via-a-windows-machine)
- [Linux & MacOS](#sshing-via-a-linux-or-macos-machine)
	
#### SSHing via a Windows machine

- To make sure your PC has `SSH` client and server both installed, run the following command on [Command Prompt](https://www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line/) as __Administrator__.
  ```ps
  Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
  Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
  ```
  - Windows also has [Powershell](https://en.wikipedia.org/wiki/PowerShell) and the new [Windows Terminal](https://en.wikipedia.org/wiki/Windows_Terminal) which combines all the different [shell environments](https://en.wikipedia.org/wiki/Shell_(computing)). So, you can choose one from these as well, but it doesn't matter in this context.
- Now `ssh` into the remote server
  <details>
  <summary>
	Using SSH keys
  </summary>
	
  ```ps
  ssh -i C:\path\to\privatekey user@host_address
  ```
  > C:\path\to\privatekey[^1] • user[^2] • host_address[^3]
  </details>
  
  <details>
  <summary>
	Using Password
  </summary>
	
  ```ps
  ssh user@host_address
  ```
  > user[^2] • host_address[^3]
  </details>

#### SSHing via a Linux or MacOS machine

- You can ssh via the following methods
  <details>
  <summary>
	Using SSH keys
  </summary>
	
  ```sh
  ssh -i path/to/privatekey user@host_address
  ```
  > path/to/privatekey[^1] • user[^2] • host_address[^3]

  > **Note**

  The afore-mentioned method has a long command to type in, the recommended method will not be an alias but utilize something which SSH itself provides us.<br>
We can add the config details to the ssh config file (`~/.ssh/config`).	The format is given below, replace the content inside `<_>` with your values and save it into the config file.<br>
**Then you can ssh directly by using `ssh MyAzure`**.

  ```graphql
   Host <MyAzure>
 	  HostName <Host Address>
 	  User <Username>
 	  IdentityFile </path/to/privatekey>
 	  IdentitiesOnly yes
  ```

  > **Note** make sure you have set the correct permissions on the private key or else you will get an error during ssh. You can fix this by changing the permissions using the following command:

  ```sh
  chmod 400 path/to/privatekey
  ```
  > path/to/privatekey[^1]
	
  </details>
	
  <details>
  <summary>
	Using Password
  </summary>
	
  ```sh
  ssh user@host_address
  ```
  > user[^2] • host_address[^3]
  </details>

### Step 4: Setup OpenVPN Access Server

After we have ssh'ed into the machine, we have to set up the OpenVPN Access Server. 

- Before that, it's a good practice to update and upgrade your system via
  ```sh
  sudo apt update
  sudo apt upgrade
  ```
- Execute the following command
  ```sh
  wget https://git.io/vpn -O openvpn-install.sh && sudo bash openvpn-install.sh
  ```
  It will download and execute a script that automates openvpn server configuration.
- Keep in mind to update the following options during the setup process & leave the rest in their default state:
  - `IP address`: Your _Public IP_ for the azure machine.
  - `UDP or TCP`: Enter 2 for __TCP__ as __UDP ports are blocked on campus network__.
  - `PORT`: __443__
  - `DNS RESOLVER`: Enter 4 for __OpenDNS__.
  - `CLIENT`: One configuration for one client/device. Name it like pc, mobile, etc.
- The `.ovpn` file will be stored inside `/root` directory, copy it into your user's home directory using the following command
  ```sh
  sudo cp /root/client_name.ovpn ~/
  ```
  > client_name[^4]

> **Note** Run the same script to generate new clients (you will need a unique client for each device that’s going to be connected to the VPN), i.e., __one `.ovpn` file one connection__.

#### Configuration for Gaming

Use the `TCP_NODELAY` option if you are planning to use this VPN for gaming. Execute the following command on the remote VPN server
```sh
sudo echo "tcp-nodelay" | sudo tee -a /etc/openvpn/server.conf
```
Now restart the openvpn service using 
```sh
sudo systemctl restart openvpn.service && sudo systemctl restart openvpn@server.service
```

### Step 5: Download ovpn files

Now we have to transfer the `.ovpn` files generated on the remote server to our local machine. The steps to achieve this are different for `*nix` (Linux or MacOS) & Windows, refer to the following links to read about the steps for your platform of interest:
- [Windows](#windows)
- [Linux & MacOS](#linux--macos)

#### Windows
- [Download WinSCP](https://winscp.net/eng/download.php) a GUI implementation for `scp (secure copy)` on windows. Open it.
- Click on `New Session`<br>
  <img width="480" alt="image" src="https://user-images.githubusercontent.com/86282911/221348819-75807203-7b93-4eca-9095-0d6a76cd0fc8.png">

- Now refer to the procedure mentioned below based on your authentication method.
  <details>
  <summary>
	Using SSH keys
  </summary>

  - [Download PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) for converting the `.pem` file to `.ppk` via __PuTTYgen__. Open it.
    - From the `Start menu`, choose `All Programs` > `PuTTY` > `PuTTYgen`.
    - Choose `Load`.<br>
      <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221342564-7a3936fe-2d3e-4318-9529-5a4d9fdb95b4.png">

    - By default, PuTTYgen displays only files with the extension `.ppk`. To locate your `.pem` file, choose the option to display files of all types.<br>
      <img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/221342654-fca0027b-1f83-4e7d-811c-78719137ce9f.png">
  
    - Select your `.pem` file for the key pair that you specified when you launched your instance and choose `Open`. PuTTYgen displays a notice that the .pem file was successfully imported. Choose `OK`.<br>  
      <img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/221342668-94223a8d-7e06-4927-873c-209aa4e1b794.png">
	
    - To save the key in the format that PuTTY can use, choose `Save private key`.<br>
      <img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/221342698-93f3ef59-1175-48cc-bea4-67e163d2b36a.png">
	
    - PuTTYgen displays a warning about saving the key without a passphrase. Choose `Yes`.<br>
      <img width="300" alt="image" src="https://user-images.githubusercontent.com/86282911/221342709-00472e3f-d94c-4681-8edb-af9b10ff7955.png">
	
  - Now head back to the `WinSCP` window & enter the following login configuration
    - `File Protocol`: _SCP_.
    - `Host Name`: Your remote machine's Public IP address.
    - `Port`: 22 (Default).
    - `Username`: username which you set for the remote machine.<br>
      <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221343071-51004b21-467d-4ad7-a422-06bb3112e61a.png">
	
  - Navigate to `Advanced` > `Authentication`
  - Browse and select your `.ppk` file.<br>
    <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/221343115-b1f63903-5bb0-4416-a53d-9b706d4fd872.png">
	
  - Press `OK` then `Login` & finally `YES`.
  </details>
  <details>
  <summary>
   	Using Password
  </summary>

  - Enter the following login configuration
    - `File Protocol`: _SCP_.
    - `Host Name`: Your remote machine's Public IP address.
    - `Port`: 22 (Default).
    - `Username`: _Username_ which you set for the remote machine.
    - `Password`: _Password_ which you set for the remote machine<br>
      <img width="450" alt="image" src="https://user-images.githubusercontent.com/86282911/222964236-a165f125-4e32-4754-8752-9a01f948235e.png">
	  
  - Press `Login` then `YES`.
  </details>
  
- Select and download all the `.ovpn` files you created which will be shown on the interface.<br>
  <img width="180" alt="image" src="https://user-images.githubusercontent.com/86282911/221343162-03ed5396-6637-4ecb-9b21-433a3799bb1b.png">

- Now shut down the `WinSCP session`

#### Linux & MacOS

<details>
<summary>
	Using SSH keys
</summary>
	
Run the following command, the key will be downloaded in the `Downloads` directory.
```sh
scp -i path/to/privatekey user@host_address:client_name.ovpn ~/Downloads/
```
> path/to/privatekey[^1] • user[^2] • host_address[^3] • client_name[^4]
>> You can skip the -i (identity file) parameter if you have [added the ssh config earlier](#sshing-via-a-linux-or-macos-machine).
</details>

<details>
<summary>
	Using Password
</summary>
	
Run the following command, the key will be downloaded in the `Downloads` directory after you enter the correct password set by you earlier.
```sh
scp user@host_address:client_name.ovpn ~/Downloads/
```
> user[^2] • host_address[^3] • client_name[^4]
</details>

To _start/stop/check_ status of the OpenVPN server use `systemctl`:
```sh
sudo systemctl start/stop/status openvpn@server.service
```

> **Android**: Follow either of the aforementioned methods and then transfer the downloaded `.ovpn` file to your Android device via Telegram/Bluetooth/Mail or whatever to your android device.

### Step 6: Connecting to the VPN on client devices

* **Android**: Download [Open VPN Connect](https://play.google.com/store/apps/details?id=net.openvpn.openvpn&hl=en_IN&gl=US) app from Play Store. Open the app and after going through the first screen, go to **Files** tab, there import the `.ovpn` file, and connect.
    
* **Linux**: In most of the distros, you can go to the network manager and import the `.ovpn` file. If not then install OpenVPN with `sudo apt install openvpn` and connect using `sudo openvpn --config /path/to/config.ovpn`.

* **MacOS**: You can either download the _GUI tool_ [tunnelblick](https://tunnelblick.net/downloads.html) for importing the `.ovpn` file or download the _CLI tool_ for openvpn via [MacPorts](https://www.macports.org/install.php) or [HomeBrew](https://brew.sh/) using `sudo ports install openvpn` and `brew install openvpn` respectively; then execute `sudo openvpn --config /path/to/config.ovpn`.
    
* **Windows**: Download the official [OpenVPN Connect client for Windows](https://openvpn.net/client-connect-vpn-for-windows/), import the `.ovpn` file, and toggle it ON to finally connect - [video guide](https://www.youtube.com/watch?v=P2SroQ_pzPU).

### Step 7: Budget Control

> **Warning** This is a very important step, to ensure the long-term usability of your credits

- Use only one instance.
- Bandwidth is _**free up to $100 credits**_, so it's better not to waste resources on the VPN.

> **Note** If in any case, you have to stop an instance forcibly, do it; to be on the safer side.

***

### Authors

- Arpit Bhardwaj ([@proffapt](https://github.com/proffapt))

<p align="center"> Created with lots of <b>&lt;/&gt;</b> and ♥ </p>
