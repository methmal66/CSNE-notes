---
tag: cloud gcp software linux 
---

# Create an instance
GCP provided a $300 free credits for 3 months of duration to use with new accounts. SO, set a new account and add your billing details. Then go to the cloud console 
<https://console.cloud.google.com> and create a new project.
![[Screenshot 2023-03-04 at 12.35.08 1.png]]

Then go to `Menu -> Compute Engine -> VM instances` 
![[Screenshot 2023-03-03 at 18.18.04.png|350]]

You will redirected to this page when creating VM for the first time. Enable the Compute Engine API.
![[Screenshot 2023-03-03 at 18.18.18.png|400]]

You will redirected to the VM instance page. Then create a instace from there
![[Screenshot 2023-03-03 at 18.20.50.png]]

Enter instace name, region and machine type
![[Screenshot 2023-03-03 at 18.21.09 1.png|500]]

> [!tip]
> Use `asia-south1(Mumbai)` as the region. It is the closest to Sri Lanka

Change the default boot disk. Set the disk size and select another OS from the market place
![[Screenshot 2023-03-03 at 18.28.13 1.png]]

Explore the marketplace, find your desired OS. Then hit launch
![[Screenshot 2023-03-03 at 18.27.04.png|300]]

Close the new instance creation tab. Go to the privous page where we were creating the VM. Notice that, your desired OS is under the Operating System. Select it and save the changes. Boot disk configs are updated now.
![[Screenshot 2023-03-03 at 18.31.49 1.png|400]]

Edit network interfaces from `Advanced Options -> Networking -> Network Interfaces -> Edit network interface`. Select a desired network and subnetwork. Save the changes.
![[Screenshot 2023-03-04 at 13.31.10.png|500]]

> [!NOTE]
> [[Creating a custom private network in GCP]] (vlan) is explained here

> [!NOTE]
> Only subnets that are hosted in the selected region are available to setup.

> [!tip]
> Custom IP can be assigned optionally. It will be useful for hosting a somthing like dhcp server

You will be redirected to the VM instace home page. Connect to the brower ssh of your instance
![[Screenshot 2023-03-04 at 13.47.48.png]]

You will be redirected to a new page with ssh in browser. It will take couple seconds to tranfer the SSH key, wait patiently. We can continue the setup from terminal from here.
![[Screenshot 2023-03-04 at 15.54.15.png]]
# Setup instance

Set root password
```
$ sudo su
$ cd
$ passwd
```

Create a new sudo user
```
$ useradd -m methmal
$ gpasswd -a sudo methmal
$ passwd methmal
$ su methmal
```

> [!note]
> The above step is not necessary. We created the sudo user to use in any future senarios

Update the system
```CentOS
$ yum update -y
```

# Get a snapshot
> [!warning]
> Make sure to get a snapshot immeditely after creating the VM. Then take another shots after major configuration to the instance. Otherwise, VMs would not be able to back up in case of a faliure.

Go to `Navigation Menu -> Compute Engine -> Snapshots`
![[Screenshot 2023-03-04 at 14.40.38.png|400]]

Enter name, description. Select the instace and the location where it getting stored. Then create the snapshot.
![[Screenshot 2023-03-04 at 14.48.49.png|500]]


All the created snapshots will be availble in the snapshot page.
![[Screenshot 2023-03-04 at 14.56.57.png]]

When it is requied to time travel to a past state of a instace, select the snapshot from the above. Then create a seperate instance from the snapshot. All the changes will be availble out of the box in the newly created instance.
![[Screenshot 2023-03-04 at 15.00.33.png]]

