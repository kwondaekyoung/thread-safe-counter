# thread-safe-counter
# OS version : Ubuntu Linux 18.04


------------

### What is semaphore and Mutex?
+ semaphore : semaphore synchronize multiple, that mean semaphore provide environment that multiple proccess or threads can be access in critical section. semaphore generally used with the resource that acquire a long time.
 And semaphore aims to coordinate or synchronize multiple processes competing for resources of the operating system.
simply speaking If another process is in use, it must wait a certain amount of time before retrying. it mean that in semaphore, process or thread get the key value, using the resource through the value accessing the critical section the other semaphore waits while changing value.
additionally if semaphore use state only 0,1 it called bianry semaphore.

+ mutex : orgianl mean is 'mutual exclusion'. compare with semaphore, mutex sychronize only for one, that mean only one proccess or thread can access in critical section.
mutex allow each process or thread accessing a critical section to execute independently so that the running times of the processes or threads does not overlap each other.(mutual exclusion)
using lock and unlock while access to critical section...

------------
#### critical section
+ in multiprogramming when multiple processes share data, critical section is part of code that access shared data in each process.
------------
### Why we use semaphore and Mutex?
+ Because there is a problem when processes exchange information or when specific data is shared through shared memory, locking is a way to restrict access to shared resource data so that only one process can access it at a time. and in lock we can see semaphore and mutex

------------

### commonality between semaphore and Mutex
+ concept base on protect the specific data, implement locking.

------------

### difference between semaphore and Mutex
+ First, for example with toilet the mutex has only one toilet space(ex..door) but semaphore has multiple toilet space. additionally we can assume that toilet is the critical section.
and second as i mentioned earlier (what is semaphore and mutex), semaphore synchronize multiple but mutex is not.
third mutext has a concept that 'owner' it means only the owner can lock or unlock the mutex on the other hand semaphore doesn't have a concept 'owner', it mean with owner-less semaphore can lock or unlock.
------------

## compare processing time
+ use time command(real: from start to end call    user: in user-mode   sys: in kernel-mode)

+ print time that in code(main function)
```
time ./a.out 1000000
```
------------
```
 #include<time.h>
 int(main){
 clock_t start=clock();

 code about process

 clock_t end=clock();
 printf("time: %lf\n",(double)(end-start)/CLOCKS_PER_SEC);
 return 0;
 }
```
------------
with mutex time check(tscounter.c)
![mutex](https://user-images.githubusercontent.com/80217642/121780058-913d7d80-cbd9-11eb-990c-d1d1eac2e068.png)
------------
with semaphore time check(semaphore.c)
![semaphore](https://user-images.githubusercontent.com/80217642/121780084-b500c380-cbd9-11eb-9d52-7c25f19e6e59.png)

------------
# implement bianry-semaphore with semaphore.h(in POSIX)
+ semaphore can be mutex that named bianry-semaphore that use state only 0,1
 (mutex=binary semaphore)
+ use <semaphore.h> in POSIX (binary-semaphore.c)
![Screenshot from 2021-06-12 22-44-49](https://user-images.githubusercontent.com/80217642/121780121-e5486200-cbd9-11eb-90b3-7dc06d164d74.png)
+ it take less time than semaphore compile with semaphore.c i think it's because it use only POSIX header and it spend time only system call nothing to spend bad time than other code.
------------
 
#conclusion
+ In many time with OS we have to use multi-programming or multi-processing (even though multi-threading) and at that time we always meet the problem of protecting the process or thread that access to shared resource. and we prevent that error with using lock. and as i mentioned earlier we can choose between semaphore and mutex each synchronize mutiple or one.
and with thread p1,p2 in two codes(semaphore.c and tscounter.c) we can see a time difference easily.
in my analysis i think the point is name of mutex, mutual exclusion. that mean other process can't contact when other access shared resource or specific data.
in detail, mutex has a key to unlock and each thread which in critical section give a key to next thread after unlock the mutex. one by one access critical section.
but in semaphore thread get the key 'value' in this code -1 1 for lock unlock, and in semaphore using the resource through the value accessing the critical section, the other semaphore waits while changing value.
so that it take more time than mutex because of waiting for changing value.
simply speaking while semaphore system waiting for previous thread access but mutex is not.
And we can also find a difference between mutex and semaphore code sys time with two picture. it said system(cpu) take more time in kernel-mode. in detail, that saids system have to wait previous thread in critical section. that mean while semaphore doing systemcall but they have to wait while value change, so they must waiting in kernel position. otherwise in mutex system, they don't have to wait in kernel-mode so sys time has a difference.
so in these reason mutex is faster than semaphore.
------------






