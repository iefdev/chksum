# chksum

![][licenseBadge]


A script to check/verify checksums. Some sites offer a checksum file, while others offer the checksum to copy (as text) to manually compare against.

Or to create checksum files, like: `fooBar.txt.sha256` or: `CHECKSUMS.rmd160` (batch).

 

## Install

Put the script in `/usr/local/bin`, or any folder of your choice. Just make sure it's in `$PATH`.

Give it execute permissions (`chmod +x`).

Or you can use `install`...

    $ sudo install -v -m755 -o0 -g0 chksum /usr/local/bin


## Usage

    Verifying:
        chksum <mode <checksum> <file>

    Creating checksum files:
        chksum -a <files>
        chksum -o <mode> <files>
        chksum -b <mode> <files>

    Modes:
        md5|sha[1|224|256|384|512]|r[ipe]md160|whirlpool
	    [!] When creating checksum files... MD5 or SHA[1] are not accepted.


## Examples

Success:

    $ chksum sha da39a3ee5e6b4b0d3255bfef95601890afd80709 test.txt
	test.txt:		... OK

Error:

	$ chksum sha da39a3ee5e6b4b0d3255bfef95601890afd80708 test.txt
	test.txt:		... FAILED

	chksum: WARNING: The checksum (da39a3ee5e6b4b0d3255bfef95601890afd80708) did NOT match

Creating files:

    $ chksum -o rmd160 test.txt         // test.txt.rmd160
    $ chksum -a test.txt                // test.txt.rmd.160 + test.txt.sha256
    $ chksum -b sha256 test_0{1..5}.txt // CHECKSUMS.sha256 with all in 1 file

_The text format of the output file is:_

    da39a3ee5e6b4b0d3255bfef95601890afd80709 */path/to/test.txt


## License and Info

![][licenseBadge]

[gitlab.com/iEFdev/chksum][gl]


<!-- Markdown: link & image dfn's -->
[gl]: https://gitlab.com/iEFdev/chksum
[licenseBadge]: https://img.shields.io/badge/license-GPL--3.0-orange.svg?style=plastic