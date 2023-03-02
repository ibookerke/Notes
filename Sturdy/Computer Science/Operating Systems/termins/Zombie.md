If no parent is waiting (did not invoke wait()), the child process is a **zombie**

An [[Orphan]] process is formed when it's parent dies while the process continues to execute, while ==zombie== process is a process which has terminated but it's entry/parent is there in the system 

To summarize, we can say that **a zombie process is a terminated or completed process that remains in the process table**. It will be there until its parent process clears it off. And it does this by calling wait() call on its child and reading the exit value and other accounting information.
