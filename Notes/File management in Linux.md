#practical  #linux #software 
https://www.redhat.com/sysadmin/linux-file-permissions-explained

###### View files
List files
`$ ls`

View permissions of files
`$ ls -l`

###### Read permissions
![[Pasted image 20230225154941.png|400]]
The user and the group is also mentioned in the output of the above command.

###### Modify permissions using characters
Give execution permission to al 
`$ chmod +x file`

Remove write permissions from all
`$ chmod -w file`

Give execution permission to owner only
`$ chmod u+x file`

Remove read permission from group and other
`$ chmod go-r file`

Give all permission for all
`$ chmod +rwx file`

Set other's permissions as read only
`$ chmod o=r file` 

Set user's permissions as all read, write and execute
`$ chmod u=rwx file`

###### Modify permissions using octal values
- r (read) = 4
- w (write) = 2
- x (execute) = 1

An octal value can be formed by adding those values. Examples,
- (rwx) = 4+2+1 = 7
- (r--)   = 4+0+0 = 4
- (-w-) = 0+2+0 = 2
- (--x)  = 0+0+1 = 1
- (rw-) = 4+2+0 = 6
- (-wx) = 0+2+1 = 3
- (r-x)  = 4+0+1 = 5
- (---) = 0+0+0 = 0

When three of those octal values get together, complete permission is formed. Examples,
`$ chmod 777 file` -rwxrwxrwx
`$ chmod 700 file` -rwx------
`$ chmod 156 file` ---xr-xrw-
###### Change ownership of a file
Change user
`$ chown user file`

Change group
`$chown :group file`

Change both user and group
`$ chown user:group file`

