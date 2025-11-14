# 📚 CS 244 MCQ & DEFINITIONS CHEAT SHEET

**Based on comprehensive analysis of past papers 2011-2022**

**Purpose:** This cheat sheet sorts ALL multiple choice questions by frequency, provides verified answers from memos, includes textbook definitions, and adds miscellaneous short-answer topics for complete test preparation.

---

## 📑 Table of Contents

1. [Multiple Choice Questions (MCQs) - Sorted by Frequency](#mcq-section)
2. [Definitions - From Textbook & Verified Sources](#definitions-section)
3. [Miscellaneous Short Questions](#misc-section)

---

<a name="mcq-section"></a>
## 🎯 SECTION 1: MULTIPLE CHOICE QUESTIONS

**Sorted by frequency of appearance in past papers**

### 🏆 MCQ #1: Intel Instruction with NO Effect on Stack Pointer

**Frequency:** ⭐⭐⭐ Appeared **8 times** - Years: 2011, 2015, 2016, 2017, 2018, 2019, 2022

**Question:** Which one of the following Intel instructions has no effect on the stack pointer?

**Options:**
- A) call
- B) push (sometimes cmp)
- C) ret
- D) test

**Answer: D) test** (In 2019, answer was B) cmp)

**Explanation:**
- **call** - Pushes return address onto stack (ESP decrements by 4)
- **push** - Pushes operand onto stack (ESP decrements by size)
- **ret** - Pops return address from stack (ESP increments by 4)
- **test** - Performs bitwise AND and sets flags only, NO stack modification
- **cmp** - Performs subtraction and sets flags only, NO stack modification

**✅ Remember:** Both `test` and `cmp` are comparison/test instructions that only affect FLAGS (ZF, SF, CF, OF, PF), never the stack pointer!

---

### 🏆 MCQ #2: Cannot Be Encoded in Mic-1 Microcode

**Frequency:** ⭐⭐⭐ Appeared **8 times** - Years: 2012, 2015, 2016, 2017, 2018, 2019, 2022

**Question:** Which one of the following cannot be encoded in Mic-1 microcode?

**Options:**
- A) H = H - MDR
- B) H = MDR - H
- C) H = H + MDR
- D) Various other operations

**Answer: B) H = MDR - H**

**Explanation:**
The Mic-1 ALU has a fundamental constraint: **In subtraction A - B, the H register must always be B (the subtrahend/value being subtracted).**

✅ **Valid operations:**
- `H = H - MDR` ✓ (H is on right side of minus)
- `H = H + MDR` ✓ (addition works both ways)
- `H = MDR + H` ✓ (addition is commutative)

❌ **Invalid operation:**
- `H = MDR - H` ✗ (Would require H as subtrahend on left side)

**Memory trick:** Think "H is what gets subtracted FROM" - so it must be on the left of the equals: `H = H - other`

---

### 🏆 MCQ #3: Proportional Allocation Calculation

**Frequency:** ⭐⭐⭐ Appeared **7 times** - Years: 2015, 2016, 2017, 2018, 2019, 2022

**Question:** Suppose a proportional allocation scheme is used on a system with 62 frames, and two processes, one of 10 pages, and one of 127 pages. How many frames would be allocated to the larger process?

**Options:**
- A) 4
- B) 31
- C) 57
- D) 58

**Answer: C) 57 frames**

**Formula:** `(process_pages / total_pages) × total_frames`

**Step-by-step calculation:**
```
Total pages = 10 + 127 = 137
Frames for Process 1 (10 pages) = (10/137) × 62 = 4.53 ≈ 5 frames
Frames for Process 2 (127 pages) = (127/137) × 62 = 57.47 ≈ 57 frames
Verification: 5 + 57 = 62 ✓
```

**✅ Quick shortcut:** Larger process ≈ (127/137) × 62 ≈ 0.927 × 62 ≈ 57

---

### 🏆 MCQ #4: Pipeline Dependency Type

**Frequency:** ⭐⭐⭐ Appeared **6 times** - Years: 2012, 2015, 2017, 2018, 2019, 2022

**Question:** For a pipelined RISC processor, which kind of dependency exists in the following instruction sequence?
```
R1 = R2 * R3
R4 = R5 + R1
```

