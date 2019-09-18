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
