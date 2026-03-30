# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:A thread is a smaller unit of execution, whereas a process is an independent program in execution with its own memory space and system resources. Processes are heavier and require more overhead to create and manage, whereas threads are lighter and switch between more quickly. Unlike processes, which need inter-process communication protocols, threads share the same memory area, enabling efficient communication. Because the simulation necessitates frequent context switching and coordination, threads were employed in this assignment because they are more effective. Furthermore, Java has built-in thread support, which facilitates the simulation of CPU scheduling behavior. **

[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:In Round-Robin scheduling, if a process does not finish within its assigned time quantum, it is preempted and moved to the end of the ready queue. This ensures fairness, allowing other processes to get CPU time before the same process runs again. The process will continue execution in the next cycle when it reaches the front of the queue again. This behavior is clearly shown in the program output where processes repeatedly yield the CPU and are re-added to the queue. As a result, all processes share CPU time equally until they complete execution

[Write your answer here. Describe the specific behavior - where does the process go? When does it run again? Give an example from your actual program output showing a process that was re-queued.]

Example from my output:▶ P1 executing quantum [4000ms] 
⚡ Quantum progress: [███████████████] 100%
⏸ P1 completed quantum 4000ms │ Overall progress: [████████████░░░░░░░░] 60%
   Remaining time: 2608ms
↻ P1 yields CPU for context switch

➕ P1 added to ready queue │ Burst time: 6608ms │ Priority: 3

Ready Queue:
[P3 → P4 → P5 → ... → P16 → P1]
```In this instance, process P1 was allotted a time quantum of 4000 ms, however it still had 2608 ms left to complete its execution. Consequently, it was positioned at the end of the ready queue and yielded the CPU (↻ yields CPU for context switch). We may observe that P1 appears at the end of the queue after being re-added: [... → P16 → P1]. This illustrates the fundamental concept of Round-Robin scheduling, in which incomplete tasks are repeatedly carried out until they are finished.
[Paste a relevant snippet from your program output here showing a process being re-queued]
```

**Explanation of example:**
[Explain what's happening in the output snippet you pasted]

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:In this simulation, each process (such as P1) is executed using a thread, and it transitions through different thread states during its lifecycle. These states include New, Runnable, Running, Waiting, and Terminated. The transitions depend on how the scheduler manages execution using time quantum and thread control methods like start() and join(). By analyzing the output and code behavior, we can trace how P1 moves through each state step by step.

New:
P1 is in the New state when it is first created using new Thread(process) before calling start(). At this point, the thread exists but has not started execution yet.
Runnable:
After calling currentThread.start(), P1 enters the Runnable state. It is now ready to run and waiting for the CPU scheduler to assign it CPU time.
Running:
P1 enters the Running state when it starts executing its quantum:
▶ P1 executing quantum [4000ms]

At this moment, the thread is actively using the CPU to perform its task.

Waiting:
P1 goes into the Waiting (or Timed Waiting) state during execution when Thread.sleep() is called to simulate processing time. Also, the main thread waits using join(), ensuring that the current process finishes its quantum before moving to the next one.
Terminated:
Finally, P1 enters the Terminated state when it finishes execution completely:
✓ P1 finished execution!

At this point, its remaining time becomes 0, and it is no longer scheduled again.**



---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1:Web Server Handling Client Requests

**Description**: Multiple client requests are handled concurrently by a web server, and each request is handled by a different thread.

**Why Round-Robin works well here**:By ensuring that every request receives an equal amount of CPU time, Round-Robin keeps one request from obstructing another. This guarantees greater performance and increases responsiveness for all users. When a lot of people are using the server at once, it is extremely helpful. 


### Example 2: Multimedia Applications (Video Player)

**Description**: A media player may simultaneously handle user input, buffer data, and decode video.


**Why Round-Robin works well here**: 
Each activity can run for a brief period of time thanks to round-robin scheduling, which guarantees responsive controls and fluid playback. It keeps other tasks from being delayed, which is crucial for real-time performance. A better user experience results from this.
---

## Summary

**Key concepts I understood through these questions:**
1. The distinction between processes and threads and how they affect performance.
2. How Round-Robin scheduling uses a ready queue to guarantee fairness.
3. a thread's life cycle and the way it changes states.

**Concepts I need to study more:**
1.sophisticated scheduling methods such as SJF and Priority Scheduling.
2.Race situations and deadlocks are examples of synchronization problems.


1.sophisticated scheduling methods such as SJF and Priority Scheduling.
2.
1. 
2. 
