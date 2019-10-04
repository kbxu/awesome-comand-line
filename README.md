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