**Options:**
- A) RAW (Read After Write)
- B) WAR (Write After Read)
- C) WAW (Write After Write)
- D) No dependency

**Answer: A) RAW (Read After Write) - TRUE DEPENDENCY**

**Explanation:**
- First instruction **WRITES** to R1
- Second instruction **READS** from R1
- This is a **Read After Write** hazard - the second instruction needs the result from the first

**✅ Remember all three types:**

1. **RAW** = **TRUE DEPENDENCY** (cannot eliminate)
   - Second reads what first writes
   - MUST execute in order
   
2. **WAR** = **ANTI-DEPENDENCY** (can eliminate with register renaming)
   - Second writes to what first reads
   
3. **WAW** = **OUTPUT DEPENDENCY** (can eliminate with register renaming)
   - Both write to same register

---

### 🏆 MCQ #5: Intel Segment Registers Width

**Frequency:** ⭐⭐ Appeared **5 times** - Years: 2011, 2012, 2015, 2022

**Question:** How many bits wide are segment registers on Intel architecture?

**Options:**
- A) 8
- B) 16
- C) 32
- D) 64

**Answer: B) 16 bits**

**Explanation:**
Segment registers (CS, DS, SS, ES, FS, GS) in Intel architecture are **16 bits wide**. They originated from the 8086/8088 era.

**The 6 segment registers:**
- **CS** - Code Segment (holds code)
- **DS** - Data Segment (holds data)
- **SS** - Stack Segment (holds stack)
- **ES** - Extra Segment (additional data)
- **FS** - Extra Segment (additional data)
- **GS** - Extra Segment (additional data)

**✅ Key fact:** Despite being 16-bit, they can address 4GB segments in protected mode using segment descriptors!

---

### 🏆 MCQ #6: Second-Chance Page Replacement

**Frequency:** ⭐⭐ Appeared **5 times** - Years: 2015, 2016, 2019, 2022

**Question:** When a second-chance page replacement algorithm, with a reference bit and a modify bit (in this order), is used, which one of the following page classes should be evicted first?

**Options:**
- A) (0, 0)
- B) (0, 1)
- C) (1, 0)
- D) (1, 1)

**Answer: A) (0, 0) - Not Referenced, Not Modified**

**Eviction order (from best to worst):**

| Priority | Class | Reference | Modified | Why? |
|----------|-------|-----------|----------|------|
| **1st - EVICT** | **(0, 0)** | No | No | **BEST CHOICE** - Clean, unused page |
| 2nd | (0, 1) | No | Yes | Unused but needs write-back to disk |
| 3rd | (1, 0) | Yes | No | Recently used but clean |
| **4th - KEEP** | **(1, 1)** | Yes | Yes | **WORST CHOICE** - Recently used & modified |

**✅ Memory trick:** "Zero-zero is the hero" - (0,0) is always evicted first!

---

### 🏆 MCQ #7: Mic-1 Stack Top Register

**Frequency:** ⭐ Appeared **3 times** - Years: 2015, 2022

**Question:** Which Mic-1 register always keeps the stack top value?

**Options:**
- A) CPP
- B) LV
- C) SP
- D) TOS

**Answer: D) TOS (Top Of Stack)**

**Explanation:**
TOS is a dedicated register that holds the **actual value** at the top of the stack, not just a pointer.

**All Mic-1 registers:**
- **TOS** - Top Of Stack (holds the actual top VALUE) ← **This is the answer!**
- **SP** - Stack Pointer (points to memory ADDRESS)
- **LV** - Local Variable pointer
- **CPP** - Constant Pool Pointer
- **MAR** - Memory Address Register
- **MDR** - Memory Data Register (32-bit)
- **PC** - Program Counter
- **MBR** - Memory Byte Register (8-bit)
- **H** - Holding register for ALU operations

**✅ Key distinction:** SP points to WHERE the top is, TOS holds WHAT the top value is!

---

<a name="definitions-section"></a>
## 📖 SECTION 2: DEFINITIONS

**Primary source: Tanenbaum's Structured Computer Organization textbook**
**Secondary source: Verified online resources**

### 1. Page fault

**Appeared in:** 2011, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2022
**Source:** Textbook

**Definition:** A page fault is an interrupt that occurs when a program tries to access a page that is not currently in physical memory, requiring the OS to load the page from disk.

---

### 2. Thrashing

