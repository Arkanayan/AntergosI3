# Antergos + i3 windows manager

# STILL TESTING BETA PHASE

This is my configuration for I3 improved tiling to be used on any Antergos linux distribution.

In the installation folder is all the data, explanations and scripts for you to have a great working environment but not directly a desktop environment.

I do not work with a display manager. Xorg and I3 provide all the display you will ever need.

I suggest you read up to better understand what a tiling window manager is.

It is really great once you have mastered the most important shortcuts.

https://i3wm.org/

# What can you achieve?

Yltra Flat Orange on Antergos I3
Icons can be found at github
https://github.com/erikdubois/Yltra-Flat

![Screenshots](http://i.imgur.com/xtILBj5.jpg)



![Screenshots](http://i.imgur.com/MRH6EiB.jpg)




![Screenshots](http://i.imgur.com/2bMwqsl.jpg)




![Screenshots](http://i.imgur.com/UUw3NUM.jpg)



#What can you do if the script does not execute?

Since I sometimes forget to make the script executable, I include here what you can do to solve that.

A script can only run when it is marked as an executable.

    ls -al 

Above code will reveal if a script has an "x". X meaning executable.
Google "chmod" and "execute" and you will find more info.

For now if this happens, you should apply this code in the terminal and add the file name.

    chmod +x typeyourfilename

Then you can execute it by typing

    ./typeyourfilename




# A N T E R G O S    L I N U X 
--------------------------------

I started using Antergoslinux as a learning experience. I have tried installing all kinds of desktop environments (DE) and formatted many times my ssd's to start from scratch. After a while it was more practical to have a script of some kind to record the knowledge and to automate the things I had already learned. They became repetitive in nature.

The goal is to be quickly up and running after a clean install. 

That's why I have written a script to do just that. 

#1. Installation of the base system

I started following the guide of 

https://wiki.Antergoslinux.org/index.php/Beginners%27_guide

After this base installation you will end up in a black screen (terminal) with no graphical environment what so ever. Then it is up to the user to choose a Desktop Environment.

Good options are

	- xfce
	- cinnamon
	- gnome
	- kde
	- openbox

But we will install i3 instead.

Choose for <b>Base installation</b> when installing Antergos.

#2. First boot

Set your keyboard right.

Depending on where you live, you might want to change your keyboard. The default keyboard is set to US. You will be typing in qwerty or en_US.UTF-8.

If you want to know what name of keyboard to use you can type : 
	
	localectl list-keymaps

Pageup and Pagedown moves you around.
q to quit the listing
Or you can pipe the same command to the command “less”

	localectl list-keymaps | less

Look at the first two letters that designate your country/keyboard or system.
E.g. us for America, wang for Wang computer and mac for Mac Osx.

TIP : you do not have to type all the words/letter, use the TAB and see if it completes automatically. 
Keep typing and trying TAB until you get what you want.

Our first command has been send. 

TIP : Remember that to stop processes or quit something, Linux usually takes “q”, CTRL + C, CTRL + X  or CTRL + W. 

I rarely know which one works, I go over all of them till it ends. 

If you accidentally get into “vi” which is a text editor, you can quit that by pressing “:q”.

Living in Belgium we type with an <b>azerty keyboard</b>. If I could not type blind, I would have switched to qwerty by now.

Living in Belgium I will type

	sudo loadkeys be-latin1

Now I can type in azerty format.

If you reboot right now, the system will have forgotten your keyboard and will revert to qwerty.

Therefor I will do the following steps to keep my azerty keyboard

	sudo nano /etc/locale.conf

Change this to

	KEYMAP=be-latin1

Save and exit with CTRL + X.


#3. Get all the files

The idea is to download (if you have internet connection) the i3 github files. In my case I had internet connection straight after installing the base system and git was installed as well:

Git is NOT installed then
	
	sudo pacman -S git

Git is already installed then

	git clone https://github.com/erikdubois/antergosi3



#4. Move all files to correct directory

I3 works from a hidden directory namely .i3
Let us move all downloaded files there.


This downloaded folder should be movied to a hidden folder in your home directory with the name  ~/.i3

    mv antergosi3/ ~/.i3

Know that there are also hidden files as well.

	cd .i3   

    ls -al       

#5. If problems with servers

Jan 2015 
Solution

	sudo pacman -S reflector
	sudo reflector --verbose -l 200 -p http --sort rate --save /etc/pacman.d/mirrorlist
	sudo pacman -Syyu

This will create a list with the top 200 fastest servers in your neighbourhood.



#6. Installation folder

I run an installation script to quickly  get all my software after <b>the base installation of Antergos</b>. For me this was quite a learning process, since I was a Redhat, Ubuntu, Linux Mint kind of guy over the last two decades. 


Then you can start running the below mentioned script to be found in the folder installation.

I decided to split the logical entities in seperate files. Better to debug and better for users to understand.

The scripts have been numbered from 1 to 6. Follow the orderering to install all programs.


  
    cd installation
    ls -al

    
    ./1_install_i3_core_vx.sh


If the choice comes up between choosing xf86-input-evdev and xf86-input-libinput, choose the first one.

This will install the actual i3 windows manager and xorg to render it. We will also make sure yaourt is installed. Yaourt is used to install <b>packer</b>>. Packer will serve as the aur helper from there on.

Beware when you say "Y" or "N" to the questions.



    ./2_install_i3_Antergos_repo _v1

This will install all programs coming from the "normal" Antergos repositories with the use of pacman.




    ./3_install_i3_aur_repo _vx.sh

This will install all programs coming from the AUR repositories.

If you see a program, you do not want. Just press ENTER and no number and it will be skipped.
In the script you will see a text to know which one you need to choose.

    For example

    echo "################################################################"
    echo "sane"
    echo "################################################################"

When that is done you run

	./4_keep_all_here_vx.sh

The last script is my idea to have all my data in one folder. So I make some symbolic links to them. I did notice that this is not so easy with the gtk files. The scripts makes backup files.

The zsh script is an alternative to bash more colourfull (>100 themes) and more plugins then you ever need.

    ./5_zsh_vx.sh

The smb script is to install samba or the way to share folders and files between computers if you need it.

    ./6_smb_vx.sh




<h2>Give it a go because <b> I 3 improved tiling </b> deserves to be more known.</h2>





# Reboot  N  O  W




# First use and tips

Follow some movies on youtube about i3 wm. That's the fastest way to learn.

Remember some important keyboard shortcuts

win + d = dmenu

shift + win + d = j4dmenu

ctrl + alt + a = xfce-appfinder

win + shift + e = exit i3

win + shift + r = reload config file

win + shift + q = closes any window

win + pause/break = let you suspend,hibernate, reboot and quit

All shortcuts are kept in one file : "config"
You do well to read this file.

lxappearance is the first program I use to change themes, fonts, icons.




# C O N C L U S I O N


I know that there are applications that seem 'out-of-place' in i3 but I like my working environment eye-candy. I admire for example the wallpapers creative people share with us. Through transparent terminals I will see them.

My background has been a variety of distro's. It is only natural I use a variety of programs from these distro's.

As for I3 you will need to be patient. I remember giving up a few times and somehow it challenged me to keep trying.

I am happy I persisted. 

<b>I3 is efficient.</b>

Advantages

    low memory consumption
    does not have many dependencies hence stabler
    keyboard driven
    software will be tiled automatically into two, three, four regions
    terminal is a WIN+ENTER away
    every program can get its own workspace
    switching between workspaces is easy and very practical
    have a backup environment to work if somehow your "other" desktop environment gets broken

 

Disadvantages

    takes time getting used to
    shortcuts to be remembered
    specific software to do things
    some terminal knowledge required


And remember if you start from this github, your learning curve will be much steeper and you will have the system up and running much faster.

Then you take it apart and write your own code.

------------------------------------
#But that is the fun in Linux.

You can do whatever <b>Y O U</b> want.

Share the knowledge.
------------------------------------