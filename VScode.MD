# What is VS Code?
VS Code is a code editor which acts as a terminal, script editor and file viewer all in one. It allows you to do multiple things at once, instead of closing the terminal to open a script and closing the script to return to the terminal, as other editors often do.
You can use it on your personal computer, or on remote HPCs.

## On VS Code, you can:
- View a script and the terminal at the same time.
- "Split" the terminal into two or more so you can be and code in multiple directories at once. 
- View PDFs and other visual file types.
- Edit markdown files and view them in real-time.
- Navigate a remote computer's directories by clicking like in a normal folder.
- Compare files side by side (and highlight differences)
- Find and replace text strings in a script. 
- Run scripts and commands as you normally would from any other terminal, including on normal and interactive nodes on HPCs.

## How to install VS Code

Here are installation instructions for [linux](https://code.visualstudio.com/docs/setup/linux), [macOS](https://code.visualstudio.com/docs/setup/mac) and [Windows](https://code.visualstudio.com/docs/setup/windows). 
Note that macOS users will need to manually install the code command manually, which is used to open a file in the editor (similar to `nano filename.txt`, `code filename.txt` opens the file in VS Code. filename.txt does not exist, it will create it.)

The `code` command can be used to create, view and edit files, and to open file formats like PDFs, web links and images. 

## The Terminal
You can open a terminal by pressing `CTRL+SHIFT+@` (`COMMAND+SHIFT+@` on macOS). The default position is at the bottom of the screen. You can adjust its height by clicking and dragging the top of it. 
The terminal has several tabs of its own along the top of it, which let you switch to viewing problems, outputs, debugging, and port forwarding. 
To the right of the top bar of the terminal, the coding language you are using is displayed. 
To its right is a large + plus sign; clicking this opens another terminal in the same directory and a side bar to switch between them. 
To the right of this is a split terminal option (two rectangles side-by-side). This opens a new terminal in the same directory to the right of the existing one. Their width can be adjusted by dragging the divider. It also opens the side bar to see an overview of them and close any you want to shut down. 
Besides this, the `...` button lets you do things like clear the terminal, and the `^` button lets you make the terminal take up the whole vertical span of the screen. 


## File Explorer
The file explorer is a document symbol on the left bar of the window. When you click on it, it will give you the options to open a folder or clone a repository. If you open a folder, you can open a local one (choose the parent directory of your files, as you won't be able to navigate beyond it with the file explorer - though you can with the terminal). You can also open a remote computer's directories, if you have the Remote Explorer extension (more on this below). 

**Left clicking on a directory** opens or closes it in the display. 

**Right clicking a directory** will let you make more files or directories, or copy its path (or relative path).

A **single left click on a file** opens it in the current tab. A *double left click* will open it in a new tab in the same window, keeping the old one open. 

**Right clicking a file** gives you options relating to that file. You can select a file for comparison and then right click on another file and compare the two visually side-by-side, highlighting differences. You can open a file in a new tab, or split the viewing panel and open it to the side to view it alongside another without highlighting differences. You can also rename it, delete it, download it, copy it, copy its path, or view its timeline - a sparse history of edits to that file. Selecting "Preview" on a markdown file will allow you to view it as a rich text version, rather than in the editor version. 


## Settings
You can change settings for VS Code and its extensions either by clicking on the cog next to an extension name, or by using `CTRL+SHIFT+P` (macOS: `COMMAND+SHIFT+P`) to open the command palette at the top of the page. This gives you access to many useful commands, such as those needed to connect to a remote host. 

## Extensions 
VS Code is similar to a web browser in that it lets you install extensions. These range from themes to coding languages to support for Jupyter notebooks. 

Installing extensions can be done by clicking on the left hand button showing three squares in a window shape with a fourth offset to the side. In the side panel you can see popular extensions and search for those you need. Click on one you want to install, and an information page will open with an install button. Some will require a restart to take effect. 

## Remote computing
Two of the most useful extensions are **Remote-SSH** and **Remote Explorer**.
Remote-SSH allows you to connect to a remote computer using SSH, and use VS code as normal, using the integrated viewers and text editors. 
Remote-Explorer allows you to open directories in a remote computer and browse through them in a side panel using a mouse. It can make navigating files very fast and is well worth using.

### To use Remote-SSH to connect to a remote machine:
1. Install the extension
2. Once you have installed Remote-SSH, restart VS Code. 
3. Use `CTRL+SHIFT+P` to open the *command palette*  (`COMMAND+SHIFT+P` on a mac)
4. Search for `Remote-ssh: Open SSH configuration file`
5. In the ssh configuration file, add a section like this 
```
Host <host>
  HostName <host_location>
  User <username>
```
For example, if you connect to the Isca HPC with this command: `ssh abc123@login.isca.ex.ac.uk`, your file should contain:
```
Host Isca
  HostName login.isca.ex.ac.uk
  User abc123
```
This can be extended to specify a port if needed, and to add a proxy. 
You can also specify an IP address as the hostname to connect to a specific machine.

You're now set up to connect to the remote machine. 

6. Use `CTRL+SHIFT+P` to open the *command palette* again (`COMMAND+SHIFT+P` on a mac). 
7. The option `Remote-SSH: Connect to host" will let you select the host you just added. It will then prompt you to enter your password (and possibly to tell it whether the host is a linux, mac or windows machine). 
8. An installation step runs and it attempts to connect. When this finishes, you'll be able to open a terminal and work on the remote machine!

### A limitation with ISCA when using the VPN off campus
Unfortunately, firewalls and security make it hard to connect to Isca using Remote-ssh when using the VPN. 
If you find yourself stuck on the "Install" phase of connecting, there is a fix for this.

1. Close any VS Code window that is trying to connect to Isca. 
2. Open a new terminal (it can be the regular terminal in VS Code, or any other terminal), and ssh into Isca. 
3. When you're connected and in your home directory on Isca, you need to find your .vscode-server directory. This is hidden in your home directory; you can see it when you type `ls -a` to show hidden files. 
4. Go to the .vscode-server directory, using `cd ~/.vscode-server/`
5. Make sure you're in that directory. Delete the contents with `rm -r *` 
6. Go back to your home directory and delete the .vscode-server directory. `cd ~ ; rmdir .vscode-server/` 

You should then be able to connect via the VPN, but may need to repeat the process if you reconnect. 


### Using the Remote Explorer
This is similar to the normal explorer. Install the plugin and connect to the remote machine. Then open the explorer. It should give you the option of opening the remote directories. Select the highest one you need and then open it. This will open a new window and ask you to re-enter any passwords to connect to the remote machine. You'll now be able to navigate via the explorer. 


