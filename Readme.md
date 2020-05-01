# Computer Security CW3

<b>Course name:</b> Computer Security
<br><b>Objective:</b> Gain practical experience with attacks that exploit software vulnerabilities, in particular buffer overflows.
<br><b>Focus:</b> Bash, C, Python 
<br><b>Mark:</b> 100%

## Tasks
1. This is just for warming up. This program is found in /task1/vuln, and waits for a password (stored in /task1/password.txt), and if the correct password is entered by the user, it prints the secret. The program has a buffer overflow vulnerability, making it possible – without knowing the password – to allow it to log in. Important: the real password will be changed for marking! The pidgeon and rooster various will not.
2. This program takes the user’s name as a command line argument, copies it to a buffer, and then welcomes the user. This program is vulnerable to a buffer overflow attack. Your attack script should call this program with a carefully crafted argument, such that it overwrites the return address on the stack, and returns to the read_secret function, instead of back to main. Stack canaries are not enabled in this task.
3. For this program, there is no helpful function for extracting informa- tion, meaning you must inject your own shellcode, jump to this on-stack instead of a pre-existing function. Furthermore, from this task on, the program is com- piled with GCC’s stack protection enabled, which inserts stack canaries after the return address on stack. Your attack script will input a malicious argument, such that the program loads and jumps into your shellcode, while avoiding these canaries. The template provided already contains some boilerplate code to then read the secret from this shell.
4. This program functions similarly to the previous script, however ex- ecution of code on the stack has been disabled! Instead, you should perform a return-to-libc attack. In particular, you should overwrite the stack such that execution returns into the libc function system(), and make this function be- lieve it received "/bin/sh" as an argument. For this purpose, you’ll need to find the locations of these in memory, and analyse how calls to system() would ordinarily function. Your program should use this return technique to spawn a shell – in this case the program itself forces that the real uid is set, ensuring the shell will be as the task4 user.
5. This task does not have a binary to directly exploit, but instead runs a small TCP server on the local port 4040. This program accepts requests the read sections of a secret file, but denies requests to some parts. It is however vulnerable to an attack allowing you to read this part too! Your attack script should connect to the server using netcat, and submit a malicious request, ex- tracting the secret string.

## Commands
Run graphical virtual machine
<br>```$    /afs/inf.ed.ac.uk/group/teaching/compsec/cw3/lestrade```

Run terminal-only virtual machine
<br>```$    /afs/inf.ed.ac.uk/group/teaching/compsec/cw3/watson```

Run the automarker
<br>```$    /afs/inf.ed.ac.uk/group/teaching/compsec/cw3/sherlock```

Submit the coursework
<br>```$    submit cs cw3 ~/cshome-cw3.qcow2```
