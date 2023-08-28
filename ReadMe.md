# chksum

> A script to check/verify checksums. Some sites offer a checksum file, while others offer the checksum to copy (as text) to manually compare against - or to create checksum files, like: `fooBar.txt.sha256` or: `CHECKSUMS.rmd160` (batch).

- - -

[![][mainBadge]][main] [![GitLab release][latestBadge]][latest]

![][licenseBadge]

 

## Install

Put the script in `/usr/local/bin`, or any folder of your choice. Just make sure it's in `$PATH`.

```
$ cd /path/to/chksum
$ sudo install -v -m755 -o0 -g0 chksum /usr/local/bin
```


## Usage

```
Verifying:
    chksum <mode <checksum> <file>

Creating checksum files:
    chksum -a <files>
    chksum -o <mode> <files>
    chksum -b <mode> <files>

Modes:
    md5|sha[1|224|256|384|512]|r[ipe]md160|whirlpool
    [!] When creating checksum files... MD5 or SHA[1] are not accepted.
```


## Examples

Success:
```
$ chksum sha da39a3ee5e6b4b0d3255bfef95601890afd80709 test.txt
test.txt:		... OK
```

Error:
```
$ chksum sha da39a3ee5e6b4b0d3255bfef95601890afd80708 test.txt
test.txt:		... FAILED

chksum: WARNING: The checksum (da39a3ee5e6b4b0d3255bfef95601890afd80708) did NOT match
```

Creating files:
```
$ chksum -o rmd160 test.txt         // test.txt.rmd160
$ chksum -a test.txt                // test.txt.rmd.160 + test.txt.sha256
$ chksum -b sha256 test_0{1..5}.txt // CHECKSUMS.sha256 with all in 1 file
```

_The text format of the output file is:_
```
da39a3ee5e6b4b0d3255bfef95601890afd80709 */path/to/test.txt
```


## License and Info

![][licenseBadge]

[gitlab.com/iefdev/chksum][gl]


## Contributing

1. Fork it (<https://gitlab.com/iefdev/chksum/-/forks/new>)
2. Create your feature branch (`git switch -c feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Merge Request


<!-- Markdown: link & image dfn's -->
[gl]: https://gitlab.com/iefdev/chksum
[licenseBadge]: https://img.shields.io/badge/license-GPL--3.0--or--later-C00?style=plastic "GPL v3.0 or later"
[mainBadge]: https://img.shields.io/badge/main-v1.99-778899.svg?logo=gitlab&style=plastic
[main]: https://gitlab.com/iefdev/mkpwd/ "main branch"
[latestBadge]: https://img.shields.io/badge/latest-v1.0.1-blue.svg?logo=gitlab&style=plastic
[latest]: https://gitlab.com/iefdev/chksum/-/releases/ "Latest tag/release"
