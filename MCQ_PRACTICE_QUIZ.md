# 🎯 MCQ PRACTICE QUIZ - CS 244

**Instructions:** 50 multiple choice questions covering high-yield topics. Time yourself: aim for 1 minute per question. Answers and explanations at the bottom.

---

## SECTION 1: MEMORY MANAGEMENT (Questions 1-15)

**1. Which page replacement algorithm can suffer from Belady's Anomaly?**
   - A) LRU
   - B) FIFO
   - C) Optimal
   - D) Second-Chance

**2. What is thrashing?**
   - A) A disk failure mode
   - B) System spends more time paging than executing
   - C) Cache coherence protocol
   - D) Type of fragmentation

**3. Internal fragmentation occurs when:**
   - A) Memory between allocated blocks is wasted
   - B) Allocated block is larger than needed by process
   - C) Page table is full
   - D) TLB miss rate is high

**4. External fragmentation occurs when:**
   - A) Process terminates unexpectedly
   - B) Total free memory is sufficient but not contiguous
   - C) Virtual memory is disabled
   - D) Cache is full

**5. A system has 100 frames. Process A needs 20 pages, Process B needs 80 pages. Using proportional allocation, how many frames does Process B get?**
   - A) 50
   - B) 60
   - C) 80
   - D) 100

**6. What does TLB stand for?**
   - A) Translation Lookahead Buffer
   - B) Translation Lookaside Buffer
   - C) Transfer Logic Block
   - D) Temporal Load Balancer

**7. In the second-chance page replacement algorithm, which page class is evicted FIRST?**
   - A) (1, 1) - Referenced, Modified
   - B) (1, 0) - Referenced, Not Modified
   - C) (0, 1) - Not Referenced, Modified
   - D) (0, 0) - Not Referenced, Not Modified

**8. A TLB is essentially a:**
   - A) Cache for page table entries
   - B) Backup memory system
   - C) Type of secondary storage
   - D) Pipeline buffer

**9. Which is TRUE about demand paging?**
   - A) All pages loaded at program start
   - B) Pages loaded only when referenced
   - C) Requires segmentation
   - D) Eliminates page faults

**10. Page table entries typically contain:**
   - A) Virtual page number only
   - B) Physical frame number and control bits
   - C) Process ID only
   - D) Memory address range

**11. What causes a page fault?**
   - A) Referenced page not in physical memory
   - B) TLB is full
   - C) Cache miss
   - D) Stack overflow

**12. Copy-on-write is used to:**
   - A) Back up important files
   - B) Share pages between processes until modification
   - C) Implement virtual memory
   - D) Speed up disk writes

**13. Working set model is used to:**
   - A) Predict future page references
   - B) Determine pages needed by process
   - C) Optimize disk scheduling
   - D) Implement RAID

**14. In a system with 4KB pages, a virtual address has 20 bits for page number. How many pages can be addressed?**
   - A) 2^12
   - B) 2^20
   - C) 2^32
   - D) 4096

**15. Segmentation differs from paging in that:**
   - A) Segments have variable size, pages are fixed
   - B) Segments are faster
   - C) Paging requires special hardware
   - D) Segments cannot be shared

---

## SECTION 2: PROCESSOR & MICROARCHITECTURE (Questions 16-30)

**16. In the Mic-1, which register always holds the top of stack?**
   - A) SP
   - B) TOS
   - C) CPP
   - D) LV

**17. The H register in Mic-1 is used for:**
   - A) Handling interrupts
   - B) Holding temporary ALU operands
   - C) Hardware configuration
   - D) Head pointer for queues

**18. Which Mic-1 operation CANNOT be encoded in a single microinstruction?**
   - A) H = H + MDR
   - B) H = MDR + H
   - C) H = H - MDR
   - D) H = MDR - H

**19. What does the N bit in Mic-1 indicate?**
   - A) Next instruction ready
   - B) ALU result is negative
   - C) No operation needed
   - D) Null pointer detected

**20. What does the Z bit in Mic-1 indicate?**
   - A) Zero division error
   - B) Zone memory access
   - C) ALU result is zero
   - D) Z register is full

**21. RAW dependency stands for:**
   - A) Random Access Write
   - B) Read After Write
   - C) Register Allocation Window
   - D) Reconfigurable Arithmetic Wrapper

**22. Which dependency can be eliminated by register renaming?**
   - A) RAW (Read After Write)
   - B) WAR (Write After Read)
   - C) True dependency
   - D) Data dependency

**23. In instruction pipelining, a hazard occurs when:**
   - A) Pipeline is empty
   - B) Instructions cannot proceed due to dependencies
   - C) Cache is full
   - D) Interrupts are disabled

