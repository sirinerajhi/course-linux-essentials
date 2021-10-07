---
description: ....
title: Getting Help
---

# Getting Help

Everyone needs some help from time to time. Basically thats what the man pages are for.

## Man pages

Man (`man` stands for manual) pages are used to describe the features of commands. They will provide you with a basic description of the purpose of the command, as well as provide details regarding the options of the command.

![Man page of uname command](./img/man_uname.png)

The man command uses a "pager" to display documents. Normally this pager is the `less` command. A pager is something that most administrators use frequently, to view files, read the results of long command output, and more. Common pager utils are `more` and `less`.

The most used commands inside the man pages are listed in the next table.

| Command | Description |
| ---- | ---- |
| `ENTER` | Go down a line |
| `SPACE` | Go down a page |
| `/keyword` | Search for keyword |
| `n` | Find next search item |
| `g` | Goto beginning |
| `G` | Goto end |
| `h` | Show help |
| `q` | Quit man pages |

### Sections of a man page

Man pages are broken into **sections**. Each section is designed to provide specific information about a command.

* **NAME**: Name of command and brief description.
* **SYNOPSIS**: Provides examples.
* **DESCRIPTION**: More detailed description.
* **OPTIONS**: Lists the options for the command with a description.
* **FILES**: Lists the files that are associated with the command as well as a description of how they are used. These files may be used to configure the command's more advanced features.
* **AUTHOR**: The name of the person who created the man page and (sometimes) how to contact the person.
* **REPORTING BUGS**: Provides details on how to report problems with the command.
* **COPYRIGHT**: Provides basic copyright information.
* **SEE ALSO**: Provides you with an idea of where you can find additional information.This also will often include other commands that are related to this command.

Sometimes configuration files also have man pages. Configuration files (sometimes called system files) contain information that is used to store information about the Operating System or services.

### Sections of the man pages

There are thousands of man pages on a typical Linux distribution. To organize all of these man pages, the pages are **categorized by sections**, much like each individual man page is broken into sections.

1) Executable programs or shell commands
2) System calls (functions provided by the kernel)
3) Library calls (functions within program libraries)
4) Special files (usually found in /dev)
5) File formats and conventions, e.g. /etc/passwd
6) Games
7) Miscellaneous (including macro packages and conventions)
8) System administration commands (usually only for root)
9) Kernel routines [Non standard]

