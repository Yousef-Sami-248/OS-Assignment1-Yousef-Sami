# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:**

[ifference:

Process: Think of it as a heavy, independent program that has its own private memory. Because it is "isolated," it takes more time to start and is harder to share data with other programs.

Thread: It is a "lightweight" part of a process. Since many threads live inside the same process and share the same memory, they are much faster and can talk to each other easily

Why we used Threads in this assignment:1- Efficiency 2- Shared Memory 3- Fast Context Switching

]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:**

[

Round Robin Scheduling, if a process does not finish its work within a specific time called "Time Quantum," then it (must stop)

----------------
1- The process is interrupted: The CPU interrupts the current process immediately since it has exceeded its time

2- Going back to the queue: The process goes back from the CPU to the end of the Ready Queue, waiting for its turn

3- Switching to the next one: The scheduler switches to the next process in line

4- Waiting for a new turn: The process stays in the queue until it reaches the front of the queue again to continue working from where it left off.]

Example from my output:
```
[
? P1 executing quantum [3000ms] 

  ? Quantum progress: [???????????????] 20%
  ? Quantum progress: [???????????????] 40%
  ? Quantum progress: [???????????????] 60%
  ? Quantum progress: [???????????????] 80%
  ? Quantum progress: [???????????????] 100%
  ? P1 completed quantum 3000ms ? Overall progress: [????????????????????] 49%
     Remaining time: 3074ms
  ? P1 yields CPU for context switch

  ? P1 (Priority: 2) added to ready queue ? Burst time: 6074ms
?? Ready Queue ?????????????????????????????????????????????????????????????????
? [P3 ? P4 ? P5 ? P6 ? P7 ? P8 ? P9 ? P10 ? P11 ? P12 ? P13 ? P1]
????????????????????????????????????????????????????????????????????????????????
]
```

**Explanation of example:**
[P1 started running: It had a total burst time of 6074ms, which is more than the limit.

P1 was interrupted; After running for exactly 3000ms, the scheduler stopped P1

P1 moved to the back; As P1 still has 3074ms left. you can see that it "yielded" the CPU and is now at the very end of the Ready Queue.

New Order: P1 is now at the front of the list, but now it is the last one in the list [P3 ... P1] and it has to wait for its turn agai]

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]

1. **New**: [When the Process object for P1 is first created in the code before the simulation starts]

2. **Runnable**: [When P1 is added to the Ready Queue and is waiting for its turn to use the CPU]

3. **Running**: [When the scheduler picks P1 from the queue and it starts executing its burst time ]

4. **Waiting**: [When the code uses Thread.sleep() to simulate the execution time, putting P1 in a temporary waiting state]

5. **Terminated**: [When P1 finishes its entire burst time and the remainingTime reaches 0. It is then removed from the simulation]

---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: [Multiplayer Game Servers]

**Description**: 
[For a multiplayer shooter game, the server will need to handle the moves of 10 or more players, including shooting, moving evreything!!]

**Why Round-Robin works well here**: 
[Becasue  we need Fairness The server assigns a small "Time Quantum" to each player's data That way if a player has a bad connection or a slow PC they won't make the entire game "lag" for everyone else It keeps the game smooth and fair,and makes sure everyone gets a turn to be processed by the server quickly]

### Example 2: [Background Apps]

**Description**: 
[When you are playing a game with Discord open in the background with some music playing on Spotify]

**Why Round-Robin works well here**: 
[It gives Responsiveness. The CPU switches between your game and Discord so fast that you can talk to your friends without your game "stuttering" Without RoundRobin your game would freeze every time you talk to your friends on Discord because the CPU would be busy with the game]

---

## Summary

**Key concepts I understood through these questions:**
1. I understood how the state changes from New to Running then to Waiting or Terminated depending on the execution of code

2. How Time Quantum (like 3000ms) makes the CPU switch processes in order to ensure fairness for all 

3. How this scheduling algorithm is used in real life (like in Shooter Games) in order to avoid lagging and run background apps like Discord smoothly

**Concepts I need to study more:**
1. Efficiency
2. Waiting Time