**24. Register renaming helps with:**
   - A) True dependencies (RAW)
   - B) Anti-dependencies (WAR) and output dependencies (WAW)
   - C) Cache coherence
   - D) Virtual memory management

**25. Superscalar architecture allows:**
   - A) Multiple instructions to execute in parallel
   - B) Larger register files
   - C) Faster clock speeds
   - D) More cache memory

**26. Branch prediction is used to:**
   - A) Eliminate all pipeline stalls
   - B) Reduce pipeline stalls from conditional branches
   - C) Predict page faults
   - D) Optimize cache placement

**27. A static branch prediction strategy might be:**
   - A) Always take backward branches (loops)
   - B) Randomly guess
   - C) Never predict
   - D) Only predict in kernel mode

**28. Cache locality has two types:**
   - A) Fast and slow
   - B) Temporal and spatial
   - C) Direct and indirect
   - D) Local and global

**29. Temporal locality means:**
   - A) Data accessed recently likely accessed again soon
   - B) Data near each other accessed together
   - C) Time-based access patterns
   - D) Temporary storage usage

**30. Spatial locality means:**
   - A) Data accessed recently likely accessed again
   - B) Data near recently accessed data likely accessed soon
   - C) Space-efficient storage
   - D) Spatial memory layout

---

## SECTION 3: ASSEMBLY & ISA (Questions 31-40)

**31. Which Intel instruction affects the stack pointer (SP)?**
   - A) MOV
   - B) ADD
   - C) PUSH
   - D) CMP

**32. Which Intel instruction does NOT affect the stack pointer?**
   - A) CALL
   - B) RET
   - C) POP
   - D) TEST

**33. The largest page size in Intel IA-32 architecture is:**
   - A) 4 KB
   - B) 2 MB
   - C) 4 MB
   - D) 1 GB

**34. Sign extension is used to:**
   - A) Extend unsigned numbers
   - B) Copy sign bit when expanding signed numbers
   - C) Add signatures to code
   - D) Extend execution time

**35. In 8088, a segment register is:**
   - A) 8 bits wide
   - B) 16 bits wide
   - C) 32 bits wide
   - D) 64 bits wide

**36. Little endian byte ordering means:**
   - A) Most significant byte at lowest address
   - B) Least significant byte at lowest address
   - C) Random byte ordering
   - D) No specific byte order

**37. An immediate operand is:**
   - A) A constant value in the instruction
   - B) A memory address
   - C) A register name
   - D) An I/O port

**38. Register indirect addressing uses:**
   - A) Register contains the data
   - B) Register contains address of data
   - C) Register contains instruction
   - D) Two registers for calculation

**39. RISC design principles include:**
   - A) Complex instruction set
   - B) Many addressing modes
   - C) Load/store architecture with simple instructions
   - D) Microprogrammed control

**40. CISC processors typically have:**
   - A) Very few instructions
   - B) Only load/store operations
   - C) Many complex instructions with many addressing modes
   - D) No cache memory

---

## SECTION 4: FILE SYSTEMS & I/O (Questions 41-50)

**41. FAT (File Allocation Table) is:**
   - A) A type of RAM
   - B) A file system using a table to track block chains
   - C) A cache algorithm
   - D) A page replacement strategy

**42. In Linux, an inode contains:**
   - A) File data
   - B) File metadata and pointers to data blocks
   - C) Directory listing
   - D) User passwords

**43. Why are hard links to directories typically prohibited?**
   - A) They're too slow
   - B) They waste space
   - C) They can create cycles making garbage collection impossible
   - D) They require too much memory

**44. Unix inodes use multi-level indexing with:**
   - A) Only direct pointers
   - B) Direct, single indirect, double indirect, triple indirect
   - C) Only indirect pointers
   - D) Random access pointers

**45. Compared to FAT, inodes are:**
   - A) Slower for all file sizes
   - B) Better for large files due to multi-level indexing
   - C) Simpler to implement
   - D) Can only handle small files

**46. Bus skew refers to:**
   - A) Bent bus connectors
   - B) Time difference in signal arrival due to varying wire lengths
   - C) Bus bandwidth limitation
   - D) Bus protocol errors

**47. DMA (Direct Memory Access) allows:**
   - A) CPU to access disk directly
   - B) I/O devices to transfer data without CPU intervention
   - C) Direct access to virtual memory
   - D) Faster cache access

**48. A multiplexed bus:**
   - A) Connects multiple computers
   - B) Uses same wires for address and data at different times
   - C) Only works with specific devices
   - D) Requires special software

**49. In a write-back cache:**
   - A) Data written immediately to main memory
   - B) Data written to cache only, main memory updated later
   - C) Cache is never written
   - D) All writes bypass cache

