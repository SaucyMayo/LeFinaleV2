# 🚨 ULTIMATE 4-HOUR CRAM SHEET - CS 244 🚨

**Target: 50% Pass | Time: 4 Hours | Focus: High-frequency topics**

---

## ⚡ TOP 10 DEFINITIONS (1 mark each - FREE POINTS!)

1. **Bus Skew**: Time difference when signal arrives at different components due to varying wire lengths
2. **Thrashing**: System spends more time paging than executing due to insufficient memory
3. **Internal Fragmentation**: Wasted space within allocated block not used by process
4. **External Fragmentation**: Wasted space between blocks; total free memory sufficient but not contiguous
5. **TLB**: Translation Lookaside Buffer - cache for virtual-to-physical address mappings
6. **Belady's Anomaly**: Increasing frames can increase page faults (only FIFO, not LRU)
7. **Register Renaming**: Maps architectural registers to physical registers to eliminate false dependencies
8. **Cache Locality**: Temporal (reuse recent data) + Spatial (use nearby data)
9. **RAW Dependency**: Read After Write - true dependency that cannot be eliminated
10. **Sign Extension**: Extending smaller signed value by copying sign bit to higher bits

---

## 📊 INSTANT MCQ ANSWERS

### Intel Stack Pointer
**Affects it:** CALL, PUSH, POP, RET  
**Doesn't affect it:** CMP, TEST ✓

### Proportional Allocation (62 frames, 10 & 127 pages)
**Answer:** (127/137) × 62 = **57 frames** ✓

### Second-Chance Page Classes (Order to Evict)
**(0,0) → (0,1) → (1,0) → (1,1)**  
Evict **(0,0)** first ✓

### Pipeline Dependency: R1=R2*R3; R4=R5+R1
**Type:** RAW (Read After Write) ✓

### Mic-1 Cannot Encode
**Answer:** H = MDR - H ✓  
(Can do: H=H-MDR, H=H+MDR, H=MDR+H)

### Largest Intel IA-32 Page Size
**Answer:** 4 MiB ✓

---

## 🎯 ALU CONTROL SIGNALS (4 marks - MEMORIZE!)

| Function | F0 | F1 | ena | enb | inva | inc |
|----------|----|----|-----|-----|------|-----|
| **A + B**    | 1  | 1  | 1   | 1   | 0    | 0   |
| **A + B + 1**| 1  | 1  | 1   | 1   | 0    | 1   |
| **B - A**    | 1  | 1  | 1   | 1   | 1    | 1   |
| **-A**       | 1  | 1  | 1   | 0   | 1    | 1   |

**Key Insight:** B-A = B + (-A) = B + (NOT A + 1) → invert A and add 1

---

## 📝 PAGE REPLACEMENT (9 marks - PRACTICE!)

### LRU Quick Method
1. Track "last used" time for each page
2. Evict page with **oldest** last-used time
3. Update last-used time on every reference

### FIFO Quick Method
1. Track "arrival" time for each page
2. Evict **oldest** page in memory (first in, first out)
3. Can suffer Belady's Anomaly!

### Example Problem Pattern (3 frames)
```
Reference: 1  2  3  4  1  2  5
Frame 1:   1  1  1  4  4  4  4
Frame 2:      2  2  2  1  1  1
Frame 3:         3  3  3  2  5
Fault?     ✓  ✓  ✓  ✓  ✓  ✓  ✓
```
**Count the ✓ marks = total faults**

---

## 🔧 MULTIPLEXER WIRING (2-3 marks)

| Function | D0  | D1  | C   |
|----------|-----|-----|-----|
| **A**        | A   | A   | X   |
| **A + B**    | A   | B   | B   |
| **AB**       | GND | A   | B   |

*X = don't care*

---

## 💾 FAT vs INODES (6 marks - BIG QUESTION!)

### FAT Pros/Cons
**Pros:** Simple, good for small files  
**Cons:** Fixed table size, slow for large files (chain traversal), external fragmentation, no redundancy

### Inodes Pros/Cons
**Pros:** Direct+indirect pointers, fast small files, scales to large files, efficient space  
**Cons:** More complex, small overhead for tiny files

**Strategy for Large Files:** Multi-level indexing (direct → single indirect → double → triple)

**Why No Hard Links to Directories?** Creates cycles → impossible garbage collection → infinite loops

---

## 🔄 PIPELINE DEPENDENCIES

| Type | Name | Example | Eliminable? |
|------|------|---------|-------------|
| **RAW** | Read After Write | R1=R2+R3; R4=R1+R5 | ❌ (use forwarding) |
| **WAR** | Write After Read | R1=R2+R3; R2=R4+R5 | ✅ (register rename) |
| **WAW** | Write After Write | R1=R2+R3; R1=R4+R5 | ✅ (register rename) |

**RAW = TRUE dependency** (most common in exams!)

---

## 🏗️ MIC-1 ESSENTIALS

### Key Registers
- **TOS**: Top Of Stack (always holds stack top)
- **CPP**: Constant Pool Pointer
- **LV**: Local Variables pointer
- **SP**: Stack Pointer
- **MDR**: Memory Data Register
- **H**: Holding register (for ALU ops)

