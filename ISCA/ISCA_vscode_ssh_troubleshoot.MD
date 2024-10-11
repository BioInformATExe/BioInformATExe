# Issues relating to failing to install the VS Code server onto ISCA

### How to manually install the server for when you find you **_can_ connect to ISCA in a regular terminal** but not with VSCode remote-ssh.

If you can't connect to ISCA in any terminal, make sure you are using the VPN if off campus, and inspect your local .ssh/config and .ssh/known_hosts files. You may also have issues with proxy settings. 

## The .vscode-server directory

Most issues connecting to ISCA are to do with the failure to correctly install the .vscode-server files in the correct path on ISCA. This happens after installing VSCode for the first time, or updating it. 

The `.vscode-server`directory is usually installed by VSCode when you connect remotely to a machine, but ISCA's firewall won't allow the installation of any files from the internet, which prevents the normal install from happening. 

The easiest solution to this is to manually download the server.

## 1. Check your .vscode-server directory on ISCA (OPTIONAL - you can skip straight to 2)

This step is optional because it basically just double checks that this is the cause of your issue.

```
# Log in to ISCA in another terminal.

ssh user123@login.isca.ex.ac.uk

# Make sure you're in your home directory

cd ~

# Look for your .vscode-server directory. It's hidden so to see it you need to use ls -a

ls -a

# Enter the directory and it's /bin subdirectory

cd .vscode-server/bin

# Check which versions you have installed:

ls 

# You should see something like this:
92da9481c0904c6adfe372c12da3b7748d74bdcb
d037ac076cee195194f93ce6fe2bdfe2969cc82d

```

The strings of numbers above are directories relating to a specific commit of VS-code. If you don't have the correct one installed (detailed below), you won't be able to connect remotely using remote-ssh.
If you've only used one version of VSCode, there should be only one directory like this. 

Let's inspect the contents of these directories:

```
# Inside a directory:
ls d037ac076cee195194f93ce6fe2bdfe2969cc82d
bin  extensions  LICENSE  node  node_modules  out  package.json  product.json

# Let's also check inside of /bin/
ls d037ac076cee195194f93ce6fe2bdfe2969cc82d/bin
code-server  helpers  remote-cli

```

### If your long string of numbers and letters directory is empty, the install has failed and you should do it manually. If you do have this contents but have multiple such directories, it's likely that you don't have the installation for the versio you're currently trying to use.

## 2. Getting the correct files onto ISCA:

### 2.1 Identify the correct version.

1. Open VSCode
2. Click on Code on the top bar >About Visual Studio Code  [This is the path on my mac; it may differ on Windows or Linux]

This should open a popup that contains version and commit info:

```
Version: 1.84.0 (Universal)
Commit: d037ac076cee195194f93ce6fe2bdfe2969cc82d
```

It is this commit string that needs to match an install in your .vscode-server 

### 2.2 Download the correct server onto your local machine. 

You need to download the correct commit. You want to download the server-linux-x64/stable version regardless of your local machine type, as we're transferring this file to ISCA.

Edit the commit string below so it matches your commit:

```
wget  https://update.code.visualstudio.com/commit:d037ac076cee195194f93ce6fe2bdfe2969cc82d/server-linux-x64/stable

```
You may need to install wget first if it isn't on your local machine. If you have homebrew installed you can used `brew install wget` to do so.

When this has worked, you should rename the download so it's clear that it's a .tar.gz - you may not see the file appear in the folder but stay in the directory you downloaded it into.

```
mv stable vscode-server-linux.tar.gz
```

### 2.3 Transfer the file to ISCA. You can use scp or rsync:

```
scp vscode-server-linux.tar.gz user123@login.isca.ex.ac.uk:/lustre/home/user123/.vscode-server/bin/d037ac076cee195194f93ce6fe2bdfe2969cc82d/vscode-server.tar.gz
```

### 2.4 Unzip the file:

In your regular terminal that is logged in to ISCA:

```
# Go to the directory for the commit:
cd /lustre/home/user123/.vscode-server/bin/d037ac076cee195194f93ce6fe2bdfe2969cc82d/

# Unzip the .tar.gz :
tar -xzf vscode-server.tar.gz

# Make a .done file to tell VSCode that the install is done:
touch /lustre/home/user123/.vscode-server/bin/d037ac076cee195194f93ce6fe2bdfe2969cc82d/vscode-server.tar.gz.done

```

DO NOT delete the .tar.gz after unzipping it. VSCode checks for its presence when connecting and will try (and fail) to download it if it isn't there.

# 3. Attempt to reconnect with ISCA.

Good luck.










