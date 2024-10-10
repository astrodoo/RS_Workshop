Text Editor on Linux
====================

Nano
____

Nano is a straightforward and user-friendly text editor, making it a great choice for beginners.

* Opening a File

  .. code-block:: bash

     nano filename.txt
  ..

* Basic Commands

============= ==========================================
Command       Description           
============= ==========================================
Type          Edit text directly 
`Ctrl + O`    Save changes                        
`Ctrl + X`    Exit the editor (prompt to save if needed)
`Ctrl + K`    Cut the current line                     
`Ctrl + U`    Paste the cut line                      
`Ctrl + W`    Search for text                        
Arrow keys    Navigate through the text             
============= ==========================================

----

Vim/Vi
______

Vim (Vi IMproved) is a powerful text editor that is widely used in the Linux environment. It operates in different modes, primarily **Normal**, **Insert**, and **Visual** modes.

* Opening a File

  .. code-block:: bash

     vi filename.txt
  ..

* Basic Commands in **Normal Mode**

=============  ====================================================
Command        Description                            
=============  ====================================================
i              Switch to Insert mode                         
a              Switch to Insert mode (append)               
v              Switch to Visual mode
Esc            Return to Normal mode                       
:w             Save changes                                
:wq            Save and exit                               
:q!            Exit without saving                             
h, j, k, l     Navigate left, down, up, and right, respectively
dd             Delete the current line                         
u              Undo the last action                            
=============  ====================================================

* Still Basic Commands in **Normal Mode** but good to know further

=============  ======================================================
Command        Description                            
=============  ======================================================
$              Move to the end of the line
0              Move to the start of the line
H              Move to top of the page 
M              Move to middle of the page
L              Move to bottom of the page
gg             Move to the first line of the file
G              Move to the end of the file
[n]G           Move to nth line of the file
w              Jump to the next word
b              Jump back to the previous word
/<keyword>     Search Keyword ("`n`" will prompt you to the next one)
=============  ======================================================
