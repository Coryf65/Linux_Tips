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



```bash
```


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
