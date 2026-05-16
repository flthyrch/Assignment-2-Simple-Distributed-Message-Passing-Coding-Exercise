## Assignment 2: Simple Distributed Message-Passing Coding Exercise
***
### Code Output and Revisions
***
`Progress #1` **Attempting to run MPI**
<p> Initially, I attempted to execute the starter MPI code using Jupyter Notebook. However, the program did not run as expected. Through further observation and research, I learned that MPI programs cannot properly execute directly within notebook cells because MPI requires multiple processes to be launched externally. As a result, the code needed to be placed in a separate Python (.py) file for proper execution. </p>
<img width="538" height="283" alt="image" src="https://github.com/user-attachments/assets/75210634-79fc-46ec-823b-a8388d0b19f8" />
<br>
<br>

`Progress #2` **Installing requirements and running MPI** 
<p> After identifying the issue, I installed the necessary MPI requirements, including Microsoft MPI from the official Microsoft website. I also used the pip command to install the required Python packages. Instead of directly running the code inside Jupyter Notebook, I used Jupyter as an environment to execute terminal commands connected to the .py file through the !mpiexec command.</p>
<img width="506" height="147" alt="image" src="https://github.com/user-attachments/assets/d875f331-7414-4285-87c6-f51b44d44494" />
<br>
<br>

`Progress #3` **Code Changes** 
<p>The original if statement only sent a simple greeting message from the worker processes to the master process. In the revised version, each worker process now performs an actual computation task before sending data back to the master. Specifically, each process calculates the sum of its assigned data chunk and transmits the computed result to the master process.

This revision improved the functionality of the program by demonstrating actual distributed computation instead of simple message passing. </p>
<img width="705" height="318" alt="image" src="https://github.com/user-attachments/assets/07c1a59b-d202-4061-b847-129b43523fe2" />
<br>
<br>

<p> The revised else statement enables each process to independently perform its assigned computation task. Each worker process generates a unique set of data based on its process rank, computes the sum of the values, and sends the result back to the master process.

Additionally, the output messages were reorganized to improve readability and make the communication between processes easier to understand.</p>
<img width="621" height="392" alt="image" src="https://github.com/user-attachments/assets/eb72addc-503b-4b83-b1e4-c0bb8fe6c17f" />
<br>
<br>

`Progress #4` **Final Output** 
<p>The following image presents the final output of the revised MPI program after implementing all modifications and successfully executing the distributed computation.</p>

<img width="524" height="339" alt="image" src="https://github.com/user-attachments/assets/28e49c76-ddb1-4872-baad-1b864049cbb5" />

---
### Guide Questions (Discussion and Reflection)
***
1. Why is message passing required in distributed systems?
- Message passing is essential in distributed systems because processes operate independently and do not share the same memory space. Since each process has its own local memory, communication mechanisms are necessary for exchanging information and coordinating tasks. Through message passing, processes can send and receive data, share computation results, and synchronize operations. Without message passing, processes in a distributed system would not be able to effectively cooperate with one another.

2. What happens if one process fails?
- If one process fails during execution, the remaining processes may wait indefinitely for messages or responses that will never arrive. As a result, the entire program may freeze, crash, or terminate unexpectedly. In basic MPI implementations, there is typically no automatic recovery mechanism, meaning the failure of a single process can cause the whole distributed application to stop running.
  
3. How does this model differ from shared-memory programming?
- Message-passing programming differs from shared-memory programming because processes communicate by sending and receiving messages rather than directly sharing data. In message-passing systems, each process has its own separate memory space, allowing processes to operate independently.

On the other hand, shared-memory programming allows multiple processes or threads to access the same memory space directly. This can improve performance since data sharing is faster, but it also requires synchronization methods, such as locks or semaphores, to avoid conflicts and data inconsistencies when multiple processes access shared resources simultaneously.
