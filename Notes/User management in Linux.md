#linux #software #practical #CSA 

###### Find the currently logged in user?
Find the username only
`$ whoami`
###### Get details about a user?
`$ finger user` 

Get user id and group that the user is in
`$ id user`

###### Run a command in the previlaged mode?
`$ sudo command` - sudo means Super User DO

###### Login/logout user?
Switch User
`$ su username` 

Switch User with the user's shell environment
`$ su - username` 

- Must enter the password when login command.
- `root` is the default username
- Root can access any account without password
- `exit` will logout from the currently logged in user and return to the root.

###### Change/set passwod of a user
Change pw without knowing the current pw
`$ passwd user`

User changing their own pw when it is forgotten
`$ passwd`

- All the passwords are in the `/etc/shadow` file in encrypted format.
- `/etc/passwd` file saves all the basic user info, not the passwords

Make password expire after the first login.
`$ passwd -e user`
A password must be set before using this command. This will force user to change their password after the first loggin. 
![[Screenshot 2023-02-25 at 08.45.24.png]]
###### Add/delete user
Add user
`$ useradd user`

Create a user with a home dir
`$ useradd -m user`

Create the home dir in a different location
`$ useradd -m -d /path/to/dir user`

Delete a user
`$ userdel user`

Delete the home directory of a user
`$ userdel -r user`

If there are processes started by user, it might prevent from deleting the user. Therefor, kill all the processes own by that user.
`$ killall -u user`

###### Modify user
Change/set description
`$ usermod  -c "Full name or any other description" user`

###### Rename user
`$ usermod -l new-user user`
This does not change the home dir name or file permissions.

Change the home dir location
`$ usermod -md /home/new-user user`

###### Lock/unlock user?
Lock user
`$ passwd -l user`
Though user enter the correct password, it will be an authentification error, user cannot login. It is doen by adding `!!` in front of the encrypted password.

Unlock user
`$ passwd -u user`
User can login as previous. It is done by removing the `!!` previously added.

![[Screenshot 2023-02-25 at 08.23.36.png]]
![[Screenshot 2023-02-25 at 08.26.52.png]]


###### What is a group?
Group is a collection of users. Managing groups is the simplest way to handle multiple users simultaneously, especially when dealing with file permissions. Each group has an unique `gid`

###### Which file save the group detals?
`/etc/groups`

###### Add/Delete a group
`$ groupadd group` - Create group
`$ groupdel group` - Delete group

###### Rename a group
`$ groupmod -n new-group group`

###### Add/remove user to a group
`$ gpasswd group -a user` or `$ usermod user -aG group`

Remove user from a group
`$ gpasswd group -d user`

###### Add users to sudoers
1. Create a sudo group if it is not already there
	`$ groupadd sudo`
2. Add users to the sudo group
	`$ gpasswd -a user sudo`
3. Edit `/etc/sudoers`
	Add `%sudo  ALL=(ALL)  ALL` 
	`%` is necessary to indicate that sudo is a group, not a user
	
###### Set user's primary group
`$ usermod -g group user`
`-g` for primary group
`-G` for secondary groups









