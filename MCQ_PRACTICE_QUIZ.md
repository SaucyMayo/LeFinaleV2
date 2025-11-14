# 🎯 MCQ PRACTICE QUIZ - CS 244

**Instructions:** 50 multiple choice questions covering high-yield topics. Answers with explanations are provided immediately after each question for quick learning.

---

## SECTION 1: MEMORY MANAGEMENT (Questions 1-15)

**1. Which page replacement algorithm can suffer from Belady's Anomaly?**
   - A) LRU
   - B) FIFO
   - C) Optimal
   - D) Second-Chance

**Answer: B) FIFO**  
**Explanation:** FIFO (First-In First-Out) can suffer from Belady's Anomaly, where increasing the number of page frames can actually increase the number of page faults. This counterintuitive behavior does not occur with LRU or Optimal algorithms.

---

**2. What is thrashing?**
   - A) A disk failure mode
   - B) System spends more time paging than executing
   - C) Cache coherence protocol
   - D) Type of fragmentation

**Answer: B) System spends more time paging than executing**  
**Explanation:** Thrashing occurs when a system has insufficient memory and spends most of its time swapping pages in and out rather than executing processes. This severely degrades performance.

---

**3. Internal fragmentation occurs when:**
   - A) Memory between allocated blocks is wasted
   - B) Allocated block is larger than needed by process
   - C) Page table is full
   - D) TLB miss rate is high

**Answer: B) Allocated block is larger than needed by process**  
**Explanation:** Internal fragmentation is wasted space within an allocated memory block. For example, if a process needs 3.5KB but is allocated a 4KB page, the remaining 0.5KB is internal fragmentation.

---

**4. External fragmentation occurs when:**
   - A) Process terminates unexpectedly
   - B) Total free memory is sufficient but not contiguous
   - C) Virtual memory is disabled
   - D) Cache is full

**Answer: B) Total free memory is sufficient but not contiguous**  
**Explanation:** External fragmentation happens when free memory is scattered in small non-contiguous blocks. Even though the total free memory might be sufficient for a process, it cannot be allocated because no single contiguous block is large enough.

---

**5. A system has 100 frames. Process A needs 20 pages, Process B needs 80 pages. Using proportional allocation, how many frames does Process B get?**
   - A) 50
   - B) 60
   - C) 80
   - D) 100

**Answer: C) 80**  
**Explanation:** Proportional allocation formula: (process_pages / total_pages) × total_frames = (80/100) × 100 = 80 frames for Process B.

---

**6. What does TLB stand for?**
   - A) Translation Lookahead Buffer
   - B) Translation Lookaside Buffer
   - C) Transfer Logic Block
   - D) Temporal Load Balancer

**Answer: B) Translation Lookaside Buffer**  
**Explanation:** TLB is a cache that stores recent virtual-to-physical address translations to speed up memory access. It's a critical component of virtual memory systems.

---

**7. In the second-chance page replacement algorithm, which page class is evicted FIRST?**
   - A) (1, 1) - Referenced, Modified
   - B) (1, 0) - Referenced, Not Modified
   - C) (0, 1) - Not Referenced, Modified
   - D) (0, 0) - Not Referenced, Not Modified

**Answer: D) (0, 0) - Not Referenced, Not Modified**  
**Explanation:** Second-chance algorithm evicts pages in order: (0,0) → (0,1) → (1,0) → (1,1). Pages that haven't been referenced and haven't been modified are the first candidates for eviction.

---

**8. A TLB is essentially a:**
   - A) Cache for page table entries
   - B) Backup memory system
   - C) Type of secondary storage
   - D) Pipeline buffer

**Answer: A) Cache for page table entries**  
**Explanation:** The TLB caches recently used page table entries to avoid the overhead of accessing the page table in main memory for every address translation.

---

**9. Which is TRUE about demand paging?**
   - A) All pages loaded at program start
   - B) Pages loaded only when referenced
   - C) Requires segmentation
   - D) Eliminates page faults

**Answer: B) Pages loaded only when referenced**  
**Explanation:** Demand paging loads pages into memory only when they are actually needed (referenced), not at program startup. This saves memory but can cause page faults.

---

**10. Page table entries typically contain:**
   - A) Virtual page number only
   - B) Physical frame number and control bits
   - C) Process ID only
   - D) Memory address range

**Answer: B) Physical frame number and control bits**  
**Explanation:** Each page table entry contains the physical frame number (where the page is stored) plus control bits (present/absent, read/write permissions, modified bit, referenced bit, etc.).

---

