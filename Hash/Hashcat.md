# HashCat

### Example use

```
hashcat -m 10 -a 0 [file with hash] [wordlst]
```

---

With -m you need to specify the hash type being used.
The following links can help you identify the correct hash mode:

https://hashcat.net/wiki/doku.php?id=hashcat

https://hashcat.net/wiki/doku.php?id=example_hashes

https://github.com/psypanda/hashID

https://www.tunnelsup.com/hash-analyzer/

---

**-a 0** (Straight attack)

The most basic attack type. It uses a single wordlist and tries each entry as a password candidate.

**-a 1** (Combination attack)

Uses two wordlists and combines each word from the first list with each word from the second list.
For example, combining pass from the first wordlist and 123 from the second wordlist will produce pass123.

```
hashcat -a 1 hashes.txt wordlist1.txt wordlist2.txt
```

**-a 3** (Mask attack)

Used when you know the password pattern but not the exact characters.
Instead of a wordlist, you define a mask that describes the character type for each position.

Example: password = 3 lowercase letters + 3 digits

```
hashcat -m 10 -a 3 [file with hash] ?l?l?l?d?d?d
```

?l	abcdefghijklmnopqrstuvwxyz

?u	ABCDEFGHIJKLMNOPQRSTUVWXYZ

?d	123456789

?h	0123456789abcdef

?H	0123456789ABCDEF

?s	!”#$%&'()*+,-./:;<=>?@[\]^_`{|}~

?b 	0x00 – 0xff

