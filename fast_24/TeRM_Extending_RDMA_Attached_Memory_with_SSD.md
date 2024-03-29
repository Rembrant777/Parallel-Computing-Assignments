# Paper Reading Notes 
## Terminology
* TeRM
* RDMA
* RNIC
* ODP MR 
* pinned MR 
* SSD 
* CPU page fault
* virtual memory 
* physical memory 
* LoC 
* tLib 
* CPU page table 
* Faulting 
* Invalidation 

### My Questions & Confusions 
1. what's the difference between SSD and RDMA ? 
SSD stands for Solid State Drive, a type of storage device that uses non-volatile memory(typically NAND flash memory) to store data. 
SSD provides faster read and write speeds compared to traditional hard disk drives(HDDs).

RDMA stands for Remote Direct Memory Access, that allows data trasfer between two different hosts directly, without involving the CPUs.  
RDMA enables high-speed, low-latency data transfers over a network bypassing the operationg system kernel. 

2. what are the basic operations defined in RDMA ? 
3. why use SSD up forward compatible with RDMA?  
4. ODP MR's role in previous SSD up forward compatible with RDMA?

## Identification of Previous Issues:
Read, Write, Atomic Operation, Memory Registration, Memory Protection, Completion Notificaiton 

## Paper Proposed Solutions:

## Paper Experimental Design: 

## Paper Experimental Data Interpretation: 

## Future Work:

# Questions 

# Critical Thinking 