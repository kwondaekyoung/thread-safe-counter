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
+ 
First, for example with toilet the mutex has only one toilet space(ex..door) but semaphore has multiple toilet space. additionally we can assume that toilet is the critical section.
and second as i mentioned earlier (what is semaphore and mutex), semaphore synchronize multiple but mutex is not.
third mutext has a concept that 'owner' it means only the owner can lock or unlock the mutex on the other hand semaphore doesn't have a concept 'owner', it mean with owner-less semaphore can lock or unlock.
------------

## compare processing time
+ use time command(real time) or print time that in code(main function)
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
![mutex](https://user-images.githubusercontent.com/80217642/121780058-913d7d80-cbd9-11eb-990c-d1d1eac2e068.png)
------------
![semaphore](https://user-images.githubusercontent.com/80217642/121780084-b500c380-cbd9-11eb-9d52-7c25f19e6e59.png)

------------
# struct bianry-semaphore with semaphore.h(in POSIX)
+ semaphore can be mutex that named bianry-semaphore that use state only 0,1
 (mutex=binary semaphore)
+ use <semaphore.h> in POSIX
![Screenshot from 2021-06-12 22-44-49](https://user-images.githubusercontent.com/80217642/121780121-e5486200-cbd9-11eb-90b3-7dc06d164d74.png)
------------
 
#conclusion
+ 


------------


conclusion: 

근데 동기화여부에 따라 둘의 선택이 나뉜다. 동기화라는 것은 kernel mode를 얘기하는것이다
뮤텍스는 proccess 범위 내에 속해 있기에 동기화에 부적절 즉 kernel mode에 진입할 수 없다.
바이너리 세마포어는 file 형식으로 저장되어 system call을 요구하기때문에 kernel의 진입이 필요하다.





