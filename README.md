# Linux_Tips
Notes / Tips for me using Linux (Debian based Distros, I use Pop_os and Ubuntu)


## Rasberry Pi / Rasbian, Raspberry Pi OS

1. Simple Set up wizard, examples Change Hostname

  ```BASH
  sudo raspi-config
  ```
## Seeing cool ASCII Art in Terminal (any Debian Distro)

1. Install Neofetch

```BASH
sudo apt install neofetch
```

2. Check run in the Terminal

```BASH
neofetch
```

3. results
![Ran Neofetch in Terminal](https://github.com/Coryf65/Linux_Tips/blob/main/_images/Screenshot%20from%202020-11-24%2023-32-47.png)


## Styling the Terminal !

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
