Awesome Command Line
==============================

Remove PDF Watermark
---------------------------------------
1. Uncompress original pdf file to text file.
 
   `pdftk original.pdf output uncompressed.pdf uncompress`
  
2. replace watermark strings to empty.
 
   `sed -i "s/watermarktextstring//g" uncompressed.pdf`
  
3. Compress the edited text file back to pdf file.
 
   `pdftk uncompressed.pdf output fixed.pdf compress`

Print Selected Columns of a CSV file
---------------------------------------
 - Print the 1st,3rd,5th columns
 
   `awk -F ',' '{print $1,$3,$5}' input.csv`

 - Add a header before print

   `awk -F ',' 'BEGIN {print "index,col1,col2"} {print $1,$3,$5}' input.csv`

 - Use comma to seperate output, OFS for "output field seperator"

   `awk -F ',' '{OFS=","}{print $1,$3,$5}' input.csv`

 - Change print to printf

   `awk -F ',' 'BEGIN {print "index,col1,col2"} {printf("%s,%s,%s\n",$1,$3,$5}' input.csv`

Generate a Random Password in Linux Terminal
---------------------------------------
 - `date +%s | sha256sum | base64 | head -c 32 ; echo`

SSH Asks for `password` When `authorized_keys` is Corrected Configured (with public keys)
---------------------------------------
 - Make sure the ownerships of user **ufo** are:
 - 700 for `/home/ufo`
 - 700 for `/home/ufo/.ssh`
 - 600 for `/home/ufo/.ssh/authorized_keys`

Conda Configuration
---------------------------------------
 - Put `~/Anaconda3/condabin` in system search path
 - Run `conda config --set auto_activate_base true` to activate base env when terminal starts (doesn't work for windows dos somehow)
 
 
Get Bandwidth of Network Interface
---------------------------------------
 - DOS `wmic NIC where NetEnabled=true get Name, Speed` [ref](https://superuser.com/a/412956)
 - POWERSHELL `Get-NetAdapter | where Status -eq "Up" | select InterfaceDescription, LinkSpeed` [ref](https://superuser.com/a/412956)
 - BASH `sudo ethtool <interface> | grep Speed` [ref](https://serverfault.com/a/207478) or `cat /sys/class/net/<interface>/speed` [ref](https://serverfault.com/a/770662)

Prepare a Start-up Script for Windows DOS Terminal (similar as ~/.bashrc in linux) [ref](https://stackoverflow.com/a/17405182/3431997)
---------------------------------------
 - Edit the `"%"USERPROFILE"%\init.cmd"` script (script location could be anywhere) and put in commands such as `activate` for conda environment.
 
 - Run `reg add "HKCU\Software\Microsoft\Command Processor" /v AutoRun ^ /t REG_EXPAND_SZ /d "%"USERPROFILE"%\init.cmd" /f`
 
 - To remove the start-up operation, run `reg delete "HKCU\Software\Microsoft\Command Processor" /v AutoRun`
 
 Mount Remote Drive
---------------------------------------
 - mount `sudo sshfs -o allow_other username@serveIP:remote_folder local_mount_point`
 - unmount `sudo fusermount -u local_mount_point`
