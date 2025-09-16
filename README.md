# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }

```
##OUTPUT
<img width="490" height="158" alt="image" src="https://github.com/user-attachments/assets/faf27285-4040-4ff3-b3f7-6c5079f5c7b3" />








```
## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>

int main() {
    int pid;
    pid = fork();

    if (pid == 0) {
        printf("I am child, my pid is: %d\n", getpid());
        printf("My parent pid is: %d\n", getppid());
        exit(0);
    } else {
        printf("I am parent, my pid is: %d\n", getpid());
        sleep(100);
        exit(0);
    }
}
```
##OUTPUT
<img width="201" height="151" alt="image" src="https://github.com/user-attachments/assets/a6ef6e7d-f65d-4d2f-80f8-5e244642c057" />

3.
```
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```
 OUTPUT:
 
 <img width="434" height="713" alt="image" src="https://github.com/user-attachments/assets/8e73e065-ff5d-49c7-8d69-fd857517db55" />
 <img width="424" height="800" alt="image" src="https://github.com/user-attachments/assets/997433ae-81c0-4e4c-a48a-5113275e6b4e" />
 <img width="427" height="800" alt="image" src="https://github.com/user-attachments/assets/3cf3a59f-2b1a-4029-8525-184ce7bbabb4" />
 <img width="431" height="800" alt="image" src="https://github.com/user-attachments/assets/06bdf3ab-0bc2-4c9b-817f-d7abe1b073ec" />




        
        















# RESULT:
The programs are executed successfully.
