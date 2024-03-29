cscope_macros
=============

http://www.vim.org/scripts/script.php?script_id=51

created by
Jason Duell

script type
utility

description
This script implements the recommended settings for vim's cscope interface, and also provides a set of key mappings I've found useful.  If you don't know what cscope is, go to http://cscope.sourceforge.net and check it out--it's more powerful than ctags, though it works with fewer languages (primarily C/C++/Java). 

The script takes care of automatically loading any cscope database you have in the current directory, or that you have set the $CSCOPE_DB environment variable to point to.  It also tells vim to allow cscope to share the CTRL-]  (goto tag) command with ctags.  Finally, it creates a set of keyboard maps (all starting with CTRL-spacebar) that perform the various types of cscope search, and which can either display cscope's results in a new vim window or in the current window. 

-------------------------------------------------- 
A quick vim/cscope tutorial: 
-------------------------------------------------- 

0) Get and install cscope if you don't have it already on your machine. 

1) Install this plugin (see instructions below). 

2) Go into a directory with some C code in it, and enter 'cscope -r'.  Check out the native cscope interface program (which will call vim to edit files if you set your EDITOR variable to 'vim').  The native cscope interface is very nice, but has the problem that you need to exit vim each time you want to do a new search.   Hit CTRL-D to exit cscope. 

3) Start up vim.  If you want, you can start it with a C symbol (ex: 'vim -t  main'), and you should hop right to the definition of that symbol in your code. 

4) Put the cursor over a C symbol that is used in several places in your program.  Type "CTRL-spacebar s" in quick succession, and you should see a menu showing you all the uses of the symbol in the program.  Select one of them and hit enter, and you'll jump to that use.  As with ctags, you can hit CTRL-T to jump back to your original location before the search (and you can nest searches and CTRL-T will unwind them one at a time). 

5) Try the same search, but this time via "CTRL-spacebar h s".  This time, the window will split in two horizontally, and the cscope search result will be put in the new window. [If you have trouble hitting the keys fast enough for this to work, go into the cscope_macro.vim script and change vim's timeout settings as described in the comments.]   

6) Try splitting the window vertically, by using 'v' instead of 'h' in the above search. 

7) Explore some of the other cscope search types, like 'find file' and 'find functions that call the function under the cursor'.  These are all described in the comments in cscope_macros.vim. 

8) Try using cscope with another language, like Java or C++.  The best way to do this is by doing "ls *.java > cscope.files"  (or "find -name '*.java' > cscope.files" if you've got a directory tree of Java files), then running cscope. 

9) Try setting the $CSCOPE_DB environment variable to point to a cscope database you create, so you won't need to lauch vim in the same directory as the database. This is particularly useful for projects where code is split into multiple subdirectories.  (Note: for this to work, you should build the database with absolute pathnames: cd to /, and do "find /my/fancy/project -name '*.c' -o -name '*.h' > /my/cscope.files", then run cscope in the same directory as the cscope.files file, then set and export the $CSCOPE_DB variable, pointing it to the cscope.out file that results). 

10) Use ":help cscope" within vim, and/or "man cscope" from your shell to answer any questions you have.  I.e., RTFM.

install details
vim 6:     Stick this file in your ~/.vim/plugin directory (or in a 
           'plugin' directory in some other directory that is in your 
           'runtimepath'. 

vim 5:     Stick this file somewhere and call 'source cscope_macros.vim' from 
           your ~/.vimrc file (or cut and paste cscope_macros.vim into your .vimrc). )

