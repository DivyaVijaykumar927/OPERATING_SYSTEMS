# 5. Process Synchronization

## Why synchronization is needed
Processes and threads may share data. If they access and update shared data at the same time without coordination, the result can be incorrect.

## Race condition
A **race condition** occurs when the result depends on the unpredictable timing/order of concurrent operations.

Example: a shared counter starts at 5. Two threads both read 5, add 1, and write 6. The final value is 6 rather than the expected 7 because one update is lost.

## Critical section
A critical section is code that accesses shared data or resources and must be protected against unsafe concurrent execution.

A correct solution aims for:
1. **Mutual exclusion:** at most one participant enters the protected section at a time.
2. **Progress:** if the section is free and participants want to enter, selection should not be delayed indefinitely.
3. **Bounded waiting:** a participant should not wait forever under the stated assumptions.

## Synchronization tools

### Mutex
A lock that allows one thread at a time to enter a protected region.

```text
lock(mutex)
  update shared data
unlock(mutex)
```
The actual API depends on the programming language and OS. Always release locks safely, even when errors occur.

### Semaphore
A synchronization primitive with a counter.
- **Binary semaphore:** commonly used for signaling or mutual exclusion.
- **Counting semaphore:** represents multiple available instances of a resource.

### Monitor / condition variable
A monitor groups shared state and operations. A condition variable lets a thread wait until a condition may have become true. The condition should be checked in a loop because waking up does not guarantee it is still true.

### Atomic operation
A hardware/language-supported operation that appears indivisible with respect to other concurrent operations. Atomics are useful but do not automatically make every multi-step algorithm correct.

## Producer-consumer example
A producer adds items to a bounded buffer; a consumer removes them.

```text
Producer -> [Shared bounded buffer] -> Consumer
```
The system must prevent:
- Producer adding to a full buffer.
- Consumer removing from an empty buffer.
- Producer and consumer corrupting shared buffer state.

Classic semaphore idea:
- `empty` counts empty slots.
- `full` counts occupied slots.
- `mutex` protects buffer modifications.

## Readers-writers problem
Many readers may read shared data simultaneously, but a writer usually needs exclusive access. Different policies balance reader/writer fairness.

## Dining philosophers
A classic problem showing how competing processes can deadlock or starve while acquiring shared resources.

## Practical rules
- Keep critical sections short.
- Use the synchronization primitives provided by your language/runtime.
- Avoid inconsistent lock ordering.
- Do not assume that timing observed in one run will always repeat.