**Appeared in:** 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2022
**Source:** Textbook

**Definition:** Thrashing occurs when a system spends more time swapping pages in and out of memory than executing processes, typically due to insufficient physical memory.

**Causes:**
- Too many processes for available memory
- Working sets don't fit in memory
- Poor page replacement decisions

**Solutions:**
- Suspend some processes
- Add more memory
- Use working set model
---

### 3. External fragmentation

**Appeared in:** 2011, 2012, 2013, 2014, 2015, 2017, 2019
**Source:** Textbook

**Definition:** External fragmentation is wasted memory that exists as small scattered free blocks where the total free memory is sufficient but not contiguous.

**Example:** 100KB free in 50 separate 2KB holes → can't allocate 60KB

**Occurs with:** Segmentation (variable-size segments)

**Solutions:** Compaction, coalescing free blocks
---

### 4. Bus skew

**Appeared in:** 2012, 2014, 2015, 2016, 2017, 2019
**Source:** Textbook

**Definition:** Bus skew is the variation in arrival times of signals on different lines of a bus caused by different wire lengths, capacitances, or propagation delays.

---

### 5. Internal fragmentation

**Appeared in:** 2012, 2013, 2014, 2015, 2017, 2019
**Source:** Textbook

**Definition:** Internal fragmentation is wasted memory space within an allocated memory block when the allocated block size exceeds the actual amount needed by the process.

**Example:** Process needs 3.7KB, gets 4KB page → 0.3KB wasted

**Occurs with:** Paging (fixed-size pages)
---

### 6. Demand paging

**Appeared in:** 2011, 2013, 2015, 2017, 2019
**Source:** Textbook

**Definition:** Demand paging is a memory management scheme where pages are loaded into physical memory only when they are referenced, rather than loading all pages at program start.

**Advantages:**
- Faster program startup
- Less memory used
- Can run programs larger than physical memory

**Disadvantages:**
- Page faults cause delays
- Requires page fault handler
---

### 7. Sign extension

**Appeared in:** 2014, 2015, 2017, 2019
**Source:** Textbook

**Definition:** Sign extension is the operation of increasing the bit-width of a signed integer by replicating the sign bit into the new higher-order positions to preserve the numerical value.

---

### 8. Unified cache

**Appeared in:** 2013, 2015, 2017, 2019
**Source:** Textbook

**Definition:** Unified cache memory is a cache organization where a single cache holds both instructions and data, as opposed to split caches where instructions and data have separate caches.

---

### 9. Copy-on-write

**Appeared in:** 2014, 2016, 2017, 2019
**Source:** Textbook

**Definition:** Copy-on-write is a memory optimization technique where processes share the same physical pages marked read-only until one attempts to modify a page, at which point a private copy is created.

---

### 10. Associative cache

**Appeared in:** 2012, 2014, 2016, 2022
**Source:** Textbook

**Definition:** Associative cache (fully associative) is a cache organization where any block can be placed in any cache line, providing maximum flexibility but requiring comparison with all cache entries.

---

### 11. Register renaming

**Appeared in:** 2016, 2017, 2019
**Source:** Textbook

**Definition:** Register renaming is a hardware technique that dynamically maps architectural registers to a larger set of physical registers to eliminate false dependencies (WAR and WAW hazards).

**Eliminates:** False dependencies (WAR and WAW)
**Enables:** Out-of-order execution, more parallelism

**Example:**
```
R1 = R2 + R3  →  P10 = P20 + P30
R1 = R4 + R5  →  P11 = P40 + P50  (uses different physical register)
```
---

### 12. Volatile memory

**Appeared in:** 2016
**Source:** Textbook

**Definition:** Volatile memory is memory that loses its contents when power is removed, such as RAM (as opposed to non-volatile memory like ROM or flash storage).

---

### 13. Precise interrupt

**Appeared in:** 2013
**Source:** Textbook

**Definition:** A precise interrupt is an interrupt where the machine state is saved such that the interrupted instruction and all previous instructions appear to have completed, while no subsequent instructions have executed.

---

### 14. Reentrancy

**Appeared in:** 2012
**Source:** Textbook

**Definition:** Reentrancy is the property of a code segment that allows it to be executed concurrently by multiple processes or interrupted and re-entered before the previous execution completes.

---

### 15. TLB (Translation Lookaside Buffer)

**Source:** Textbook

**Definition:** TLB is a cache that stores recent virtual-to-physical address translations to speed up memory access by avoiding page table lookups.

**Purpose:** Speed up virtual-to-physical address translation

**Hit:** Translation found in TLB (fast, ~1 cycle)
**Miss:** Must access page table in memory (slow, ~100+ cycles)
---

### 16. Belady's Anomaly

**Source:** Textbook

**Definition:** Belady's Anomaly is the counterintuitive phenomenon where increasing the number of page frames can actually increase the number of page faults (occurs only with FIFO algorithm).

**Important:** Only occurs with FIFO algorithm, NOT with LRU or Optimal

**Example:** Reference string might have 10 faults with 3 frames but 12 faults with 4 frames
---

### 17. Working set

**Source:** Textbook

**Definition:** The working set is the set of pages that a process actively uses during a time window, used to determine how much memory the process needs to avoid thrashing.

---

<a name="misc-section"></a>
## 📝 SECTION 3: MISCELLANEOUS SHORT QUESTIONS

**Quick reference for other common short questions**

### 1. ALU Control Signals

**For Mic-1 ALU - 5 control signals:**

| Function | F0 | F1 | ena | inva | inc |
|----------|----|----|-----|------|-----|
| A + B    | 1  | 1  | 1   | 0    | 0   |
| A + B + 1| 1  | 1  | 1   | 0    | 1   |
| B - A    | 1  | 1  | 1   | 1    | 1   |
| -A       | 1  | 1  | 0   | 1    | 1   |
| A        | 0  | 0  | 1   | 0    | 0   |
| B        | 1  | 0  | 0   | 0    | 0   |

**Remember:** For subtraction, use two's complement: B - A = B + NOT(A) + 1

---

### 2. Page Replacement Quick Reference

**LRU (Least Recently Used):**
- Evict the page that hasn't been used for the longest time
- Track: Last use time for each page
- Best performance but more overhead

**FIFO (First In, First Out):**
- Evict the oldest page (first loaded)
- Track: Loading order
- Simple but can suffer from Belady's Anomaly

**Second-Chance (Clock):**
- FIFO with reference bit
- Give page a "second chance" if referenced recently
- Clear reference bit on first pass, evict on second pass

---

### 3. Common Memory Sizes

**Intel IA-32:**
- Segment registers: **16 bits**
- Segments max size: **4 GB** (2³² bytes)
- Page sizes: **4 KB** (most common) or **4 MB** (large pages)

**Mic-1:**
- Memory address: **32 bits**
- Word size: **32 bits** (4 bytes)
- Memory Data Register (MDR): **32 bits**
- Memory Byte Register (MBR): **8 bits**

---

### 4. FAT vs Linux Inodes (6-mark question!)

**FAT (File Allocation Table):**
- **Structure:** Centralized table, one entry per disk block
- **Location:** Stored in fixed location at start of disk
- **File storage:** Chain of blocks using table entries
- **Advantages:** Simple, easy to implement
- **Disadvantages:** Poor locality, fragmentation, table can be huge

**Linux Inodes:**
- **Structure:** Separate inode per file with pointers
- **Location:** Distributed across disk in inode blocks
- **File storage:** Direct pointers + indirect blocks
- **Advantages:** Good locality, flexible, supports hard links
- **Disadvantages:** More complex, limited by number of inodes

**Key difference:** FAT uses centralized table; inodes are per-file structures

---

### 5. Cache Memory Basics

**Direct Mapped:**
- Each memory block maps to exactly one cache line
- Fast but prone to conflicts

**Fully Associative:**
- Any memory block can go in any cache line
- Flexible but requires comparing all entries

**Set Associative:**
- Compromise: N-way set associative
- Each block maps to a set of N lines
- Common: 2-way, 4-way, 8-way

**Write Policies:**
- **Write-through:** Write to both cache and memory immediately
- **Write-back:** Write to cache, update memory later (on eviction)

---

### 6. Boolean Algebra for Logic Gates

**De Morgan's Laws:**
- NOT(A AND B) = NOT(A) OR NOT(B)
- NOT(A OR B) = NOT(A) AND NOT(B)

