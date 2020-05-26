# Pretty Good Privacy (PGP) Implementation

  > I am going to use PGP to perform encryption. I am using Centos 7  so I will install it from "yum" repository. First I need to install the software, then generate a public/private key pair.



## Installing / Getting started

1. A quick introduction of the minimal setup you need to get a PGP up &
running.

```shell
(base) [aty@aty ~]$ sudo yum install gnupg
[sudo] password for aty: 
Loaded plugins: fastestmirror, langpacks
Determining fastest mirrors
epel/x86_64/metalink                                                                                                           |  27 kB  00:00:00     
 * base: mirror.rackdc.com
 * epel: mirror.veriteknik.net.tr
 * extras: mirror.muvhost.com
 * nux-dextop: li.nux.ro
 * rpmfusion-free-updates: ftp-stud.hs-esslingen.de
 * updates: mirror.rackdc.com
FedoraPeople-sea                                                                                                               | 2.9 kB  00:00:00     
base                                                                                                                           | 3.6 kB  00:00:00     
docker-ce-stable                                                                                                               | 3.5 kB  00:00:00     
epel                                                                                                                           | 5.3 kB  00:00:00     
extras                                                                                                                         | 2.9 kB  00:00:00     
nodesource                                                                                                                     | 2.5 kB  00:00:00     
nux-dextop                                                                                                                     | 2.9 kB  00:00:00     
rpmfusion-free-updates                                                                                                         | 3.7 kB  00:00:01     
updates                                                                                                                        | 2.9 kB  00:00:00     
(1/4): rpmfusion-free-updates/x86_64/primary_db                                                                                | 254 kB  00:00:28     
(2/4): epel/x86_64/updateinfo                                                                                                  | 1.0 MB  00:00:45     
(3/4): updates/7/x86_64/primary_db                                                                                             | 5.9 MB  00:01:53     
(4/4): epel/x86_64/primary_db                                                                                                  | 6.9 MB  00:02:37     
Package gnupg2-2.0.22-5.el7_5.x86_64 already installed and latest version
Nothing to do
```

  Above, it shows that GNUPG is already installed on my computer.

### Initial Configuration

1. Now, Then I will generate a public/private key pairs.

```shell
(base) [aty@aty ~]$ gpg --gen-key
gpg (GnuPG) 2.0.22; Copyright (C) 2013 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? RSA
Invalid selection.
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 
Requested keysize is 2048 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 
Key does not expire at all
Is this correct? (y/N) y
GnuPG needs to construct a user ID to identify your key.
Real name: aty
Name must be at least 5 characters long
Real name: alitaha
Email address: xxx@yahoo.com
Comment: 
You selected this USER-ID:
    "att <xxx@yahoo.com>"
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
You need a Passphrase to protect your secret key.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key BB4F7450 marked as ultimately trusted
public and secret key created and signed.
gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
pub   2048R/BB4F7450 2020-01-05
      Key fingerprint = DEEA CF6B EF72 590A C711  7155 469C AA6F BB4F 7450
uid                  att <aykseldi1@yahoo.com>
sub   2048R/1C9F094D 2020-01-05
```
![Public key generation](https://github.com/aykseldi/PGP-Implementation/blob/master/Snapshot1.png)

## Developing

Here's a brief intro about what a developer must do in order to start developing
the project further, I  created  keys and list is shown below.

```shell
(base) [aty@aty ~]$  gpg --list-keys
/home/aty/.gnupg/pubring.gpg
----------------------------
pub   2048R/BB4F7450 2020-01-05
uid                  alitaha <aykseldi1@yahoo.com>
sub   2048R/1C9F094D 2020-01-05
```

### Building

Some additional steps for the developer to build the project after some code changes. 

It's time to encrypt files with GPG. So I first created a file named plaintext.txt on /home/aty/Desktop/PGP folder. I inserted some text into file. When I run the comman , it will encrypt the file with the keys that I determined previous steps. I prefered 2048 bit RSA key pair while installation.

```shell
(base) [aty@aty PGP]$ gpg -e plaintext.txt 
You did not specify a user ID. (you may use "-r")
Current recipients:
Enter the user ID.  End with an empty line: alitaha
Current recipients:
2048R/1C9F094D 2020-01-05 "alitaha <aykseldi1@yahoo.com>"
Enter the user ID.  End with an empty line:
```

Here  what actually happens when the code above gets executed. I verified that I now  have encrypted files present in my directory.

```shell
(base) [aty@aty PGP]$ ll
total 296
-rw-rw-r--. 1 aty aty     61 Jan  5 17:53 plaintext.txt
-rw-rw-r--. 1 aty aty    396 Jan  5 19:47 plaintext.txt.gpg
```
When I tried to view the contents of this file I found that it's a binary.



```shell
(base) [aty@aty PGP]$ cat plaintext.txt.gpg 
�
  ���	M�&���#a��/Ŗۖ�R����
                             ��W7�x�Q8
                                         03��
                                             ���_�1��-�iN��:;�W荠f����b3D
                                                                         ­�sq�H��bY��5�����‑�ӓ�@Xf^��z�,jD��e�<��|"��'f�(�	����*V@�s=��/�
                            d\�f([��6�����m���%kX��e�ϲ��ͮ^Η�~S��3���#i�V4Jf2Q��S�n��5Ʋ_.�y6��.ů����d��/M]�p��:�z�(s1[Cw�s�A��{h�
                                                                                                 8W�2�E5�neXmk���q�PV�*`��ex�=f�&�Vs��y��,dMg�]YyH;��y�t��d���F���s����������=�!I)�wL���LZ��)N��d,&;R�u
```

### Deploying / Publishing

In case there's some step you have to take that publishes this project to a
server, this is the right time to state it.

```shell
packagemanager deploy awesome-project -s server.com -u username -p password
```

And again you'd need to tell what the previous code actually does.

## Features

What's all the bells and whistles this project can perform?
* What's the main functionality
* You can also do another thing
* If you get really randy, you can even do this

## Configuration

Here you should write what are all of the configurations a user can enter when
using the project.

#### Argument 1
Type: `String`  
Default: `'default value'`

State what an argument does and how you can use it. If needed, you can provide
an example below.

Example:
```bash
awesome-project "Some other value"  # Prints "You're nailing this readme!"
```

#### Argument 2
Type: `Number|Boolean`  
Default: 100

Copy-paste as many of these as you need.

## Contributing

When you publish something open source, one of the greatest motivations is that
anyone can just jump in and start contributing to your project.

These paragraphs are meant to welcome those kind souls to feel that they are
needed. You should state something like:

"If you'd like to contribute, please fork the repository and use a feature
branch. Pull requests are warmly welcome."

If there's anything else the developer needs to know (e.g. the code style
guide), you should link it here. If there's a lot of things to take into
consideration, it is common to separate this section to its own file called
`CONTRIBUTING.md` (or similar). If so, you should say that it exists here.

## Links

Even though this information can be found inside the project on machine-readable
format like in a .json file, it's good to include a summary of most useful
links to humans using your project. You can include links like:

- Project homepage: https://your.github.com/awesome-project/
- Repository: https://github.com/your/awesome-project/
- Issue tracker: https://github.com/your/awesome-project/issues
  - In case of sensitive bugs like security vulnerabilities, please contact
    my@email.com directly instead of using issue tracker. We value your effort
    to improve the security and privacy of this project!
- Related projects:
  - Your other project: https://github.com/your/other-project/
  - Someone else's project: https://github.com/someones/awesome-project/


## Licensing

One really important part: Give your project a proper license. Here you should
state what the license is and how to find the text version of the license.
Something like:

"The code in this project is licensed under MIT license."
