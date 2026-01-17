# HashCat

### Example use

```
hashcat -m 10 -a 0 [file with hash] [wordlst]
```

---

at **-m** you need to decide what hash type is used 
at it thos links can help you

https://hashcat.net/wiki/doku.php?id=hashcat

https://hashcat.net/wiki/doku.php?id=example_hashes

https://github.com/psypanda/hashID

https://www.tunnelsup.com/hash-analyzer/

---

**-a 0** most basic attack type its just use wordlist you privide

**-a 1** this one combine words form wordlist for example "pass" and "123"
attack type 1 whoud use it like that

```
pass
123
pass123
```

**-a 3** Mask attack 

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
?a 	?l?u?d?s
?b 	0x00 – 0xff
