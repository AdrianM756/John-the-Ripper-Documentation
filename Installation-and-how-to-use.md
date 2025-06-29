[John the Ripper](https://www.openwall.com/john/) is an Open Source password security auditing and password recovery tool.

![image](https://prd-cyberhub.oss-me-central-1.aliyuncs.com/uploads/ktetjCi-13QlTUNjeTWySQGxSRquwk)

## Installation

On this demo, we will installing ** John the Ripper on Ubuntu. To install, input the following commands on the terminal.

```
apt install john -y
```

To check if it is installed, we can simply type ```john```. We should be able to get a similar output.

```
John the Ripper password cracker, version 1.8.0
Copyright (c) 1996-2013 by Solar Designer
Homepage: http://www.openwall.com/john/

Usage: john [OPTIONS] [PASSWORD-FILES]
--single                   "single crack" mode
--wordlist=FILE --stdin    wordlist mode, read words from FILE or stdin
--rules                    enable word mangling rules for wordlist mode
--incremental[=MODE]       "incremental" mode [using section MODE]
--external=MODE            external mode or word filter
--stdout[=LENGTH]          just output candidate passwords [cut at LENGTH]
--restore[=NAME]           restore an interrupted session [called NAME]
--session=NAME             give a new session the NAME
--status[=NAME]            print status of a session [called NAME]
--make-charset=FILE        make a charset, FILE will be overwritten
--show                     show cracked passwords
--test[=TIME]              run tests and benchmarks for TIME seconds each
--users=[-]LOGIN|UID[,..]  [do not] load this (these) user(s) only
--groups=[-]GID[,..]       load users [not] of this (these) group(s) only
--shells=[-]SHELL[,..]     load users with[out] this (these) shell(s) only
--salts=[-]N               load salts with[out] at least N passwords only
--save-memory=LEVEL        enable memory saving, at LEVEL 1..3
--node=MIN[-MAX]/TOTAL     this node's number range out of TOTAL count
--fork=N                   fork N processes
--format=NAME              force hash type NAME: descrypt/bsdicrypt/md5crypt/
                           bcrypt/LM/AFS/tripcode/dummy/crypt
```
<br>

## Cracking User's Credential

To test this tool, we have created a prepared a user named ```johntest``` to crack it's user password. To cracked it's password, we be needing to retrieve it's hash that is located in ``` /etc/shadow``` then output the file a textfile which we will name as ```johnpass.txt```. To do this, we will be using the commnands:

```
cat /etc/shadow | grep johntest > johnpass.txt
```
We will then now to crack the hash using ** John the Ripper**. To do this, we will use the following commands:

```
john -format=crypt johnpass.txt
```
Wait for a bit as it may take some time. Once the ```Session completed``` appears, it means that it successfully cracked the hash. To check the cracked password, use the command:

```
john -show johnpass.txt
```