**11. What causes a page fault?**
   - A) Referenced page not in physical memory
   - B) TLB is full
   - C) Cache miss
   - D) Stack overflow

**Answer: A) Referenced page not in physical memory**  
**Explanation:** A page fault occurs when a process tries to access a page that is not currently in physical memory. The operating system must then load the page from disk.

---

**12. Copy-on-write is used to:**
   - A) Back up important files
   - B) Share pages between processes until modification
   - C) Implement virtual memory
   - D) Speed up disk writes

**Answer: B) Share pages between processes until modification**  
**Explanation:** Copy-on-write allows processes (like parent and child after fork()) to share the same physical pages until one tries to modify the page. Only then is a copy made, saving memory.

---

**13. Working set model is used to:**
   - A) Predict future page references
   - B) Determine pages needed by process
   - C) Optimize disk scheduling
   - D) Implement RAID

**Answer: B) Determine pages needed by process**  
**Explanation:** The working set model identifies the set of pages a process is actively using. This helps the OS decide which pages to keep in memory to avoid thrashing.

---

**14. In a system with 4KB pages, a virtual address has 20 bits for page number. How many pages can be addressed?**
   - A) 2^12
   - B) 2^20
   - C) 2^32
   - D) 4096

**Answer: B) 2^20**  
**Explanation:** With 20 bits for the page number, you can address 2^20 = 1,048,576 different pages. The page size (4KB) determines the offset bits, not the number of pages.

---

**15. Segmentation differs from paging in that:**
   - A) Segments have variable size, pages are fixed
   - B) Segments are faster
   - C) Paging requires special hardware
   - D) Segments cannot be shared

**Answer: A) Segments have variable size, pages are fixed**  
**Explanation:** The fundamental difference is that segments (code, data, stack) have variable sizes based on logical divisions, while pages are fixed-size blocks (e.g., 4KB).

---

## SECTION 2: PROCESSOR & MICROARCHITECTURE (Questions 16-30)

**16. In the Mic-1, which register always holds the top of stack?**
   - A) SP
   - B) TOS
   - C) CPP
   - D) LV

**Answer: B) TOS**  
**Explanation:** TOS (Top Of Stack) register always holds the value at the top of the stack for quick access. This optimization avoids memory access for the most frequently used stack element.

---

**17. The H register in Mic-1 is used for:**
   - A) Handling interrupts
   - B) Holding temporary ALU operands
   - C) Hardware configuration
   - D) Head pointer for queues

**Answer: B) Holding temporary ALU operands**  
**Explanation:** The H (Holding) register temporarily holds one of the ALU operands during microinstruction execution. It's essential for ALU operations.

---

**18. Which Mic-1 operation CANNOT be encoded in a single microinstruction?**
   - A) H = H + MDR
   - B) H = MDR + H
   - C) H = H - MDR
   - D) H = MDR - H

**Answer: D) H = MDR - H**  
**Explanation:** Due to the Mic-1's ALU design, subtraction order matters. H = MDR - H cannot be encoded because the ALU can only compute A - B where A comes from the B bus. You can do H - MDR but not MDR - H.

---

**19. What does the N bit in Mic-1 indicate?**
   - A) Next instruction ready
   - B) ALU result is negative
   - C) No operation needed
   - D) Null pointer detected

**Answer: B) ALU result is negative**  
**Explanation:** The N (Negative) bit is set when the ALU result is negative (most significant bit = 1). Used for conditional branching in microprograms.

---

**20. What does the Z bit in Mic-1 indicate?**
   - A) Zero division error
   - B) Zone memory access
   - C) ALU result is zero
   - D) Z register is full

**Answer: C) ALU result is zero**  
**Explanation:** The Z (Zero) bit is set when the ALU result equals zero (all bits = 0). Used alongside the N bit for conditional branching.

---

**21. RAW dependency stands for:**
   - A) Random Access Write
   - B) Read After Write
   - C) Register Allocation Window
   - D) Reconfigurable Arithmetic Wrapper

**Answer: B) Read After Write**  
**Explanation:** RAW (Read After Write) is a true data dependency where an instruction needs to read a value that a previous instruction will write. This cannot be eliminated.

---

**22. Which dependency can be eliminated by register renaming?**
   - A) RAW (Read After Write)
   - B) WAR (Write After Read)
   - C) True dependency
   - D) Data dependency

**Answer: B) WAR (Write After Read)**  
**Explanation:** WAR (Write After Read) and WAW (Write After Write) are false dependencies that can be eliminated by register renaming. RAW is a true dependency that cannot be eliminated.

---