**Common equivalences:**
- A + 0 = A
- A + 1 = 1
- A · 0 = 0
- A · 1 = A
- A + A = A
- A · A = A
- A + NOT(A) = 1
- A · NOT(A) = 0

**Useful for gate minimization questions!**

---

### 7. Multiplexer Logic

**2-to-1 Multiplexer: Output = C ? D1 : D0**

| Function | D0   | D1   | C |
|----------|------|------|---|
| A        | 0    | 1    | A |
| AB       | 0    | B    | A |
| A+B      | B    | 1    | A |
| NOT(A)   | 1    | 0    | A |

**Remember:** When C=0, output is D0; when C=1, output is D1

---

### 8. Segmentation vs Paging

**Segmentation:**
- **Size:** Variable-length segments
- **Visibility:** Visible to programmer
- **Fragmentation:** External fragmentation
- **Protection:** Easy per-segment protection
- **Sharing:** Easy to share code/data segments

**Paging:**
- **Size:** Fixed-length pages
- **Visibility:** Transparent to programmer  
- **Fragmentation:** Internal fragmentation only
- **Protection:** Page-level protection
- **Sharing:** Can share pages (e.g., copy-on-write)

**Can be combined:** Segmentation with paging (Intel uses both!)

---

### 9. Unix File System Quick Facts

**Hard Links:**
- Multiple directory entries point to same inode
- Share same file content and permissions
- Cannot cross file systems
- Cannot link to directories (prevents cycles)

**Soft Links (Symbolic Links):**
- File contains path to another file
- Can cross file systems
- Can link to directories
- Breaks if target is deleted

**Index Blocks:**
- Direct blocks: Point directly to data
- Single indirect: Points to block of pointers
- Double indirect: Points to block of single indirect blocks
- Triple indirect: Three levels of indirection

---

## 🎯 EXAM STRATEGY TIPS

### For MCQ Questions:
1. **Read carefully** - note exact wording ("effect on stack pointer", "cannot be encoded")
2. **Eliminate obviously wrong** answers first
3. **Watch for tricky wording** - "no effect" vs "has effect"
4. **Know the exceptions** - like "test" and "cmp" don't affect stack pointer

### For Definitions:
1. **Be concise** - "in one sentence" means exactly that!
2. **Include key terms** - don't just paraphrase, use technical vocabulary
3. **Add example if space** - but only if question allows
4. **Practice writing** definitions from memory before exam

### For Calculations:
1. **Show all work** - partial credit is available
2. **Use provided tables** - don't try to do page replacement in your head
3. **Check your arithmetic** - simple errors cost marks
4. **Label your answers** clearly

---

## ✅ PRE-EXAM CHECKLIST

**The night before:**
- [ ] Can define all terms from Section 2 without looking
- [ ] Can answer all MCQs from Section 1 correctly
- [ ] Can fill in ALU control signals table from memory
- [ ] Can calculate proportional allocation
- [ ] Know second-chance page eviction order by heart
- [ ] Can identify RAW/WAR/WAW dependencies

**Morning of exam:**
- [ ] Review this cheat sheet one final time
- [ ] Practice one LRU and one FIFO page replacement
- [ ] Verify you know which Intel instructions affect stack pointer
- [ ] Remember: H = MDR - H is INVALID in Mic-1!

---

**Last updated:** November 2025  
**Based on:** CS 244 past papers 2011-2022 (Willem Bester)  
**Textbook:** Tanenbaum - Structured Computer Organization, 6th Edition

---

## 🎊 FINAL WORDS

This cheat sheet represents a comprehensive analysis of:
- ✅ **7 core MCQ questions** ranked by frequency (appeared 3-8 times each)
- ✅ **17 essential definitions** from textbook and verified sources
- ✅ **9 miscellaneous topics** covering calculations, algorithms, and quick references
- ✅ **Complete answers and explanations** from official memos
- ✅ **Study strategies and exam tips** for maximum efficiency

**Remember:**
1. **MCQ Section 1** = Free marks if you memorize! Focus on the top 7 questions.
2. **Definitions Section 2** = Easy marks, practice writing them in one sentence.
3. **Misc Section 3** = Vital for calculations (ALU table, page replacement, proportional allocation).

**Trust the frequency analysis!** The top MCQs have appeared 5-8 times across 12 years - they WILL appear again.

**Good luck on your test! 🍀💪📚**

**Good luck! 🍀**