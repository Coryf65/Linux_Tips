# Linux_Tips
Notes / Tips for me using Linux (Debian based Distros, I use Pop_os and Ubuntu)

- [Configure Raspberry Pi options](#configure-raspberry-pi-options)
- [Neofetch, system info](#neofetch)
- [Styling the Terminal](#styling-the-terminal)
- [Linux Server more security](#server-security)
- [ssh keys for logging in](#ssh-keys)

## Configure Raspberry Pi Options

1. Simple Set up wizard, examples Change Hostname on Rasberry Pi / Rasbian, Raspberry Pi OS

  ```BASH
  sudo raspi-config
  ```
  
## Neofetch

Seeing cool ASCII Art with system info in Terminal (any Debian Distro)

*install*
```BASH
sudo apt install neofetch
```
*run*
```BASH
neofetch
```

*output*

![Ran Neofetch in Terminal](https://github.com/Coryf65/Linux_Tips/blob/main/_images/Screenshot%20from%202020-11-24%2023-32-47.png)


## Styling the Terminal

- I followed ChrisTitusTech's YouTube Video [here](https://youtu.be/iaXQdyHRL8M)
- I am using a Debian Based Distro

1. Install Powerline Fonts

```BASH
sudo apt-get install fonts-powerline
```

2. Change your bash.rc file

- I am using VSCode to edit the file, you could use *nano*

```BASH
code .bashrc
```

3. Copy and Paste from the changed bashrc file

https://raw.githubusercontent.com/ChrisTitusTech/scripts/master/fancy-bash-promt.sh

Other option is to use ohmyposh

# Windows Terminal Oh-My-Posh Setup

[What is Oh My Posh?](https://ohmyposh.dev/docs/)
[What is Windows Terminal?](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701)

## How to Setup Oh My Posh

1. Follow along with Scott Hanselman

[YouTube Video with Scott](https://youtu.be/lu__oGZVT98)

## See Themes you can use

```Powershell
Get-PoshThemes
```

> Note: You may need to install a Powerline font to have icons display correctly.

- I use Cascadia Code PL [here](https://github.com/microsoft/cascadia-code/releases)
- I also use a Nerd Font for more fun things [here](https://www.nerdfonts.com/font-downloads)

## Setting Default Theme

- Open your ~/.bashrc file with nano ~/.bashrc or the text editor of your choice. This is a bash script that runs every time bash starts. Add the following (change the theme to the one you like):

> Open Windows Terminal

> Open VSCode with the Profile settings file

```bash
code $PROFILE
 ```
- Add the Default theme desired into the file like so...

```Powershell
# Adding default theme setup
Set-PoshPrompt -Theme jandedobbeleer
```

- List out Themes

```Powershell
Get-PoshThemes C:\Users\Cory\AppData\Local\Programs\oh-my-posh\themes
```

## Server Security

Automatic updates, updates stable packages automatically.

*install*
```bash
sudo apt install unattended-upgrades
```

*configure*
```bash
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

*then click yes to allow*
![output from running the reconfigure, a yes or no option](https://user-images.githubusercontent.com/20805058/234682184-164798e3-5794-4093-80d1-c17a40f12780.png)

## ssh keys

# Setting up SSH keys for login of Linux Servers

For those of you whom like a video to follow along https://youtu.be/YS5Zh7KExvE "Learn Linux TV YouTube video"

> Note: I am using Ubuntu / PopOS a Debian based Distro, and the GNOME Desktop

## See if SSH is installed

- See if we have ssh installed

> Linux, and Mac based OS

```bash
which ssh
```
- should see a directory path, if so the ssh client is installed
`/usr/bin/ssh`

> Windows Based OS

- usually people either use PUTTY or Windows Terminal

[putty](https://www.putty.org/)


## Generating a Key Pair

- check if we have one already
```bash
ls -l ~/.ssh
```

> :warning: If you see keys / any files in here please back them up. the next few steps WILL overwrite... them if you use the default name and settings :warning:

- we should see `total 0`

    - if not backup these files, or skip creating them to use these

We have some options on how to create a key.

default, hit enter on all prompts... 
> WILL overwrite if a key exists with the default name (id_rsa):
```bash
$ ssh-keygen

Generating public/private rsa key pair.
Enter file in which to save the key (/home/username/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/username/.ssh/id_rsa
Your public key has been saved in /home/username/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:Oo95CARZs4cEyW7HDbLrZ4BZEBWPQ0utu2FcimDvtM0 username@computername
The key's randomart image is:
+---[RSA 3072]----+
|                 |
|                 |
|              .  |
|     q   1 . ..o.|
|    wdawdawdawda=|
|   aa a a a    a |
|    a   a a a a  |
|   adawdaw awd a |
|   .233443334. . |
+----[SHA256]-----+
```

We can also set things like the key type and key name !

- (optional defaults to rsa) set key type: `-t "type of key"` options [-t dsa | ecdsa | ecdsa-sk | ed25519 | ed25519-sk | rsa]
- (optional) set a comment: `-C "game server or company name"`
- (optional) set a bit size `-b 4096`

```bash
ssh-keygen -t ed25519 -C "my minecraft server"
```

during this prompt we can change the keys name here
```bash
Enter file in which to save the key (/home/username/.ssh/id_rsa): /home/username/.ssh/company_id_ed25519
```

> If using for work or company related things please use a passphrase

    - Then it will asks where we want to save the key, which we can just use the default by hitting enter
    - Then it will ask for a passphrase: (reccommended)
> :warning: if you entered one, you will not be able to get it back

### If you already have a key pair to use then skip [here](https://gist.github.com/Coryf65/29c62fca81eb0a3f2d48df1d05839e46#now-we-can-copy-our-public-key-to-our-server)

- You will get 2 :key: files created in the directory you chose

    - Private Key :key:
    `id_rsa`
    - Public Key :key:
    `id_rsa.pub`

> :spiral_notepad: DO NOT SHARE your private key with anyone
- you can see your Public Key as follows
```bash
cat ~/.ssh/id_rsa.pub
```

## Now we can copy our Public Key to our Server

1. Connect with SSH
```bash
ssh username@hostname
```
- example
`ssh testuser@192.168.1.2`

2. exit our ssh session

3. Copy our key into our server
    - we can copy the key using a simple commmand 
    ```bash
    ssh-copy-id username@ip/hostname
    ```
    - example `ssh-copy-id root@192.168.1.2`
    
    *we can copy a specific key using the following*
    ```bash
    ssh-copy-id -i ~/.ssh/mykey user@host
    ```
    - then we need to enter our password for the user on the server

4. Now we can test by ssh-ing back in

- We should be good for using our Key now.

:partying_face: Congrats! we did it !


<details open>
<summary>Screen commands</summary>
<br>

1. Create a new Screen

```bash
$ screen -S "name of the new screen"
```

2. Exit current screen

```
Control + a + d
```

3. Check for any screens that are running

```bash
$ screen -list
```

4. End a screen session by name

```bash
$ screen -XS "screen name"
```

 - or by the id which you get from the list command #3

```bash
$ screen -XS id
```

5. Re-attch to an open session by name or id

```bash
$ screen -r name
```

 - or 

```bash
$ screen -r id
```

</details>

<details open>
<summary> commands</summary>
<br>
