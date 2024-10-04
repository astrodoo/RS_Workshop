Basic Linux 
===========


Navigation
----------

.. option:: pwd [option]

   print current working directory's path

   :option: * -L (--logical)
            * -P (--physical)


.. option:: ls [option] [/directory/folder/path]

   list files and directories in your system

   :option: * -a
            * -h
            * -F: type of objects  /: directory, @: link, \*: executable
            * -l

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


File/Directory Manipulation
---------------------------

.. option:: mkdir [directory name]

   create one or multiple directories

.. option:: cp [option] [source object] [target path or filename]

   copy files or directories to another file names or target ath

   :option: * -R: all sub-directory
            * -f: force to copy
            * -v: verbose






Archive\&Unpack targets
-----------------------


File Transfer
-------------





..  backup  
    .. code-block:: bash
       :linenos:

