- Main memory management is crucial
	- entire system performance relies on the amount of memory available and the optimization of it during job processing.
## Single User Contiguous
- Single User System : non-networked environment
- Entire program is loaded into memory
- Contiguous memory spaces that get allocated as needed
- Jobs are processes sequentially
- Drawbacks
	- multiprogramming and networking not supported
	- not cost effective
- Memory Manager: performs minimal work
	- evaluates incoming process size
		- loads if small enough to fit
		- if not then rejects and evaluates next incoming process
	- monitors occupies memory space
		- makes entire memory space available upon the ending of a process and then starts over

## Fixed Partitions
- Main Memory: Partitioned
	- each partition: one job
	- static: reconfiguration requires system shut down
- Role of memory manager
	- protect each jobs memory space
	- match job size with partition size

Example of a simplified  fixed partition memory table for a machine with 400K of memory:

| Operating System   |
| ------------------ |
| Partition 1 (100K) |
| Partition 2 (25K)  |
| Partition 3 (25K)  |
| Partition 4 (50K)  |
Operating system is locations 0K-200K
Partition 1 is locations 200K-300K
Partition 2 is locations 300K-325K
Partition 3 is locations 325K-350K
Partition 4 is locations 350K-400K

- Requires contiguous loading of entire program
- Job allocations method
	- first available partition with required size
- To work well, all jobs have similar size and memory size known ahead of time.
- Drawbacks vary based on partition size
	- partitions too small &rarr; large jobs have longer turnaround time
	- partitions too large &rarr; memory waste: internal fragmentation

