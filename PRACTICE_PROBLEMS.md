# Practice Problems - High-Yield Questions

Based on past papers analysis, these are the most common question patterns you'll encounter.

---

## 🔴 PROBLEM SET 1: Page Replacement (CRITICAL!)

### Problem 1.1 - LRU with 3 Frames
**Page reference sequence:** 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5

Calculate page faults using LRU algorithm with 3 frames.

```
Reference: 1  2  3  4  1  2  5  1  2  3  4  5
Frame 1:   1  1  1  4  4  4  4  4  4  3  3  3
Frame 2:      2  2  2  1  1  1  1  1  1  4  4
Frame 3:         3  3  3  2  5  5  5  5  5  5
Fault?     ✓  ✓  ✓  ✓     ✓  ✓        ✓  ✓  ✓
```

**Answer:** 9 page faults

---

### Problem 1.2 - FIFO with 3 Frames
**Same sequence:** 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5

Calculate page faults using FIFO algorithm with 3 frames.

```
Reference: 1  2  3  4  1  2  5  1  2  3  4  5
Frame 1:   1  1  1  4  4  4  5  5  5  3  3  3
Frame 2:      2  2  2  1  1  1  1  1  1  4  4
Frame 3:         3  3  3  2  2  2  2  2  2  5
Fault?     ✓  ✓  ✓  ✓  ✓  ✓  ✓        ✓  ✓  ✓
```

**Answer:** 10 page faults

---

### Problem 1.3 - FIFO with 4 Frames (Belady's Anomaly)
**Same sequence with MORE frames:** 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5

```
Reference: 1  2  3  4  1  2  5  1  2  3  4  5
Frame 1:   1  1  1  1  1  1  5  5  5  5  5  5
Frame 2:      2  2  2  2  2  2  1  1  1  1  1
Frame 3:         3  3  3  3  3  3  2  2  2  2
Frame 4:            4  4  4  4  4  4  3  4  4
Fault?     ✓  ✓  ✓  ✓        ✓     ✓  ✓  ✓  ✓
```

**Answer:** 10 page faults

**Belady's Anomaly Demonstrated:**
- 3 frames with FIFO: 10 faults
- 4 frames with FIFO: 10 faults
- Adding a frame did NOT reduce faults! (Actually stayed same, but in some cases can increase)

**Definition:** Belady's Anomaly occurs when increasing the number of page frames results in more (or same) page faults using FIFO replacement algorithm.

---

### Practice Problem 1.4 (Do Yourself!)
**Sequence:** 3, 4, 1, 5, 3, 4, 2, 3, 4, 1, 5, 2

Calculate for:
- LRU with 3 frames
- FIFO with 3 frames
- LRU with 4 frames
- FIFO with 4 frames
- Demonstrate Belady's anomaly if it occurs

---

## 🔴 PROBLEM SET 2: ALU Control Signals

### Problem 2.1 - Fill the Table

Given a 1-bit ALU with controls: F0, F1, ena, enb, inva, inc