**23. In instruction pipelining, a hazard occurs when:**
   - A) Pipeline is empty
   - B) Instructions cannot proceed due to dependencies
   - C) Cache is full
   - D) Interrupts are disabled

**Answer: B) Instructions cannot proceed due to dependencies**  
**Explanation:** A pipeline hazard (or stall) occurs when the next instruction cannot execute in the next clock cycle due to data dependencies, control flow changes, or resource conflicts.

---

**24. Register renaming helps with:**
   - A) True dependencies (RAW)
   - B) Anti-dependencies (WAR) and output dependencies (WAW)
   - C) Cache coherence
   - D) Virtual memory management

**Answer: B) Anti-dependencies (WAR) and output dependencies (WAW)**  
**Explanation:** Register renaming eliminates false dependencies (WAR and WAW) by mapping architectural registers to a larger set of physical registers. True dependencies (RAW) cannot be eliminated.

---

**25. Superscalar architecture allows:**
   - A) Multiple instructions to execute in parallel
   - B) Larger register files
   - C) Faster clock speeds
   - D) More cache memory

**Answer: A) Multiple instructions to execute in parallel**  
**Explanation:** Superscalar processors can issue and execute multiple instructions simultaneously in the same clock cycle, increasing instruction-level parallelism.

---

**26. Branch prediction is used to:**
   - A) Eliminate all pipeline stalls
   - B) Reduce pipeline stalls from conditional branches
   - C) Predict page faults
   - D) Optimize cache placement

**Answer: B) Reduce pipeline stalls from conditional branches**  
**Explanation:** Branch prediction guesses which way a conditional branch will go, allowing the pipeline to continue fetching instructions. Correct predictions avoid stalls; mispredictions require pipeline flushing.

---

**27. A static branch prediction strategy might be:**
   - A) Always take backward branches (loops)
   - B) Randomly guess
   - C) Never predict
   - D) Only predict in kernel mode

**Answer: A) Always take backward branches (loops)**  
**Explanation:** A simple static strategy is to predict backward branches as taken (since they're usually loops that iterate) and forward branches as not taken.

---

**28. Cache locality has two types:**
   - A) Fast and slow
   - B) Temporal and spatial
   - C) Direct and indirect
   - D) Local and global

**Answer: B) Temporal and spatial**  
**Explanation:** Temporal locality means recently accessed data will be accessed again soon. Spatial locality means data near recently accessed data will be accessed soon.

---

**29. Temporal locality means:**
   - A) Data accessed recently likely accessed again soon
   - B) Data near each other accessed together
   - C) Time-based access patterns
   - D) Temporary storage usage

**Answer: A) Data accessed recently likely accessed again soon**  
**Explanation:** Temporal locality is the principle that if data is accessed once, it's likely to be accessed again in the near future (e.g., loop variables).

---

**30. Spatial locality means:**
   - A) Data accessed recently likely accessed again
   - B) Data near recently accessed data likely accessed soon
   - C) Space-efficient storage
   - D) Spatial memory layout

**Answer: B) Data near recently accessed data likely accessed soon**  
**Explanation:** Spatial locality means that accessing data at one location suggests nearby data will be accessed soon (e.g., array elements processed sequentially).

---

## SECTION 3: ASSEMBLY & ISA (Questions 31-40)

**31. Which Intel instruction affects the stack pointer (SP)?**
   - A) MOV
   - B) ADD
   - C) PUSH
   - D) CMP

**Answer: C) PUSH**  
**Explanation:** PUSH, POP, CALL, and RET all modify the stack pointer. MOV, ADD, and CMP do not affect SP.

---

**32. Which Intel instruction does NOT affect the stack pointer?**
   - A) CALL
   - B) RET
   - C) POP
   - D) TEST

**Answer: D) TEST**  
**Explanation:** TEST performs a logical AND and sets flags but doesn't modify any registers including SP. CALL, RET, and POP all modify the stack pointer.

---

**33. The largest page size in Intel IA-32 architecture is:**
   - A) 4 KB
   - B) 2 MB
   - C) 4 MB
   - D) 1 GB

**Answer: C) 4 MB (4 MiB)**  
**Explanation:** IA-32 supports page sizes of 4KB (standard) and 4MB (large pages). The 4MB pages are useful for reducing TLB misses when accessing large memory regions.

---

**34. Sign extension is used to:**
   - A) Extend unsigned numbers
   - B) Copy sign bit when expanding signed numbers
   - C) Add signatures to code
   - D) Extend execution time

**Answer: B) Copy sign bit when expanding signed numbers**  
**Explanation:** Sign extension preserves the value of a signed number when converting to a larger bit width by copying the sign bit (MSB) to all new higher-order bits.

---

**35. In 8088, a segment register is:**
   - A) 8 bits wide
   - B) 16 bits wide
   - C) 32 bits wide
   - D) 64 bits wide

**Answer: B) 16 bits wide**  
**Explanation:** In the 8088/8086 architecture, segment registers (CS, DS, SS, ES) are 16 bits wide. They're shifted left 4 bits and added to a 16-bit offset to form a 20-bit physical address.

---

**36. Little endian byte ordering means:**
   - A) Most significant byte at lowest address
   - B) Least significant byte at lowest address
   - C) Random byte ordering
   - D) No specific byte order

**Answer: B) Least significant byte at lowest address**  
**Explanation:** In little endian systems (like x86), the least significant byte is stored at the lowest memory address. For example, 0x12345678 is stored as 78 56 34 12.

---

**37. An immediate operand is:**
   - A) A constant value in the instruction
   - B) A memory address
   - C) A register name
   - D) An I/O port

**Answer: A) A constant value in the instruction**  
**Explanation:** An immediate operand is a constant value encoded directly in the instruction itself, like MOV AX, 5 where 5 is the immediate operand.

---

**38. Register indirect addressing uses:**
   - A) Register contains the data
   - B) Register contains address of data
   - C) Register contains instruction
   - D) Two registers for calculation

**Answer: B) Register contains address of data**  
**Explanation:** In register indirect addressing, the register holds a memory address, and the processor uses that address to access the actual data. Example: MOV AX, [BX].

---

**39. RISC design principles include:**
   - A) Complex instruction set
   - B) Many addressing modes
   - C) Load/store architecture with simple instructions
   - D) Microprogrammed control

**Answer: C) Load/store architecture with simple instructions**  
**Explanation:** RISC (Reduced Instruction Set Computer) principles include simple instructions, load/store architecture (only load/store access memory), and hardwired control rather than microcode.

---

**40. CISC processors typically have:**
   - A) Very few instructions
   - B) Only load/store operations
   - C) Many complex instructions with many addressing modes
   - D) No cache memory

**Answer: C) Many complex instructions with many addressing modes**  
**Explanation:** CISC (Complex Instruction Set Computer) processors have large instruction sets with complex operations and multiple addressing modes, often implemented with microcode.

---

## SECTION 4: FILE SYSTEMS & I/O (Questions 41-50)

**41. FAT (File Allocation Table) is:**
   - A) A type of RAM
   - B) A file system using a table to track block chains
   - C) A cache algorithm
   - D) A page replacement strategy

**Answer: B) A file system using a table to track block chains**  
**Explanation:** FAT uses a table where each entry corresponds to a disk block. Each entry points to the next block in the file, forming a linked list or chain.

---

**42. In Linux, an inode contains:**
   - A) File data
   - B) File metadata and pointers to data blocks
   - C) Directory listing
   - D) User passwords

**Answer: B) File metadata and pointers to data blocks**  
**Explanation:** An inode stores file metadata (size, permissions, timestamps) and pointers to data blocks (direct, indirect, double indirect, triple indirect). The actual file data is in the data blocks.

---

**43. Why are hard links to directories typically prohibited?**
   - A) They're too slow
   - B) They waste space
   - C) They can create cycles making garbage collection impossible
   - D) They require too much memory

**Answer: C) They can create cycles making garbage collection impossible**  
**Explanation:** Hard links to directories could create cycles in the directory tree, making it impossible to determine when a directory can be deleted and causing infinite loops in directory traversal.

---

**44. Unix inodes use multi-level indexing with:**
   - A) Only direct pointers
   - B) Direct, single indirect, double indirect, triple indirect
   - C) Only indirect pointers
   - D) Random access pointers

**Answer: B) Direct, single indirect, double indirect, triple indirect**  
**Explanation:** Unix inodes typically have 10-12 direct pointers, plus single indirect, double indirect, and triple indirect pointers. This allows efficient access for both small and large files.

---

**45. Compared to FAT, inodes are:**
   - A) Slower for all file sizes
   - B) Better for large files due to multi-level indexing
   - C) Simpler to implement
   - D) Can only handle small files

**Answer: B) Better for large files due to multi-level indexing**  
**Explanation:** Inodes use multi-level indexing which scales well to large files without wasting space for small files. FAT requires traversing a chain which is slow for large files.

---

**46. Bus skew refers to:**
   - A) Bent bus connectors
   - B) Time difference in signal arrival due to varying wire lengths
   - C) Bus bandwidth limitation
   - D) Bus protocol errors

**Answer: B) Time difference in signal arrival due to varying wire lengths**  
**Explanation:** Bus skew occurs when signals on different bus lines arrive at different times because some wires are longer than others, causing timing issues.

---

**47. DMA (Direct Memory Access) allows:**
   - A) CPU to access disk directly
   - B) I/O devices to transfer data without CPU intervention
   - C) Direct access to virtual memory
   - D) Faster cache access

**Answer: B) I/O devices to transfer data without CPU intervention**  
**Explanation:** DMA allows I/O devices to transfer data directly to/from memory without involving the CPU for each byte, freeing the CPU for other tasks.

---

**48. A multiplexed bus:**
   - A) Connects multiple computers
   - B) Uses same wires for address and data at different times
   - C) Only works with specific devices
   - D) Requires special software

**Answer: B) Uses same wires for address and data at different times**  
**Explanation:** A multiplexed bus time-shares the same physical wires for both address and data signals, reducing the number of pins needed but requiring multiple bus cycles.

---

**49. In a write-back cache:**
   - A) Data written immediately to main memory
   - B) Data written to cache only, main memory updated later
   - C) Cache is never written
   - D) All writes bypass cache

**Answer: B) Data written to cache only, main memory updated later**  
**Explanation:** Write-back (also called write-deferred) caches write data to the cache first and update main memory only when the cache line is evicted. This is faster but requires coherence protocols.

---

**50. Cache coherence is a problem in:**
   - A) Single processor systems
   - B) Multiprocessor systems with multiple caches
   - C) Systems without cache
   - D) Virtual memory systems

**Answer: B) Multiprocessor systems with multiple caches**  
**Explanation:** When multiple processors each have their own cache, keeping all caches consistent (coherent) becomes a challenge. Protocols like MESI ensure all caches see the same values.

---

---

# 📊 SCORING GUIDE

Count your correct answers:

**45-50 correct (90-100%)**: Excellent! You're very well prepared.  
**40-44 correct (80-89%)**: Great! You're on track for a strong performance.  
**35-39 correct (70-79%)**: Good! Review topics you missed.  
**30-34 correct (60-69%)**: Passing territory. Focus on weak areas.  
**25-29 correct (50-59%)**: Target achieved! Keep reviewing.  
**Below 25 (below 50%)**: Study the missed topics urgently!

---

# 🎯 TOPICS TO REVIEW BASED ON WRONG ANSWERS

**If you missed questions 1-15 (Memory Management):**
- Review page replacement algorithms (LRU, FIFO)
- Study Belady's Anomaly
- Understand fragmentation types (internal vs external)
- Learn TLB operation and purpose
- Practice demand paging concepts

**If you missed questions 16-30 (Processor & Microarchitecture):**
- Study Mic-1 architecture and registers (TOS, H, SP, etc.)
- Learn pipeline dependencies (RAW, WAR, WAW)
- Understand register renaming benefits
- Review cache locality principles (temporal and spatial)
- Study branch prediction strategies

**If you missed questions 31-40 (Assembly/ISA):**
- Memorize Intel stack pointer instructions (PUSH, POP, CALL, RET)
- Learn addressing modes (immediate, register indirect)
- Understand RISC vs CISC differences
- Review byte ordering (little endian vs big endian)
- Study sign extension

**If you missed questions 41-50 (File Systems/I/O):**
- Compare FAT vs inodes thoroughly
- Understand Unix file system structure (direct/indirect pointers)
- Learn why hard links to directories are prohibited
- Study bus concepts (skew, multiplexing)
- Review cache write policies (write-back vs write-through)

---

# 💡 STUDY TIPS

1. **Focus on weak areas**: Identify topics where you got questions wrong and review those sections in ULTIMATE_CRAM_SHEET.md
2. **Retake the quiz**: Try the quiz again after studying to measure improvement
3. **Time yourself**: Practice answering in under 1 minute per question
4. **Understand, don't memorize**: Make sure you understand the explanations, not just the answers
5. **Use existing materials**: Refer to PRACTICE_PROBLEMS.md for worked examples on topics you're struggling with

---

# 🚀 NEXT STEPS

1. **Calculate your score** from the 50 questions above
2. **Review explanations** for questions you got wrong
3. **Study weak topics** using ULTIMATE_CRAM_SHEET.md
4. **Retake quiz** tomorrow and aim for 40+/50
5. **Practice calculations** for page replacement and ALU problems

---

**Remember: Understanding why answers are correct is more important than memorizing them!**

**Good luck with your exam preparation! 🍀💪📚**

---

*Created from CS 244 past paper analysis (2011-2022) - Optimized for quick learning and retention*
