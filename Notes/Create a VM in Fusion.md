 #vmware #practical  #software #linux #CSA #os 

###### Complete new VM wizard
Go to VMware and new virtual machine. Then select "install from disc or image"
![[Screenshot 2023-02-23 at 19.00.06.png]]
Select the iso file you want to install. Then continue
![[Screenshot 2023-02-23 at 19.05.19.png]]
Edit the VM location
![[Screenshot 2023-02-23 at 19.09.44.png]]
Give proper name and a location. Then save.
![[Screenshot 2023-02-23 at 19.11.22.png]]
###### Customize settings
Go to the settings of the VM you just created. Then navigate to the "Processors and Memory" section.
![[Screenshot 2023-02-23 at 19.16.06.png]]
Customize the settings as prefer. Be sure to keeps the resources above the recommended level. Then go the 
![[Screenshot 2023-02-23 at 19.18.15.png]]
Then go to the "Startup disk" section of the settings. And select CD/DVD as the startup disk.
![[Screenshot 2023-02-23 at 19.20.32.png]]
Then go the "Network Adapter" section from the settings. Make sure that you have configured the adapter to work as "Internet sharing".
![[Screenshot 2023-02-23 at 19.23.16.png]]
###### Install the iso to the VM
Start the VM. Continue to live installation.
![[Screenshot 2023-02-23 at 19.26.01.png]]
Select "Install to Hard Drive"
![[Screenshot 2023-02-23 at 19.30.21.png|400]]

Select your prefered language. Then continue.
![[Screenshot 2023-02-23 at 19.32.04.png]]

Select your date time. And done.
![[Screenshot 2023-02-23 at 19.34.39.png]]

Then select the installation destination. And done.
![[Screenshot 2023-02-23 at 19.35.22.png]]

If everything seems to be fine, go with the "Begin Installation"
![[Screenshot 2023-02-23 at 19.36.42.png]]

Patiently wait for the installation process to complete. Finish installation then.
![[Screenshot 2023-02-23 at 19.57.31.png]]

Restart the VM to boot from the hard drive
![[Screenshot 2023-02-23 at 20.01.57.png|250]]

######  Setup VM
Go through any welcome page
![[Screenshot 2023-02-23 at 20.07.27.png]]

Give username and password
![[Screenshot 2023-02-23 at 20.08.14.png]]

To change hostname, edit `/etc/hostname` and add your `hostname`. Then edit `/etc/hosts` and append line `127.0.0.1 hostname`

Go to terminal and update your system
```bash
$ sudo dnf update
```

Install ohmyzsh
```Shell
$ sudo yum install zsh -y
$ chsh -s $(which zsh)
$ sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
Edit `~/.zshrc` and set ZSH_THEME="agnoster". Then edit `~/.bashrc` and add `zsh` at the end of the file.

###### Get a backup
This is a very important step, this save lof of your time. Get a backup so you can skip the all above steps when creating your next VM. Go to the folder where your VMs are saved. Then make a copy of the newly created VM and rename it as a backup. Whenever you want to create a simillar VM, just copy paste the backup VM to you desired location, then open the VM from there.
![[Screenshot 2023-02-24 at 01.15.54.png]]
Suppose your VM got crashed some how, then you have to setup it again from all the way up. You can stave snapshot of your VM at a any given time. Then VM can be launched from that state. It come really handy as you can play with the VM without being afraid of crashing it. Right click on the VM from the VM library, then snapshots. Get a new snapshot by clicking the camera icon.
![[Screenshot 2023-02-24 at 20.52.19.png]]
GIve a name to your snapshot and save it.
![[Screenshot 2023-02-24 at 20.52.45.png|300]]

Now you can restore to any of those state from the righ click menu of each snapshot