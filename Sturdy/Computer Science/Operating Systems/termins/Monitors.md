- A high level abstraction that provides a convenient and effective mechanism for process synchronization
- A monitor-type presents a set of programmer-defined operations that provide mutual exclusion within the monitor
- The monitor-type also contains the declaration of variables whose values define the state of an instance of that type, along with the bodies of the procedures or functions that operate on those variables

![[Pasted image 20230301211324.png]]


Condition Construct: condition x, y;

The only operations that can be invoked on a condition variable are wait( ) and signal ( ).

The operation x.wait( ); means that the process invoking this operation is suspended until another process invokes x.signal( );

The operation x.signal( ); resumes exactly one suspended process.

x/y represensts philosofers like state[i] = x 