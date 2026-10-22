# 4. CPU Scheduling

## What is CPU scheduling?
CPU scheduling is how the OS chooses a ready process/thread to run on a CPU.

### Why is it needed?
Many tasks may be ready at once, but each CPU core can execute only a limited number of instruction streams at a time. Scheduling balances responsiveness, fairness, and throughput.

## Important terms
- **Arrival time (AT):** when a process enters the ready queue.
- **Burst time (BT):** CPU time required for a burst of work.
- **Completion time (CT):** time at which the process completes.
- **Turnaround time (TAT):** `CT - AT`.
- **Waiting time (WT):** turnaround time minus total CPU burst time in a simple single-burst problem.
- **Response time (RT):** first time scheduled minus arrival time.

## Algorithms

### 1. FCFS — First-Come, First-Served
Processes run in arrival order.
- Easy to understand.
- Non-preemptive in its basic form.
- Can cause the convoy effect: short jobs wait behind a long job.

### 2. SJF — Shortest Job First
Chooses the ready process with the smallest next CPU burst.
- Can minimize average waiting time when burst lengths are known.
- Exact future burst length is often not known.
- Long jobs may starve if short jobs keep arriving.

### 3. SRTF — Shortest Remaining Time First
Preemptive version of SJF. A newly arrived process can preempt the current process if its remaining time is shorter.

### 4. Priority Scheduling
Runs a process with the highest assigned priority.
- Can be preemptive or non-preemptive.
- Low-priority processes may starve.
- **Aging** gradually increases waiting processes' priority to reduce starvation.

### 5. Round Robin (RR)
Each ready process gets a time quantum.
- Good for interactive time-sharing.
- Very small quantum causes frequent context-switch overhead.
- Very large quantum behaves more like FCFS.

### 6. Multilevel Queue / Multilevel Feedback Queue
Uses multiple queues or priority levels. Feedback queues can move processes between queues based on behavior and waiting.

## Example: Round Robin
Suppose P1, P2, and P3 are ready in that order and each needs 5 units of CPU time. Quantum = 2 units.

```text
0--P1--2--P2--4--P3--6--P1--8--P2--10--P3--12
  --P1--13--P2--14--P3--15
```
The final order and completion times depend on arrival times and the exact scheduling rules. This example assumes all arrive at time 0.

## Quick comparison

| Algorithm | Preemptive? | Main advantage | Main concern |
|---|---|---|---|
| FCFS | Usually no | Simple | Convoy effect |
| SJF | Usually no | Low average waiting under assumptions | Needs burst estimates; starvation possible |
| SRTF | Yes | Favors short remaining jobs | More switching; starvation possible |
| Priority | Either | Important tasks can run first | Starvation |
| Round Robin | Yes | Responsive/fair time slices | Quantum choice matters |
| Feedback queue | Usually | Adapts to process behavior | Complex to tune |

## Practice problem
Processes arrive at time 0:
- P1 burst 5
- P2 burst 3
- P3 burst 1

Try drawing the Gantt chart for FCFS and non-preemptive SJF. Then calculate CT, TAT, and WT for each process.
