# 6. Deadlocks

## What is a deadlock?
A deadlock is a situation where a group of processes is permanently waiting for resources or events that only members of that group can provide.

### Real-life analogy
Two people each hold one pen and need the other's pen to finish. Neither gives up their pen, so both wait forever.

## Four necessary conditions
A deadlock can occur only when all four Coffman conditions hold:
1. **Mutual exclusion:** at least one resource is non-shareable.
2. **Hold and wait:** a process holds one resource while waiting for another.
3. **No preemption:** resources cannot simply be taken away.
4. **Circular wait:** a circular chain exists where each process waits for a resource held by the next.

## Resource example
```text
P1 holds R1 and waits for R2
P2 holds R2 and waits for R1
```
If neither can release its current resource, both are stuck.

## Strategies

### 1. Prevention
Design the system so at least one necessary condition cannot hold.
- Example: require processes to request all resources at once (may reduce utilization).

### 2. Avoidance
Grant a request only if the system remains in a safe state.
- **Banker's algorithm** is a classic avoidance algorithm when maximum resource demands are known.

### 3. Detection and recovery
Allow deadlocks, detect them, and recover.
- Recovery may terminate a process, roll it back, or reclaim resources where safe.

### 4. Ignore
Some general-purpose systems do not attempt to prevent every possible deadlock if the cost of handling rare cases is too high. This is sometimes called the ostrich approach.

## Safe state vs deadlock
- **Safe state:** there exists an order in which all processes can finish with available resources and their remaining needs.
- **Unsafe state:** no safe sequence is known under the model; it is not necessarily already deadlocked.
- **Deadlock:** processes are actually stuck in a circular/resource wait situation.

## Deadlock vs starvation
- **Deadlock:** a set of processes cannot progress because they wait on one another/resources.
- **Starvation:** a process waits indefinitely because it is repeatedly denied a resource or CPU time, while other work may continue.

## Revision questions
1. Name the four necessary conditions.
2. Compare prevention, avoidance, detection, and recovery.
3. Why is an unsafe state not automatically a deadlock?
4. Give a real-world deadlock example.
