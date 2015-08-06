chksum
======

A small script to check md5/sha* checksum when downloading something, where they offer a checksum to verify against.

 

### Install

Put the script in `/usr/local/xbin`, or any folder of your choice. Just make sure it's in `$PATH`.

Give it execute permissions (`chmod +x`).



### Usage

	chksum md5 [-s] checksum file
	chksum sha[1|224|256|384|512] [-s] checksum file
	chksum [-h|-hl]

-	`-s, --status`.	Will only return true/false (1,0).



### Example

Success:

	[me@myhost] ~$ chksum sha da39a3ee5e6b4b0d3255bfef95601890afd80709 test.txt
	test.txt:		... OK
	[me@myhost] ~$

Error:

	[me@myhost] ~$ chksum sha da39a3ee5e6b4b0d3255bfef95601890afd80708 test.txt
	test.txt:		... FAILED

	chksum: WARNING: The checksum (da39a3ee5e6b4b0d3255bfef95601890afd80708) did NOT match

	[me@myhost] ~$



### Req.

The script is made to use/work with:

- [x] OS X: `md5` and `shasum`
- [x] Linux/*BSD: `md5sum` and `sha{1,224,256,384,256,512}sum`