### Four Subcycles
1. Put address on bus → start read
2. Wait for memory
3. Data arrives in MDR
4. ALU operates → write back

### N & Z Bits
- **N**: Set if ALU result negative (MSB=1)
- **Z**: Set if ALU result zero (all bits=0)
- Used for conditional branching

---

## 🔐 SEGMENTATION vs PAGING

| Aspect | Segmentation | Paging |
|--------|--------------|--------|
| **Concept** | Logical divisions | Fixed-size blocks |
| **Size** | Variable | Fixed (4KB) |
| **View** | Visible to programmer | Transparent |
| **Fragmentation** | External | Internal |
| **Fault** | Seg fault (protection) | Page fault (demand) |

---

## 📐 ESSENTIAL FORMULAS

### Proportional Allocation
```
frames_for_process = (process_pages / total_pages) × total_frames
```

### TLB Operation Time
```
Effective_Access_Time = hit_rate × fast_time + (1-hit_rate) × slow_time
```

---

## ⚠️ COMMON MISTAKES - AVOID THESE!

1. ❌ Forgetting initial page faults (all frames start EMPTY!)
2. ❌ Not showing work on calculations → no partial credit
3. ❌ Writing paragraphs for "one sentence" questions
4. ❌ Mixing up RAW/WAR/WAW (RAW = true dependency)
5. ❌ Not using provided boxes for page replacement
6. ❌ Spending 20 min on 1-mark question
7. ❌ Leaving questions blank → ALWAYS write something!

---

## 🎯 4-HOUR STUDY PLAN

### Hour 1: Definitions & MCQs (25 marks potential)
- [ ] Memorize all 10 one-liners above
- [ ] Do 30 MCQ practice questions
- [ ] Review instant answers section

### Hour 2: Page Replacement (9 marks potential)
- [ ] Practice 5 LRU problems
- [ ] Practice 5 FIFO problems  
- [ ] Demonstrate Belady's Anomaly once
- [ ] Must complete each in under 5 minutes!

### Hour 3: ALU + Mic-1 (8 marks potential)
- [ ] Memorize ALU control signal table
- [ ] Practice 3 ALU problems
- [ ] Review Mic-1 registers and operations
- [ ] Understand N and Z bits

### Hour 4: FAT vs Inodes + Final Review (10 marks potential)
- [ ] Write out FAT vs inodes comparison twice
- [ ] Practice Unix file system questions
- [ ] Review all definitions one more time
- [ ] Quick scan of pipeline dependencies

**Total Realistic Target: 52+ marks (65%)**

---

## 🚨 EXAM DAY STRATEGY

### First 30 Minutes: Easy Points
1. All MCQs (5-7 marks)
2. All one-sentence definitions (5-7 marks)
3. Anything you recognize immediately

### Next 60 Minutes: Calculations
1. Page replacement (9 marks)
2. ALU control signals (4 marks)
3. Proportional allocation (2 marks)

### Final 90 Minutes: Long Answers
1. FAT vs inodes (6 marks)
2. File system questions (4-6 marks)
3. Pipeline dependencies (3-4 marks)
4. Remaining questions

### Last 15 Minutes: Review
- Check all calculations
- Ensure you answered every question
- Verify you showed work

---

## 💡 FINAL TIPS

1. **Write in INK** (pencil = no mark queries!)
2. **Show ALL work** on calculations (partial credit exists!)
3. **Use provided boxes** for page replacement work
4. **Read "one sentence" literally** - don't write paragraphs
5. **Budget time**: 80 marks in 3 hours = ~2.25 min/mark
6. **Never leave blank** - educated guess gets partial credit
7. **Check units** - frames, pages, bytes, etc.

---

## ✅ YOU'RE READY WHEN YOU CAN:

- [ ] Define all 10 terms without looking (1 min)
- [ ] Complete LRU/FIFO calculation (5 min)
- [ ] Fill ALU table from memory (2 min)
- [ ] Explain FAT vs inodes comprehensively (5 min)
- [ ] Identify RAW/WAR/WAW in code (30 sec)
- [ ] List Intel stack pointer instructions (30 sec)
- [ ] Calculate proportional allocation (1 min)
- [ ] Wire a multiplexer for A, AB, A+B (2 min)

---

## 🏆 CONFIDENCE BOOSTER

**Past Paper Patterns:** Willem Bester (2012-2022) repeats questions with minor variations!

**Most Common Topics:**
1. Page replacement (appears in 9/11 papers)
2. FAT vs inodes (appears in 8/11 papers)
3. ALU control signals (appears in 7/11 papers)
4. Pipeline dependencies (appears in 6/11 papers)

**If you master the above 4 topics = guaranteed 50%+**

---

## 🎊 GOOD LUCK!

**Remember:** You don't need perfection, you need 50%. Focus on high-frequency topics, show your work, and don't leave anything blank!

**You got this! 💪🔥📚**

---

*Based on analysis of CS 244 past papers (2011-2022) by Willem Bester*  
*Last updated: Right now, for YOUR exam!*
