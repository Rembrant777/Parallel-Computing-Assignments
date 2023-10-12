# Notes of Probabilistic Concurrency Testing for Weak Memory 

## Terms 

### Interleaving Execution 
Interleaving Execution means in multi-thread or multi-progress programming, different thread or programs execute the commands in turn. 
Usually, under this pattern, every thread or process will be allocated a period of time of execution so that they can execute their program logics in turn. 

When one of the thread or process executes the job in the given time, it will switch to the next one. 

And one of the most classic scenario of interleaving execution is trying to programming upon the multi-cores, in which there are multi-cores to process different thread or process at the same time. And because of this, shared resources(like memory) will be occupied by different threads or progress. So it is necessary to design some synchronized strategy to coordinating the threads and process's invocations to avoid concurrency issues such as race conditions. 

### SC (Sequential Consistency)
In shared memory concurrency, threads communicate through shared memory acesses. 
And the behaviors of these programs are usually explained by thread interleavings, 
where the shared memory accesses in each thread execute in syntactic order, and threads interleave arbitrarily. 
This is formally known as sequential consistency(SC). 


### Weak Memory 
In java language,a variable X will be access by multiple threads, when one of the threads try to modify the value of X.
If the variable X is not decorated by a key word in Java Language -- `volatile` the modification will only maintain in the scope of that thread only.
This will result in value X's modification is not access to other reamined thread which will involes lots of dirty reads/write and finally result in an unexpected result.

The above explanation is very similary to the Weak Memory. Suppose there are interleaving execution(multi-threads/multi-process) shared a piece of memory that is the Weak Memory. Thread-a's modification can not immediatly affected or accessed by the reamined threads. This is the Weak Memory strategy. 

### C/C++ Concurrency 

There is a little different in C/C++'s Concurrency in C11. (Trying to understand the C/C++'s Memory strategy by refering to the Java's inner defined Atomic Variables like AtomicInteger ...).

### Probabilistic Concurrency Testing (PCT)

A randomized concurrency testing algorithm designed for SC(sequence-consistency) programs. 
It provides strong theoretical guarantees on the probability of detecting concurrency buts. 

Given bug depth d, PCT randomly generates a test execution that encodes a particular ordering of events with d scheduling constraints. 

### Native Random Concurrency Testing 
A native random concurrency testing algorithm chooses the next event to schedule from the set of all enabled events at each scheduling choice.

Such an algorithm detects the violation in the example with a probability of only 1/2^k where the k is the number of scheduling choices. 
To detect it, it must choose the event in the first thread among the 2 enabled events for all k scheduling choices in the execution. 

### Difference between PCT and Native Random Concurrency Testing 
PCT differs from native random testing by sampling an execution from the set of executions with d ordering constraints. 

It guarantees a lower bound on the probability of detecting a bug by a test execution with a probability of at least 1/(t*k^(d-1)) where the t is the 
number of threads, and the k is the numver of program events. And the d is the bug depth. 

### What's PCT algorithm relies on?
The PCT algorithm relies on the ordering constraints and the interleaving semantics of sequential consistency. 

More specially, it relies on the notion of bug depth that is defined as the minimum number of scheduling constraints that are sufficient to find the bug. 




## Question(s) of the paper content 
### What's this paper mainly talk about? 


### What question/issues that this paper proposed and how to verify that via what's methodology? 

### Can we use implement the same idea and adopt it upon an existing distributed system framework ? like Spark ? 

### PCT What's PCT(The Probabilistic Concurrency Testing) ? 

### How can PCT described or explained in algorithm psedo code ? 

### Is PCT already adopt in other areas already ? What are they? That's the metrics to verify its good or bad ? 

### What's Weak Memory ? Is it refer to the hardware or the a methodology or industry standard ? 

#### What's PRTWM refers to? 

