## Problem formulation
We consider the scheduling problem, where operations (jobs) can be parallelized and energy consumption is taken into account. 
Execution of a job at a slower speed is more energy efficient, but leads to a longer processing time and increases 
scheduling metrics.

A set of jobs J={1,...,n} is to be scheduled on two speed scalable processors.
Each job j is characterized by processing volume (work) V_j and the number size_j of required processors.

The standard homogeneous model in speed-scaling is considered. When a processor
runs at a speed s, then the rate with which the energy is consumed is s^a,
where a > 1 is a constant. Each processor may operate at variable speed.
We assume that the total work V_j of a single mode job j should be uniformly divided between the utilized processors.
If job j uses size_j processors, then the processing volumes are the same for all these processors 
(denoted by W_j=V_j / size_j), and they run simultaneously at the same speed. 

The aim is to find a feasible schedule with the minimum sum of completion times so that the energy consumption
is not greater than a given energy budget E.

## Local improvements
We suggest local improvements for the given solution of an instance of this problem. The local impovements have two strategies:

1) Consider blocks from the solution sequentially. If the current block is odd  (i.e. contains odd number of single-processor jobs), 
then we move the last single-processor job of the block to the beginning of the next block, containing at least one single-processor job (if it is possible).

2) Consider blocks from the solution sequentially. If the current block is odd, we move the last single-processor job of the block to the next block b_n, 
containing at least one single-processor job (if it is possible). The job should be assigned as the first job to the processor with maximum idle time. 
If the duration of the block b_n is not changed, then we do not consider this block at the subsequent steps even if this block contains odd number of single-processor jobs.

## Examples
This repository contains two examples: 
- The example from directory `Strategy 1 is better` presents a job order, for which the frist strategy has better result than the second strategy.
- The example from directory `Strategy 2 is better` presents a job order, for which the second strategy has better result than the first strategy.

Each screenshot shows an order for 10 jobs. Each job is presented in format [p, w, d], 
where p - the number of required processors (1 or 2), w - the processing volume for one processor (W_j), d - calculated duration of this job.