| Function | F0 | F1 | ena | enb | inva | inc | Explanation |
|----------|----|----|-----|-----|------|-----|-------------|
| A + B    | 1  | 1  | 1   | 1   | 0    | 0   | Enable both, add |
| A + B + 1| 1  | 1  | 1   | 1   | 0    | 1   | Enable both, add, +1 |
| B - A    | 1  | 1  | 1   | 1   | 1    | 1   | Invert A, +1 (two's complement), add B |
| -A       | 1  | 1  | 1   | 0   | 1    | 1   | Invert A, +1, B disabled |

### Problem 2.2 - Explain B - A

**Question:** "Explain your reasoning for calculating B - A"

**Answer:** To calculate B - A, we use two's complement arithmetic. Two's complement of A is obtained by inverting all bits of A (inva=1) and adding 1 (inc=1). Then we add this to B. So: B - A = B + (-A) = B + (NOT A + 1). This requires enabling both A and B (ena=1, enb=1), inverting A (inva=1), incrementing (inc=1), and setting F0=F1=1 for addition.

---

## 🔴 PROBLEM SET 3: Proportional Allocation

### Problem 3.1 - Standard Problem
System with 62 frames. Two processes:
- Process A: 10 pages
- Process B: 127 pages

**Calculate frames allocated to each:**

```
Total pages = 10 + 127 = 137
Process A: (10/137) × 62 = 4.52 ≈ 4 frames
Process B: (127/137) × 62 = 57.48 ≈ 57 frames
```

**Answer for large process:** 57 frames (this is the common exam question)

---

### Problem 3.2 - Three Processes
System with 100 frames. Three processes:
- Process A: 20 pages
- Process B: 50 pages  
- Process C: 30 pages

**Calculate frames for each:**

```
Total pages = 20 + 50 + 30 = 100
Process A: (20/100) × 100 = 20 frames
Process B: (50/100) × 100 = 50 frames
Process C: (30/100) × 100 = 30 frames
```

---

## 🔴 PROBLEM SET 4: Memory Allocation (First-fit/Best-fit)

### Problem 4.1 - Standard Problem
Memory partitions: (1) 100K, (2) 500K, (3) 200K, (4) 300K, (5) 600K
Processes to allocate: 212K, 417K, 112K, 426K
Circular list starting at partition 1.

**First-Fit:**
```
212K → Partition 2 (500K) ✓
417K → Partition 5 (600K) ✓
112K → Partition 3 (200K) ✓ (continues from after partition 2)
426K → Partition 2 (288K remaining, not enough), 
       check 3 (88K remaining, not enough),
       check 4 (300K) - NOT ENOUGH,
       check 5 (183K remaining) - NOT ENOUGH
       → Cannot allocate!
```

**First-fit Answer:** 2, 5, 3, FAIL

**Best-Fit:**
```
212K → Best is partition 4 (300K, waste=88K)
417K → Best is partition 2 (500K, waste=83K)
112K → Best is partition 3 (200K, waste=88K)
426K → Best is partition 5 (600K, waste=174K)
```

**Best-fit Answer:** 4, 2, 3, 5

---

## 🔴 PROBLEM SET 5: Second-Chance Algorithm

### Problem 5.1 - Page Classes
Second-chance algorithm with reference bit and modify bit (in that order).

Page classes in memory:
- Page A: (1, 1) - referenced, modified
- Page B: (0, 0) - not referenced, not modified
- Page C: (1, 0) - referenced, not modified
- Page D: (0, 1) - not referenced, modified

**Question:** Which page is evicted first?

**Answer:** Page B (0, 0) - not referenced and not modified is the first choice for eviction.

**Eviction Priority Order:**
1. (0, 0) - Clean, not used recently ← EVICT FIRST
2. (0, 1) - Dirty but not used recently
3. (1, 0) - Clean but used recently (reference bit cleared on second chance)
4. (1, 1) - Dirty and used recently ← KEEP IF POSSIBLE

---

## 🔴 PROBLEM SET 6: Pipeline Dependencies

### Problem 6.1 - Identify Dependencies

```assembly
Instruction 1: R1 = R2 * R3
Instruction 2: R4 = R5 + R1
```

**Question:** What type of dependency?

**Answer:** RAW (Read After Write)
- Instruction 2 reads R1 which is written by instruction 1
- This is a "true" dependency - cannot be eliminated
- Can only mitigate with forwarding/bypassing

---

### Problem 6.2 - Multiple Dependencies

```assembly
Instruction 1: R1 = R2 + R3
Instruction 2: R2 = R4 + R5
Instruction 3: R1 = R6 + R7
```

**Between 1 and 2:** WAR (Write After Read)
- Inst 1 reads R2, inst 2 writes R2
- Anti-dependency, can eliminate with register renaming

**Between 1 and 3:** WAW (Write After Write)  
- Both write to R1
- Output dependency, can eliminate with register renaming

---

## 🔴 PROBLEM SET 7: Short Definitions

### Practice writing one-sentence definitions:

1. **Bus skew**
   - *Answer: The time difference when a signal arrives at different components due to varying wire lengths.*

2. **Unified cache**
   - *Answer: A single cache memory that stores both instructions and data.*

3. **Register renaming**
   - *Answer: A hardware technique that maps architectural registers to a larger pool of physical registers to eliminate false dependencies.*

4. **Internal fragmentation**
   - *Answer: Wasted space within an allocated memory block that is not used by the process.*

5. **External fragmentation**
   - *Answer: Wasted space between allocated memory blocks where total free memory is sufficient but not contiguous.*

6. **Copy-on-write**
   - *Answer: A memory optimization technique where processes share pages until one modifies a page, at which point a copy is made.*

7. **Thrashing**
   - *Answer: A condition where a system spends more time swapping pages between memory and disk than executing processes.*

8. **Sign extension**
   - *Answer: The process of extending a smaller signed value to a larger width by copying the sign bit to the new high-order bits.*

---

## 🔴 PROBLEM SET 8: Long Answer Questions

### Problem 8.1 - TLB Operation (3 marks)

**Question:** Briefly describe the operation of a translation lookaside buffer.

**Answer Template:**
A Translation Lookaside Buffer (TLB) is a cache for virtual-to-physical address translations. When the CPU generates a virtual address, the TLB is first checked for the mapping. If found (TLB hit), the physical address is used immediately, providing fast translation. If not found (TLB miss), the page table must be consulted to find the translation, which is then cached in the TLB for future use. The TLB significantly speeds up memory access by avoiding repeated page table lookups.

---

### Problem 8.2 - FAT vs inodes (6 marks)

**Question:** Discuss, compare, and evaluate the allocation strategies provided by FAT on the one hand, and Linux inodes on the other. Your analysis must include references to file size, access time, and fragmentation.

**Answer Template:**

**FAT (File Allocation Table):**
FAT uses a central table where each entry points to the next cluster of the file, forming a linked list. 
- *File Size:* Limited by table size; poor scalability for very large files
- *Access Time:* Sequential access requires traversing the chain, slow for large files; no direct access to middle of file
- *Fragmentation:* Susceptible to external fragmentation as files are scattered across non-contiguous clusters

**Linux inodes:**
Linux uses index nodes (inodes) with direct, indirect, double-indirect, and triple-indirect pointers.
- *File Size:* Scales well from small to very large files; direct pointers for small files, multi-level indirect for large
- *Access Time:* Fast for small files (direct pointers); reasonable for large files (at most 3-4 levels of indirection); supports random access
- *Fragmentation:* Reduced fragmentation; small files use direct pointers efficiently; internal fragmentation minimal

**Evaluation:**
Inodes are superior for general-purpose file systems due to better scalability, faster access, and reduced fragmentation. FAT is simpler and suitable for small, embedded systems with limited file sizes. Inodes' multi-level indexing provides an elegant solution to the trade-off between small file efficiency and large file support.

---

### Problem 8.3 - Thrashing (3 marks)

**Question:** Explain briefly what thrashing is, and give an example of circumstances on a computer system under which it can occur.

**Answer Template:**
Thrashing occurs when a computer system spends more time handling page faults (swapping pages between memory and disk) than executing actual processes. This happens because there is insufficient physical memory for the active processes' working sets.

**Example:** On a system with 2GB RAM, if 10 large programs (each requiring 500MB) are running simultaneously, none has enough memory for its working set. The system constantly evicts pages needed by other processes, causing continuous page faults. CPU utilization drops dramatically as the disk I/O for swapping dominates, even though processes are ready to run. The solution is to reduce the degree of multiprogramming or add more physical memory.

---

### Problem 8.4 - Pipeline Dependencies (4 marks)

**Question:** RAW dependencies are also often called "true dependencies". Motivate this characterization, with reference to other instruction dependencies, and also say what can be done to mitigate these other dependencies.

**Answer Template:**
RAW (Read After Write) dependencies are called "true" dependencies because they represent genuine data flow in the program - a later instruction truly needs the value produced by an earlier instruction. Unlike other dependencies, RAW cannot be eliminated as they reflect the program's semantic meaning.

The other dependencies are "false" or "name" dependencies:
- **WAR (Write After Read):** Occurs when an instruction writes to a register that a previous instruction reads. This is a false dependency caused only by register naming.
- **WAW (Write After Write):** Occurs when two instructions write to the same register. Again, this is a naming conflict, not a true data dependency.

**Mitigation:** Both WAR and WAW dependencies can be eliminated through **register renaming**. The hardware maintains a pool of physical registers and dynamically maps architectural registers to different physical registers, removing naming conflicts while preserving true data flow. RAW dependencies, being true dependencies, require forwarding/bypassing to minimize stalls but cannot be eliminated entirely.

---

## 🎯 FINAL PRACTICE TIPS

### Before the test:
1. **Do all Problem Sets 1-8** at least once
2. **Time yourself** - you have limited time in the exam
3. **Practice writing definitions** without looking
4. **Draw the ALU table** from memory
5. **Work through 3 different page replacement sequences**

### Common mistakes to avoid:
- ❌ Forgetting to count initial page faults (empty frames)
- ❌ Mixing up RAW/WAR/WAW definitions
- ❌ Rounding errors in proportional allocation
- ❌ Not showing work on calculations
- ❌ Writing paragraphs for "one sentence" questions

### Easy marks to grab:
- ✓ Multiple choice (Intel instructions, Mic-1 registers)
- ✓ One-sentence definitions (10 marks available!)
- ✓ Proportional allocation (simple formula)
- ✓ Second-chance algorithm (memorize order)
- ✓ Pipeline dependency identification

---

**Practice these until you can do them in your sleep! 💪**
