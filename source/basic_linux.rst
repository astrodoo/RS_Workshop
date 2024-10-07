Basic Linux Commands 
====================

In this page, the essential Linux commands are listed. You can exercise all commands below on the Argon cluster. 


First helpers
-------------

.. option:: man [option] [section number] [command name]

   | display a comprehensive guide of commands. 
   | If no section number, it will print out the entire manual of the requested command. 

.. option:: history [option]

   check previous run utilities

   .. code-block:: bash

      dooyoon@argon-itf-login-3 ~> history
      1  cd
      2  ls
   ..


Navigation
----------

.. option:: pwd [option]

   print current working directory's path

   :option: * -L (--logical)
            * -P (--physical)


.. option:: ls [option] [/directory/folder/path]

   list files and directories in your system

   :option: * -a: show hidden content
            * -R: list items inside subfolders
            * -h: print file sizes in human-readable format
            * -F: type of objects  /: directory, @: link, \*: executable
            * -l: display detailed information 

  .. code-block:: bash

     dooyoon@argon-itf-login-4 ~> ls -altrh
     total 4.5M
     -rw-r--r--  1 dooyoon 5.4K Dec  7  2023 .vimrc
     drwxr-xr-x  2 dooyoon    5 Dec  7  2023 .vim-file
     lrwxrwxrwx  1 dooyoon   26 Feb 19  2024 nfsscratch -> /nfsscratch/Users/dooyoon/
     drwx------  3 dooyoon    3 Feb 28  2024 .dbus
     -rw-------  1 dooyoon   16 Feb 28  2024 .esd_auth
     drwxr-xr-x  2 dooyoon    2 Feb 28  2024 Desktop
     drwxr-xr-x  2 dooyoon    2 Feb 28  2024 Downloads
     drwxr-xr-x  2 dooyoon    2 Feb 28  2024 Templates


.. option:: cd [/directory/folder/path]

   move to the destination folder

   * **Absolute path**: start w/ the root directory and provide the full path to the file or directory
   * **Relative path**: a path to a file or directory that is relative to the current directory  

----

File/Directory Manipulation
---------------------------

.. option:: mkdir [directory name]

   create one or multiple directories

.. option:: cp [option] [source object] [target path or file name]

   copy files or directories to another file names or target ath

   :option: * -R: all sub-directory
            * -f: force to copy
            * -v: verbose

.. option:: mv [source object] [target path or file name]

   move files or directories to a new location or rename them


.. option:: rm [option] [file names or directory names]
   
   remove files or directories

   :option: * -i: prompt a confirmation before deletion
            * -f: allow file removal without confirmation
            * -r: delete files and directories recursively

.. warning::

   In most cases, deleted files and directories cannot be recovered. 


.. option:: touch [option] [file name]

   create a new empty file in a specific directory


.. option:: cat [file name]

   print the content of a text file

.. note::

   You can also use ``cat`` with the operator to combine multiple files into a new file. 
   
   .. code-block:: bash

      dooyoon@argon-itf-login-4 ~> cat file1.txt file2.txt > target_file.txt
   ..

.. option:: head [option] [file name]

   print the first few entries of a file 

   :option: * -n: number of lines

.. option:: tail [option] [file name]

   print the last few entries of a file

   :option: * -n: number of lines
            * **-f: output appended the data (i.e., display the lines in real time)**


.. option:: grep [option] keyword [file name]

   | search specific lines from a file using keyword 
   | -> Useful for filtering large data like logs


.. option:: ln [option] [source] [destination]

   create links between files or directories

   * hard link:
        * only files on a same partition
        * link to inode
   * symbolic link:
        * option: ``-s``
        * point to files or directories
        * considered as "shortcuts"

   .. code-block:: bash

      dooyoon@argon-itf-login-4 links_hard_symbolic> ls -il *
      285698 -rw-r--r-- 2 dooyoon 4 Sep  3 15:33 source1
      285698 -rw-r--r-- 2 dooyoon 4 Sep  3 15:33 source1-hard
      285699 -rw-r--r-- 1 dooyoon 4 Sep  3 15:22 source2
      285701 lrwxrwxrwx 1 dooyoon 7 Sep  3 15:30 source2-soft -> source2


.. option:: which [command]

   search for executable **First** commands in the PATH environment

.. option:: whereis [option] [command]

   display the path of the binary source, and manual page files in the PATH or MANPATH environment

.. option:: locate [option] [command]

   search all files that include pattern in the pre-existed database

.. option:: find [dir] [option] [expression] 

   search files and directories in any designated directory

.. option:: chmod [option] [permission] [file or directory]

   change permission of files or directories

   * u: user / g: group / o: other / a: all
   * r: read / w: write / x: execute

   .. code-block:: bash

      dooyoon@argon-itf-login-4 Executable> ls -l
      -rwxr--r-- 1 dooyoon 38 Sep  5 14:08 hello.sh

      dooyoon@argon-itf-login-4 Executable> chmod ugo+x hello.sh
      dooyoon@argon-itf-login-4 Executable> ls -l
      -rwxr-xr-x 1 dooyoon 38 Sep  5 14:08 hello.sh
   ..

   * Octal Number: r=4 / w=2 / x=1

   .. code-block:: bash

      dooyoon@argon-itf-login-4 Executable> chmod 755 hello.sh
      dooyoon@argon-itf-login-4 Executable> ls -l
      -rwxr-xr-x 1 dooyoon 38 Sep  5 14:08 hello.sh
   ..

.. option:: df [option] [file system]

   check your system's disk usage

   :option: * -h: print file sizes in human-readable format

   .. code-block:: bash

      dooyoon@argon-itf-login-3 ~> df -h $HOME
      Filesystem                          Size  Used Avail Use% Mounted on
      172.29.4.38:/dpool01/Homes/dooyoon  1.0T   20G 1005G   2% /old_Users/dooyoon
   ..

.. option:: du [option] [directory]

   check the size of a directory and its content

   :option: * -h: print file sizes in human-readable format
            * -d, --max-depth=N: print the total for a directory only if it is N or fewer levels below.  


----


Archive\&Unpack targets
-----------------------

.. option:: tar [option] [archive file] [target objects]

   bundle multiple files or directories into an archive

   :option: * c or x: create or extract
            * v     : verbose
            * f     : specify the archive file
            * z or j: compression (file extension -> .tar.gz or .tar.bz2) 
                      without compression, the extension will be .tar

.. option:: zip [option] [archive file] [target objects]

   bundle and compress multiple files or directories using zip

.. option:: unzip [option] [archive file]

   extract the zip archived file

----


File Transfer
-------------

.. option:: wget [option] [URL]

   download files from the internet via HTTP, HTTPS, or FTP protocols

.. option:: curl [option] [URL]

   transfer data from or to a server by specifying its URL

   :option: * -O/-o: download files from the specific link

.. option:: scp [option] [source] [address]:[destination folder]

   securely copy files and directories between systems over a network

.. option:: rsync [option] [source] [address]:[destination folder]

   syncs files or directories between two destinations to ensure they have the same content

   :option: * -r: recurse into sub-directories
            * -a: archive mode, keeps all file permissions, symbolic links,file ownership, etc
            * **-u: skip files that are newer on the receiver**





..  backup  
    .. code-block:: bash
       :linenos:

