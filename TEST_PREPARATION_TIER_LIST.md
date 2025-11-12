# Test Preparation Tier List - Computer Science 244
## Based on Past Papers Analysis (2011-2022)

**Examination Date:** 2 days from now  
**Analysis Date:** November 12, 2025  
**Examiner:** Willem Bester (all recent papers: 2012-2022)

---

## 📊 Methodology

This tier list is based on:
- **Recency Weight:** Most recent papers (2022, 2019, 2018) have highest priority
- **Examiner Credibility:** Papers by Willem Bester (2012-2022) weighted higher than others
- **Frequency:** How often a topic appears across all papers
- **Combined Score:** Weighted sum considering all factors above

Papers analyzed: **12 total** (2011-2022)
- **High credibility (Willem):** 2012-2022 (11 papers)
- **Lower credibility (Other):** 2011 (1 paper)

---

## 🔴 **TIER S - NEED TO KNOW** (Weight: 45-57)
### These topics appear constantly, especially in recent Willem papers. You MUST master these.

### 1. **Page Replacement Algorithms (LRU/FIFO)** - Weight: 57
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2014, 2013, 2012 (9/11 Willem papers)
- **What to know:**
  - Calculate page faults for given page reference sequences
  - LRU (Least Recently Used) algorithm
  - FIFO (First In First Out) algorithm
  - Work through examples with 3 and 4 frames
  - Show your calculations in boxes/tables

### 2. **Paging System** - Weight: 57
- **Appears in:** All recent papers
- **What to know:**
  - Page tables and page faults
  - Frame allocation
  - Memory addressing with paging
  - Difference from segmentation

### 3. **Translation Lookaside Buffer (TLB)** - Weight: 52
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2014, 2013, 2012
- **What to know:**
  - What it is and how it operates
  - Purpose: speed up virtual-to-physical address translation
  - Briefly describe its operation (short answer)

### 4. **FAT vs. Linux inodes** - Weight: 52
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2014, 2013
- **What to know:**
  - Compare and contrast allocation strategies
  - Discuss file size implications
  - Access time considerations
  - Fragmentation differences
  - This is often a 6-mark question!

### 5. **Fragmentation (Internal & External)** - Weight: 52
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2014, 2013
- **What to know:**
  - Define internal fragmentation (1 sentence)
  - Define external fragmentation (1 sentence)
  - Context: memory allocation, paging vs segmentation

### 6. **Belady's Anomaly** - Weight: 52
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2014, 2013 (8 papers)
- **What to know:**
  - Define the anomaly
  - Illustrate with your page replacement calculations
  - Usually asked after LRU/FIFO calculations with different frame counts
  - Shows that more frames can sometimes lead to MORE page faults (counterintuitive!)

### 7. **Thrashing** - Weight: 52
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2014, 2013 (8 papers)
- **What to know:**
  - Define what thrashing is (brief)
  - Give example of circumstances where it can occur
  - Related to insufficient memory/too many processes

### 8. **Bus Design/Bus Skew** - Weight: 51
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2014, 2012
- **What to know:**
  - Define bus skew in one sentence
  - Intel Core architecture bus design
  - How to accommodate fast and slow components
  - System bus layout considerations

### 9. **Intel Instructions & Stack Pointer** - Weight: 51
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2013, 2012, 2011 (9 papers)
- **What to know:**
  - Which instructions affect stack pointer: call, push, pop, ret
  - Which DON'T affect it: cmp, test
  - Common short answer question (1 mark)

---

## 🟠 **TIER A - HIGH PRIORITY** (Weight: 43-47)

### 10. **Mic-1 Registers (TOS, CPP, LV, SP, MDR, H)** - Weight: 47
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2012
- **What to know:**
  - TOS: Top of Stack (always keeps stack top value)
  - SP: Stack Pointer
  - LV: Local Variable pointer
  - CPP: Constant Pool Pointer
  - MDR: Memory Data Register
  - H: Holding register (used in ALU operations)

### 11. **Pipeline Dependencies (RAW, WAR, WAW)** - Weight: 47
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015, 2012
- **What to know:**
  - **RAW** (Read After Write): "true dependencies"
  - **WAR** (Write After Read): can be mitigated
  - **WAW** (Write After Write): can be mitigated
  - How to mitigate WAR and WAW (register renaming!)
  - Identify dependency type in given instruction sequences
  - Common example: R1 = R2 * R3; R4 = R5 + R1 (RAW dependency)

### 12. **Cache Memory & Locality Principles** - Weight: 46
- **Appears in:** 2022, 2019, 2017, 2016, 2015, 2014, 2013, 2012
- **What to know:**
  - Temporal locality: recently used data will be used again
  - Spatial locality: nearby data will be used
  - Motivate why cache is useful
  - Discuss with respect to locality principles

### 13. **Segmentation vs. Paging** - Weight: 46
- **Appears in:** 2022, 2019, 2018, 2016, 2015, 2014, 2013, 2011
- **What to know:**
  - Conceptual differences
  - Segmentation faults vs page faults (from programmer's perspective)
  - Fragmentation in each system
  - Brief discussion question (3-4 marks)

### 14. **ALU/RLE Operations** - Weight: 45
- **Appears in:** 2022, 2018, 2017, 2016, 2015, 2014, 2013, 2012
- **What to know:**
  - 1-bit ALU circuit diagram
  - Control signals: F0, F1, ena, enb, inva, inc
  - Calculate functions: A+B, A+B+1, B-A, -A
  - Fill in truth table (4 marks typically)
  - **How to calculate B-A:** Use two's complement (invert A, add 1)

### 15. **Second-Chance Page Replacement** - Weight: 45
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015
- **What to know:**
  - Uses reference bit and modify bit
  - Page classes: (0,0), (0,1), (1,0), (1,1)
  - **Which to evict first?** (0,0) - not referenced, not modified
  - Common 1-mark multiple choice question

### 16. **Proportional Allocation Scheme** - Weight: 45
- **Appears in:** 2022, 2019, 2018, 2017, 2016, 2015
- **What to know:**
  - Standard problem: 62 frames, two processes (10 pages and 127 pages)
  - Formula: frames_for_process = (process_pages / total_pages) × total_frames
  - Large process gets: (127/137) × 62 = 57 frames
  - Common 1-mark question

### 17. **Mic-4 Pipelining** - Weight: 43
- **Appears in:** 2022, 2019, 2018, 2017, 2014, 2013, 2012
- **What to know:**
  - Why 4 Memory Instruction Registers (MIRs) are needed
  - Pipelining the Mic-1 architecture
  - Reference to datapath, control store, registers
  - Original subcycles in Mic-1

### 18. **Unix File System Details** - Weight: 43
- **Appears in:** 2019, 2018, 2017, 2016, 2015, 2014, 2013, 2011
- **What to know:**
  - Index blocks (inodes) strategy for large file ranges
  - Why hard links to directories are NOT allowed
  - Direct, indirect, double indirect, triple indirect pointers
  - Graph directory structure

---

## 🟡 **TIER B - MEDIUM PRIORITY** (Weight: 22-32)

### 19. **Multiplexer** - Weight: 32
- **Appears in:** 2022, 2018, 2017, 2015, 2012
- **What to know:**
  - Draw 2-input multiplexer circuit diagram
  - Wire inputs (A, B, VGnd, VCC) to compute: A, AB, A+B
  - Control line C chooses between D0 and D1

### 20. **SR Latch/Flip-flop** - Weight: 30
- **Appears in:** 2022, 2018, 2017, 2016, 2015, 2012
- **What to know:**
  - Draw SR latch circuit diagram
  - Explain inconsistency leading to nondeterminism
  - Difference between latch and flip-flop
  - D latches are always deterministic (unlike SR)

### 21. **Mic-1 Control Store & Branching** - Weight: 28
- **Appears in:** 2022, 2019, 2014, 2013, 2012
- **What to know:**
  - Control store contains offsets T and F
  - Branching based on N or Z latch (1 → T, 0 → F)
  - Microinstruction branching

### 22. **Copy-on-Write** - Weight: 26
- **Appears in:** 2019, 2017, 2016, 2014
- **What to know:**
  - Define in one sentence
  - Memory optimization technique
  - Used in process forking

### 23. **Segment Registers (Intel)** - Weight: 25
- **Appears in:** 2022, 2015, 2014, 2013, 2012, 2011
- **What to know:**
  - Width: 16 bits
  - Types: CS, DS, SS, ES (not DI - that's a general purpose register)

### 24. **Sign Extension** - Weight: 25
- **Appears in:** 2019, 2017, 2015, 2014
- **What to know:**
  - Define in one sentence
  - Extending 8-bit to 32-bit values
  - Signed vs unsigned numbers

### 25. **Demand Paging** - Weight: 25
- **Appears in:** 2019, 2017, 2015, 2013, 2011
- **What to know:**
  - Full explanation required
  - How it's same/different from cache memory
  - Pages loaded only when needed (on demand)

### 26. **Unified Cache** - Weight: 24
- **Appears in:** 2019, 2017, 2015, 2013
- **What to know:**
  - Define in one sentence
  - Single cache for both instructions and data
  - vs. split cache (separate I-cache and D-cache)

### 27. **Mic-1 Datapath & Subcycles** - Weight: 22
- **Appears in:** 2022, 2019, 2013
- **What to know:**
  - Four subcycles of datapath cycle
  - Describe pointwise what happens in each
  - Microarchitecture operation

### 28. **Branch Prediction** - Weight: 22
- **Appears in:** 2022, 2019, 2013
- **What to know:**
  - Static strategy: take backward jumps, skip forward jumps
  - Why? Loops (backward) usually taken, if-statements (forward) less predictable
  - Is this a good strategy? (with reference to high-level language control flow)

### 29. **Associative Cache Memory** - Weight: 22
- **Appears in:** 2022, 2016, 2014, 2012
- **What to know:**
  - Define and discuss merits
  - How it works (content-addressable)
  - Fully associative vs set-associative

### 30. **Register Renaming** - Weight: 22
- **Appears in:** 2019, 2017, 2016
- **What to know:**
  - Define in one sentence
  - Used to eliminate WAR and WAW dependencies
  - Hardware maintains mapping of architectural to physical registers

### 31. **Memory Allocation (First-fit/Best-fit)** - Weight: 22
- **Appears in:** 2017, 2015, 2014, 2013, 2012, 2011
- **What to know:**
  - Given partitions (e.g., 100K, 500K, 200K, 300K, 600K)
  - Place processes (e.g., 212K, 417K, 112K, 426K)
  - Circular list approach
  - Calculate which partition for each process

---

## 🟢 **TIER C - POTENTIALLY IN PAPER** (Weight: 15-20)

### 32. **Assembly Data Types** - Weight: 20
- **Appears in:** 2022, 2014, 2013, 2012, 2011
- **What to know:**
  - Critical discussion: "There are no data types in assembly language"
  - Actually, there ARE types at instruction level
  - Different instructions for different sizes/operations

### 33. **Mic-1 N and Z bits** - Weight: 17
- **Appears in:** 2017, 2016, 2014
- **What to know:**
  - How they're wired
  - Involved with branching on microinstruction level
  - Z=1 when ALU result is zero
  - N=1 when result is negative

### 34. **cdecl Calling Convention** - Weight: 17
- **Appears in:** 2017, 2014, 2013, 2012, 2011
- **What to know:**
  - Pointwise what happens when function called
  - Caller pushes arguments right-to-left
  - Caller calls function
  - Callee saves old base pointer
  - Callee allocates space for local variables
  - Function executes
  - Callee cleans up
  - Caller cleans up arguments

### 35. **Adders (Ripple Carry vs Carry Select)** - Weight: 15
- **Appears in:** 2018, 2017
- **What to know:**
  - Ripple carry: simple, slow (carry propagates)
  - Carry select: faster, more hardware
  - General principle: time-space tradeoff

### 36. **Intel IA-32 Specifics** - Weight: 15
- **Appears in:** 2015, 2014, 2013, 2012, 2011
- **What to know:**
  - Page sizes: 4 KiB typical, 4 MiB maximum
  - 32-bit architecture details

### 37. **Relocatable Code** - Weight: 13
- **Appears in:** 2016, 2014, 2013
- **What to know:**
  - Define in one sentence
  - Code that can be loaded at different memory addresses

---

## 🔵 **TIER D - LOWER PRIORITY** (Weight: 6-9)

### 38. **Cache Write Policies** - Weight: 9
- **Appears in:** 2014, 2013, 2012
- **What to know:**
  - Write back: write to cache, update memory later
  - Write through: write to both cache and memory
  - Write allocate: load into cache on write miss

### 39. **Speculative Execution** - Weight: 8
- **Appears in:** 2016, 2012
- **What to know:**
  - Brief example of catastrophic consequences
  - Hardware protection needed (Spectre/Meltdown vulnerabilities)

### 40. **Dynamic Linking/Loading** - Weight: 6
- **Appears in:** 2016 only
- **What to know:**
  - Difference between dynamic linking and dynamic loading
  - Linking: resolving symbols at load time
  - Loading: loading code on demand

### 41. **Volatile Memory** - Weight: 6
- **Appears in:** 2016 only
- **What to know:**
  - Define in one sentence
  - Loses contents when power is off (RAM)

---

## 📝 **Key Question Types You'll See**

### Short Questions (1 mark each)
- Multiple choice on Intel instructions, stack pointer effects
- Multiple choice on Mic-1 registers and microcode limitations
- Multiple choice on proportional allocation (62 frames problem)
- Multiple choice on second-chance algorithm page classes
- Multiple choice on pipeline dependencies (RAW/WAR/WAW)

### Definitions (1 mark each)
- Bus skew
- Sign extension
- Unified cache
- Register renaming
- Internal/external fragmentation
- Copy-on-write

### Calculations (4-5 marks)
- Page replacement with LRU and FIFO (3-4 frames)
- Belady's anomaly demonstration
- ALU control signal table
- Memory allocation (first-fit/best-fit)

### Long Questions (3-6 marks each)
- Explain thrashing (brief)
- TLB operation (brief)
- FAT vs inodes (6 marks - detailed!)
- Segmentation vs paging
- Pipeline dependencies and mitigation
- Cache memory and locality principles
- Unix file system strategy
- Branch prediction strategy evaluation

---

## 🎯 **Study Strategy for Next 2 Days**

### Day 1 (Today)
**Focus on TIER S (Need to Know):**
1. Practice page replacement algorithms (LRU/FIFO) - do 5-10 examples
2. Memorize TLB, thrashing, Belady's anomaly definitions
3. Study FAT vs inodes comparison thoroughly (this is 6 marks!)
4. Review fragmentation types
5. Memorize second-chance algorithm page classes
6. Practice proportional allocation calculation
7. Know which Intel instructions affect stack pointer

### Day 2 (Tomorrow)
**Morning - TIER A (High Priority):**
1. Mic-1 registers and their purposes
2. Pipeline dependencies (RAW, WAR, WAW) with examples
3. Cache memory and locality principles
4. ALU operations - practice the truth table
5. Segmentation vs paging discussion

**Afternoon - TIER B (Medium Priority):**
1. Multiplexer wiring problems
2. SR latch vs D latch
3. Sign extension, bus skew, unified cache definitions
4. Demand paging explanation
5. Branch prediction strategy

**Evening - Quick Review:**
1. Skim TIER C topics
2. Review all 1-sentence definitions
3. Practice one more set of page replacement calculations
4. Rest well!

---

## 🚨 **Critical Formulas & Facts to Memorize**

1. **Proportional Allocation:** frames = (process_pages / total_pages) × total_frames
2. **Second-Chance Eviction Order:** (0,0) → (0,1) → (1,0) → (1,1)
3. **Intel Segment Registers:** 16 bits wide
4. **Mic-1 Stack Top Register:** TOS (Top of Stack)
5. **B - A calculation in ALU:** Invert A (inva=1), add 1 (inc=1), add B
6. **RAW = "True" dependencies** (cannot be eliminated)
7. **Belady's Anomaly:** More frames can cause more page faults (FIFO)

---

## 📚 **Good Luck!**

Remember:
- **Willem Bester sets the paper** - focus on his patterns (2012-2022)
- **Recent papers (2022, 2019, 2018) are most predictive**
- **Page replacement, memory management, and Mic-1 are HUGE topics**
- **Show your work on calculations** - partial credit is available
- **Know your 1-sentence definitions** - these are free marks
- **The 6-mark FAT vs inodes question appears frequently** - prepare it well!

*Generated from analysis of 12 past papers (2011-2022)*
