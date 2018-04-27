## 1. List all of the main states a process may be in at any point in time on a standard Unix system. Briefly explain what each of these states mean.
  - Created: The process has been created and is waiting to be approved by the scheduler and moved to the 'Ready' state.
  - Ready: The process has been loaded into memory and waiting in a queue to be executed by the CPU.
  - Running: The process has been chosen by the scheduler to be executed by one of the CPU or cores in a system. It is typically run in either a 'Kernel mode' or 'User mode'.
  - Blocked: The process can't contune with some kind of external input (like user input or I/O from a peripheral) so it is but in a 'blocked' state.
  - Terminated: The process has either completed executing or has been terminated.

## 2. What is a Zombie Process? How does it get created? How does it get destroyed?
  It is a child process that is no longer scheduled to be executed. Even after a process is terminated or completed it still remains in the process table as a Zombie Process. It gets destroyed once the parent process calls the `wait` system call and reads it's exit status. The process is then removed from the process table and killed for good. If the parent fails to kill it it can lead to a resource leak.

## 3. Describe the job of the Scheduler in the OS in general.
  A CPU or core can only run one process at a time. In order for it to handle concurrent tasks it needs to continually switch off the process it is running. The Scheduler ensure that all processes are executed, seemingly concurrently, in a manner that balances efficiency and responsiveness.

## 4. Describe the benefits of the MLFQ over a plain Round-Robin scheduler.
  A MLFQ aims to minimize turnaround time while also lowering response time. While RR can reduce response time, the turnaround time can be high. MLFQ organizes the process into different priority levels and can 'learn' about the process as it's running and predict future behavior.
