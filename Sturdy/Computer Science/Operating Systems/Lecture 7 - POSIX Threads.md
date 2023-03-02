## Threads on Linux
- Does not distinguish between threads and processes 
- The clone() system call is used to determine what will be shared with the child (thread) task 
	- Flags are used to do so (e.g., CLONE_FS, ls CLONE_VM) 
	- man clone for more info

## Pthreads

Pthreads ([[POSIX]] threads) is a standard or API for doing threading 
- Specification, not implementation 
- Can be implemented using User threading or Kernel threading 
- Users can be oblivious(forget) of the underlying implementation
- Allows a program to control multiple different flows of work that overlap in time

- Linux Native POSIX Thread Library (LNPT) 
	- Since kernel v2.6 
- Library: Implemented in the form of a library (that you have to link to your program) 
	- ```#include <pthread.h>``` 
- Rely on kernel to create / schedule threads 
→ Comparison with Windows Thread API 
	- Not POSIX compliant but Pthreads ports exist

```
#include <stdio.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <pthread.h>

int main(){
  int pthread_create(
    pthread_t * thread,
    const pthread_attr_t * attr,
    void * (*start_routine)(void *),
    void * arg
  );
  
  void pthread_exit(void * value_ptr);
  
  int pthread_join(pthread_t thread, void ** value_ptr);
  
  int pthread_cancel(pthread_t thread);
  
  int pthread_detach(void);
}
```

## pthread_create()
![[Pasted image 20230228083454.png]]

## pthread_join()
The main process waits for a thread to terminate 
```
int pthread_join(pthread_t thread, void **retval);
```

## pthread_self()

Returns the thread id (this is not the PID!)

## pthread_yield()
- Gives up using CPU resources so other threads can make use of the CPU
- Implemented using sched_yield() 
	- Requires ``` #include <sched.h>```