**50. Cache coherence is a problem in:**
   - A) Single processor systems
   - B) Multiprocessor systems with multiple caches
   - C) Systems without cache
   - D) Virtual memory systems

---

---

# ✅ ANSWER KEY

## SECTION 1: MEMORY MANAGEMENT
1. **B** - FIFO can suffer from Belady's Anomaly
2. **B** - Thrashing is excessive paging
3. **B** - Internal fragmentation is wasted space within allocated block
4. **B** - External fragmentation is non-contiguous free memory
5. **C** - (80/100) × 100 = 80 frames
6. **B** - Translation Lookaside Buffer
7. **D** - (0,0) evicted first in second-chance
8. **A** - TLB caches page table entries
9. **B** - Pages loaded only when needed
10. **B** - Contains frame number and control bits
11. **A** - Page not in physical memory
12. **B** - Share pages until modification needed
13. **B** - Determines pages needed by process
14. **B** - 2^20 pages possible
15. **A** - Segments variable, pages fixed size

## SECTION 2: PROCESSOR & MICROARCHITECTURE
16. **B** - TOS (Top Of Stack) register
17. **B** - H holds temporary ALU operands
18. **D** - H = MDR - H cannot be encoded (operand order matters)
19. **B** - N bit indicates negative result
20. **C** - Z bit indicates zero result
21. **B** - Read After Write
22. **B** - WAR can be eliminated by renaming
23. **B** - Hazard is when instructions cannot proceed
24. **B** - Helps with WAR and WAW
25. **A** - Multiple instructions in parallel
26. **B** - Reduces branch stalls
27. **A** - Take backward (loop) branches
28. **B** - Temporal and spatial
29. **A** - Recent data accessed again soon
30. **B** - Nearby data accessed together

## SECTION 3: ASSEMBLY & ISA
31. **C** - PUSH affects SP
32. **D** - TEST does not affect SP
33. **C** - 4 MB (4 MiB) is largest
34. **B** - Copy sign bit when expanding
35. **B** - 16 bits wide
36. **B** - LSB at lowest address
37. **A** - Constant value in instruction
38. **B** - Register contains address
39. **C** - Load/store with simple instructions
40. **C** - Many complex instructions

## SECTION 4: FILE SYSTEMS & I/O
41. **B** - File system using table for block chains
42. **B** - Metadata and pointers to data blocks
43. **C** - Creates cycles, impossible garbage collection
44. **B** - Direct, single, double, triple indirect
45. **B** - Better for large files
46. **B** - Time difference in signal arrival
47. **B** - I/O without CPU intervention
48. **B** - Same wires for address and data
49. **B** - Write to cache, update memory later
50. **B** - Problem in multiprocessor systems

---

# 📊 SCORING GUIDE

**45-50 correct (90-100%)**: Excellent! You're very well prepared.  
**40-44 correct (80-89%)**: Great! You're on track for a strong performance.  
**35-39 correct (70-79%)**: Good! Review topics you missed.  
**30-34 correct (60-69%)**: Passing territory. Focus on weak areas.  
**25-29 correct (50-59%)**: Target achieved! Keep reviewing.  
**Below 25 (below 50%)**: Study the missed topics urgently!

---

# 🎯 TOPICS TO REVIEW BASED ON WRONG ANSWERS

**If you missed Section 1 (Memory):**
- Review page replacement algorithms (LRU, FIFO)
- Study Belady's Anomaly
- Understand fragmentation types
- Learn TLB operation

**If you missed Section 2 (Processor):**
- Study Mic-1 architecture and registers
- Learn pipeline dependencies (RAW, WAR, WAW)
- Understand register renaming
- Review cache locality principles

**If you missed Section 3 (Assembly/ISA):**
- Memorize Intel stack pointer instructions
- Learn addressing modes
- Understand RISC vs CISC
- Review byte ordering

**If you missed Section 4 (File Systems/I/O):**
- Compare FAT vs inodes thoroughly
- Understand Unix file system structure
- Learn bus concepts
- Study cache write policies

---

# 💡 QUICK TIPS FOR MCQs IN EXAM

1. **Elimination Strategy**: Cross out obviously wrong answers first
2. **Keyword Recognition**: Look for key terms in questions
3. **Time Management**: Don't spend more than 1 minute per MCQ
4. **Never Leave Blank**: Guess if you must (25% chance is better than 0%)
5. **Check Extremes**: "Always" and "Never" are usually wrong
6. **Trust First Instinct**: Usually right unless you spot clear error

---

**Good luck! Practice these until you get 40+/50 consistently! 🚀**

*Created from CS 244 past paper analysis (2011-2022)*