When you use the man` command, it searches each of these sections **in order** until it finds the first "match".

For example:

```bash
[bioboost@linux][~]$ man echo
```

To determine which section a specific man page belongs to, look at the numeric value on the first line of the output of the man page.

![Man page section](./img/man_echo.png)

In some cases you will need to specify the section in order to display the correct man page. This is necessary because sometimes there will be man pages with the same name in different sections.

There is for example a man page about the `passwd` command (section 1) but also about the file `/etc/passwd` (section 5). To request a man page from a specific section, just add the number before the name of the man page.

```bash
[bioboost@linux][~]$ man 5 passwd
```

### Partial Matches

The `-f` option to the `man` command will display man pages that match, or partially match, a specific name and provide a brief description of each man page.

```bash
[bioboost@linux][~]$ man -f ip
```

::: output
<pre>
ip (7)               - Linux IPv4 protocol implementation
ip (8)               - show / manipulate routing, network devices, interfaces...
</pre>
:::

Note that on most Linux distributions, the `whatis` command does the same thing as `man -f`.

```bash
[bioboost@linux][~]$ whatis ip
```

::: output
<pre>
ip (7)               - Linux IPv4 protocol implementation
ip (8)               - show / manipulate routing, network devices, interfaces...
</pre>
:::

### Search by Keyword

You can search for a keyword in the man pages names and the short descriptions by using the `-k` option.

```bash
[bioboost@linux][~]$ man -k ssh
```

::: output
<pre>
authorized_keys (5)  - OpenSSH SSH daemon
rlogin (1)           - OpenSSH SSH client (remote login program)
</pre>
:::

The `apropos` command does the same thing as `man -k`.

```bash
[bioboost@linux][~]$ apropos ssh
```

::: output
<pre>
authorized_keys (5)  - OpenSSH SSH daemon
rlogin (1)           - OpenSSH SSH client (remote login program)
</pre>
:::

You can use the `apropos` command to find a specific command based on its description. This is especially helpfull when you know what you want to achieve but don't know what command to use.

## Info

The `info` command also provides documentation on operating system commands and features. The goal of this command is slightly different from the man pages.

Consider man pages to be more of a reference resource and info documents to be more of a learning guide.

You may need to install info: `sudo apt install info`

```bash
[bioboost@linux][~]$ info ls
```

The info command automatically redirects to man pages if no info exists.

Like the `man` command, you can get a listing of traverse keys by typing the letter `h` while reading the info documentation.

## Command help

Many commands will also provide you basic information, very similar to the SYNOPSIS found in man pages, when you apply the `--help`, `-h` or `-?` option to the command.

```bash
[bioboost@linux][~]$ passwd --help
```

::: output
<pre>
Usage: passwd [options] [LOGIN]

Options:
  -a, --all                     report password status on all accounts
  -d, --delete                  delete the password for the named account
  -e, --expire                  force expire the password for the named account
  -h, --help                    display this help message and exit
  -k, --keep-tokens             change password only if expired
  -i, --inactive INACTIVE       set password inactive after expiration
</pre>
:::

## Documentation

On most systems, there is a directory where additional documentation is found. This will often be a place where vendors who create additional (third party) software can store documentation files. These documentation files are often called readme files, since the files typically have names such as `README` or `readme.txt`.

Typical locations include `/usr/share/doc` and `/usr/doc`.

## Challenges

Find all the info you need in the man-pages. Make sure to comment the commands you used to find this information. No google!

Mark challenges using a ✅ once they are finished.

### ✅ The free command

*Describe in your own words what the `free` command does. Give an example and a partial output.*

It gives an overview of the used and free memory, but also other details such as shared, buffer and available memory. It is presented in kilobytes.

|:|total| used | free | shared| buff/cache | available|
| Mem: | 16594724 | 7323652 | 9041720 | 17720 | 229352 | 9137340 |
| Swap: | 50331648 | 64236 | 50267412 |

### ✅ The id command

*Describe in your own words what the `id` command does. Give an example and a partial output.*

Gives information about the user that is currently using the system.

uid=1000(sirine) gid=1000(sirine) groups=1000(sirine),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),117(netdev)

### ✅ The tree command

*Describe in your own words what the `tree` command does. How do you list all subdirectories too? How can you only include directories? If the `tree` command is not available on your system you can install it using `sudo apt install tree`*

It lists all the directories in a easily readable (tree) format. You can add -a to view subdirectories and -d to view directories only.

subdirectories included example:
.
├── .bash_history
├── .bash_logout
├── .bashrc
├── .landscape
│   └── sysinfo.log
├── .lesshst
├── .motd_shown
├── .profile
└── .sudo_as_admin_successful

### ✅ The which command

*Describe in your own words what the `which` command does. What is the result for `pwd` ?*

Which displays the pathnames that are executed in the current environment. The pwd displays the path to the currently used environment. Result:
/usr/bin/pwd

### ✅ The file command

*Describe in your own words what the `file` command does. What is the result for `~/.bashrc` ?*

File displays which type the specified file is. Result: ASCII text

### ✅ The type command

*Describe in your own words what the `type` command does. What is the result for `ls` and what is the result for `g++` ?*

Type displays information about a command, e.g. if it's a shell built-in, function, alias, file or keyword. ls is an alias for 'ls --color=auto', g++ is '/usr/bin/g++'

### ✅ Counting lines and words

*What command can be used to count lines and words in text? Give an example and explain the output.*

wc -l to count lines, wc -w to count words
Example:
wc -lw ~/.bashrc
117  518 /home/sirine/.bashrc

### ✅ The wget command

*How can you download a file from the Internet using the command line?. Find a file online to use it on and demonstrate its usage.*

You can download files from the internet with the wget command.
Example:
wget https://linux-essentials.netlify.app/
--2021-09-30 13:01:56--  https://linux-essentials.netlify.app/
Resolving linux-essentials.netlify.app (linux-essentials.netlify.app)... 206.189.58.26, 18.192.76.182, 2a05:d014:275:cb00:c26c:5b6d:e2c8:e5a, ...
Connecting to linux-essentials.netlify.app (linux-essentials.netlify.app)|206.189.58.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘index.html’

index.html                        [ <=>                                           ]  14.56K  --.-KB/s    in 0.01s

2021-09-30 13:01:58 (1.12 MB/s) - ‘index.html’ saved [14913]

### ✅ The dmesg command

*Describe in your own words what the `dmesg` command does. Give an example and a partial output.*

This command can be used (with options) to control or print the kernel ring buffer.
Example:
[    0.015364]  Microsoft 4.4.0-19041.1237-Microsoft 4.4.35
[    0.064459] <3>init: (1) ERROR: ConfigInitializeCommon:570: Failed to mount /usr/lib/wsl/drive
[    0.064463] : 19
[    0.064559] <3>init: (1) ERROR: ConfigInitializeCommon:570: Failed to mount /usr/lib/wsl/lib
[    0.064561] 19

### ✅ Checksums

*Go to the website of Raspberry Pi - [https://www.raspberrypi.org/software/operating-systems](https://www.raspberrypi.org/software/operating-systems) and download the Raspberry Pi OS image using the `wget` command line tool. Now check if the SHA-256 checksum complies with the one being advertised on the website.*

*What tool did you use to calculate the checksum? Demonstrate its usage.*

First installed the hashalot with `sudo apt install hashalot`, then `sha356sum` and the name of the file (2021-05-07-raspios-buster-armhf-lite.zip)

*What is the use of this hash?*

It checks if there were any errors while downloaded.

### ✅ The printenv command

*Describe in your own words what the `printenv` command does.*

You can print your environment with this command.

### IP Address

*Find the IP address of your WiFi interface. What command did you use?*

### IP Address of Sivir Server

*What is the IP address of the internal server `sivir.devbit.be`? Make sure you are connected to the `Devbit` network.*
