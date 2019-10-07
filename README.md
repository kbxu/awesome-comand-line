Awesome Command Line
==============================

Remove PDF Watermark
---------------------------------------
1. Uncompress original pdf file to text file.
2. replace watermark strings to empty.
3. Compress the edited text file back to pdf file.

`pdftk original.pdf output uncompressed.pdf uncompress`

`sed -i "s/watermarktextstring//g" uncompressed.pdf`

`pdftk uncompressed.pdf output fixed.pdf compress`



Print Selected Columns of a CSV file
---------------------------------------

print the 1st,3rd,5th columns


`awk -F ',' '{print $1,$3,$5}' input.csv`

add a header before print

`awk -F ',' 'BEGIN {print "index,col1,col2"} {print $1,$3,$5}' input.csv`

use comma to seperate output, OFS for "output field seperator"

`awk -F ',' '{OFS=","}{print $1,$3,$5}' input.csv`

change print to printf

`awk -F ',' 'BEGIN {print "index,col1,col2"} {printf("%s,%s,%s\n",$1,$3,$5}' input.csv`

Generate a Random Password in Linux Terminal
---------------------------------------

`date +%s | sha256sum | base64 | head -c 32 ; echo`

While having public key added to authorized_keys but the terminal still asks for password
---------------------------------------

**check for the below ownerships for user ufo**

 - `/home/ufo` ownership is 700
 - `/home/ufo/.ssh` ownership is 700
 - `/home/ufo/.ssh/authorized_keys` ownership is 600

Conda Configuration
---------------------------------------
 - Put `~/Anaconda3/condabin` in system search path
 - Run `conda config --set auto_activate_base true` to activate base env when terminal starts (doesn't work for windows dos somehow)
 
 
Get Bandwidth of Network Interface
---------------------------------------
 - DOS `wmic NIC where NetEnabled=true get Name, Speed` [ref](https://superuser.com/a/412956)
 - POWERSHELL `Get-NetAdapter | where Status -eq "Up" | select InterfaceDescription, LinkSpeed` [ref](https://superuser.com/a/412956)
 - BASH `sudo ethtool <interface> | grep Speed` [ref](https://serverfault.com/a/207478) or `cat /sys/class/net/<interface>/speed` [ref](https://serverfault.com/a/770662)

Prepare a Start-up Script for Windows DOS Terminal (similar as ~/.bashrc in linux)
---------------------------------------
 - Edit the `"%"USERPROFILE"%\init.cmd"` script (script location could be anywhere) and put in commands such as `activate` for conda environment.
 
 - Run `reg add "HKCU\Software\Microsoft\Command Processor" /v AutoRun ^ /t REG_EXPAND_SZ /d "%"USERPROFILE"%\init.cmd" /f`
 
 - To remove the start-up operation, run `reg delete "HKCU\Software\Microsoft\Command Processor" /v AutoRun`
