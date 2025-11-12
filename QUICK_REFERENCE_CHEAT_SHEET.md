# Quick Reference Cheat Sheet - CS 244 Test

## 🔴 MUST-KNOW ONE-LINERS (Free Marks!)

| Term | Definition |
|------|------------|
| **Bus Skew** | Time difference when a signal arrives at different components due to varying wire lengths |
| **Sign Extension** | Extending a smaller signed value to a larger width by copying the sign bit |
| **Unified Cache** | A single cache that stores both instructions and data |
| **Register Renaming** | Hardware technique mapping architectural registers to physical registers to eliminate false dependencies |
| **Internal Fragmentation** | Wasted space within an allocated memory block that is not used by the process |
| **External Fragmentation** | Wasted space between allocated memory blocks; total free memory sufficient but not contiguous |
| **Copy-on-Write** | Memory optimization where processes share pages until one modifies it, then a copy is made |
| **Thrashing** | System spends more time swapping pages than executing processes due to insufficient memory |
| **Volatile Memory** | Memory that loses its contents when power is removed (e.g., RAM) |
| **Relocatable Code** | Code that can be loaded and executed at different memory addresses |

---

## 🎯 INSTANT ANSWERS (Multiple Choice)

### Intel Stack Pointer
- **Affects it:** `call`, `push`, `pop`, `ret`
- **Doesn't affect it:** `cmp`, `test` ✓

### Mic-1 Registers
- **TOS** = Top of Stack ✓ (always keeps stack top value)
- CPP = Constant Pool Pointer
- LV = Local Variable pointer
- SP = Stack Pointer
- MDR = Memory Data Register
- H = Holding register

### Mic-1 Microcode Limitation
- **Cannot encode:** `H = MDR - H` ✓
- Can encode: `H = H - MDR`, `H = H + MDR`, `H = MDR + H`

### Segment Registers
- **Width:** 16 bits ✓
- Types: CS, DS, SS, ES

### Proportional Allocation (62 frames, 10 & 127 pages)
- Formula: (127/137) × 62 = **57 frames** ✓

### Second-Chance Page Replacement
- **Evict first:** (0, 0) ✓ [not referenced, not modified]
- Order: (0,0) → (0,1) → (1,0) → (1,1)

### Pipeline Dependency (R1 = R2*R3; R4 = R5+R1)
- **Type:** RAW ✓ (Read After Write - "true dependency")

### Intel IA-32 Largest Page Size
- **Answer:** 4 MiB ✓

---

## 📊 ALU Control Signals Cheat Sheet

| Function | F0 | F1 | ena | enb | inva | inc |
|----------|----|----|-----|-----|------|-----|
| A + B    | 1  | 1  | 1   | 1   | 0    | 0   |
| A + B + 1| 1  | 1  | 1   | 1   | 0    | 1   |
| B - A    | 1  | 1  | 1   | 1   | 1    | 1   |
| -A       | 1  | 1  | 1   | 0   | 1    | 1   |

**How B - A works:** Invert A (two's complement = invert + 1), then add B

---

## 📝 Page Replacement Quick Reference

### LRU (Least Recently Used)
- Evict the page that hasn't been used for the longest time
- Track "last used" time for each page
- Most common pattern to practice!

### FIFO (First In First Out)
- Evict the oldest page in memory
- Simple queue approach
- Can suffer from Belady's Anomaly

### Belady's Anomaly
- **Definition:** Increasing the number of frames can sometimes INCREASE page faults (counterintuitive!)
- Only occurs with FIFO, not LRU
- Show with your calculations (e.g., 3 frames vs 4 frames)

---

## 🔧 Multiplexer Wiring Table

| Function | D0  | D1  | C   |
|----------|-----|-----|-----|
| A        | A   | A   | X   |
| A + B    | A   | B   | B   |
| AB       | VGnd| A   | B   |

*X = don't care, VGnd = electrical ground, VCC = voltage*

---

## 💾 Memory Management Formulas

### Proportional Allocation
```
frames_for_process_i = (pages_i / total_pages) × total_frames
```

### Standard Problem
- System: 62 frames
- Process 1: 10 pages
- Process 2: 127 pages
- Total: 137 pages
- **Process 2 gets:** (127/137) × 62 = 57 frames

---

## 🏗️ Mic-1 Architecture Quick Facts

### Four Subcycles
1. **Subcycle 1:** Put address on bus, start memory read
2. **Subcycle 2:** Wait for memory
3. **Subcycle 3:** Get data from memory into MDR
4. **Subcycle 4:** ALU operates, write back to registers

### N and Z Bits
- **N (Negative):** Set when ALU result is negative (MSB = 1)
- **Z (Zero):** Set when ALU result is zero (all bits = 0)
- Used for branching: if condition true → branch to T, else → branch to F

### Mic-4 Pipelining
- **Why 4 MIRs?** One for each pipeline stage to avoid conflicts

---

## 📂 File Systems Comparison

### FAT (File Allocation Table)
**Pros:**
- Simple
- Good for small files

**Cons:**
- Fixed table size
- Slow for large files (chain traversal)
- External fragmentation
- No built-in redundancy

### Linux inodes
**Pros:**
- Direct, indirect, double-indirect, triple-indirect pointers
- Fast access for small files (direct pointers)
- Scales well to large files
- Efficient space usage

**Cons:**
- More complex
- Small overhead for tiny files

**Strategy for large files:** Multi-level indexing (direct → indirect → double → triple)

---

## 🔄 Pipeline Dependencies

### RAW (Read After Write) - "True"
- **Example:** R1 = R2 + R3; R4 = R1 + R5
- **Cannot eliminate** - real data dependency
- **Mitigation:** Forwarding/bypassing

### WAR (Write After Read) - "Anti"
- **Example:** R1 = R2 + R3; R2 = R4 + R5
- **Can eliminate** with register renaming

### WAW (Write After Write) - "Output"
- **Example:** R1 = R2 + R3; R1 = R4 + R5
- **Can eliminate** with register renaming

---

## 🎓 Cache Memory

### Locality Principles
1. **Temporal Locality:** Recently used data will likely be used again soon
   - Example: loop variables
2. **Spatial Locality:** Data near recently used data will likely be used soon
   - Example: array elements

### Types
- **Unified:** Instructions + data in one cache
- **Split:** Separate instruction cache (I-cache) and data cache (D-cache)
- **Associative:** Content-addressable; any block can go in any cache line

---

## 🚦 Branch Prediction Strategy

### Static Strategy
- **Take:** Backward jumps (loops usually iterate)
- **Don't take:** Forward jumps (if-statements less predictable)

### Evaluation
- **Good for loops** (backward = loop back to start)
- **Mediocre for conditionals** (forward = if-then-else)
- Overall: Decent simple strategy

---

## 🔐 Segmentation vs Paging

| Aspect | Segmentation | Paging |
|--------|-------------|--------|
| **Concept** | Logical divisions (code, data, stack) | Fixed-size blocks |
| **Size** | Variable | Fixed (e.g., 4KB) |
| **Programmer View** | Visible (segment:offset) | Transparent |
| **Fragmentation** | External | Internal |
| **Fault Type** | Segmentation fault (protection error) | Page fault (demand paging) |

---

## 📐 Unix File System

### Why No Hard Links to Directories?
- Would create cycles in directory graph
- Makes garbage collection impossible
- Could lead to infinite loops in traversal
- Only soft/symbolic links allowed to directories

### inode Strategy
- **Direct pointers:** First 10-12 blocks (fast access for small files)
- **Single indirect:** Points to block of pointers
- **Double indirect:** Points to block of single indirect blocks
- **Triple indirect:** Points to block of double indirect blocks
- Allows large file range without wasting space for small files

---

## ⚡ TLB (Translation Lookaside Buffer)

### Operation
1. CPU generates virtual address
2. Check TLB for virtual-to-physical mapping
3. **TLB hit:** Use cached translation (fast!)
4. **TLB miss:** Look up page table (slow), then cache result in TLB
5. Access physical memory

**Purpose:** Speed up virtual memory address translation

---

## 🎯 Day-Before-Test Checklist

### Can you...
- [ ] Calculate LRU and FIFO page faults?
- [ ] Define and show Belady's Anomaly?
- [ ] Explain thrashing in 2 sentences?
- [ ] Compare FAT vs inodes (6 marks worth)?
- [ ] Fill in ALU control signal table?
- [ ] Identify RAW/WAR/WAW dependencies?
- [ ] Know which Intel instructions affect stack pointer?
- [ ] Calculate proportional allocation (62 frames)?
- [ ] Define all 10 one-sentence terms?
- [ ] Explain second-chance page replacement?
- [ ] Describe TLB operation?
- [ ] Compare segmentation vs paging?
- [ ] Explain cache locality principles?

### Emergency Review Priority
1. Page replacement calculations (most common!)
2. All one-sentence definitions
3. FAT vs inodes (high marks!)
4. Pipeline dependencies
5. ALU control signals

---

## 💡 Pro Tips

1. **Show your work** on calculations - partial credit!
2. **Use the boxes provided** for page replacement work
3. **Write neatly in ink** - pencil not allowed for mark queries
4. **Read "in one sentence" carefully** - they mean it!
5. **Remember: 80 is full marks** even if paper has more points
6. **Time management:** Don't spend 20 minutes on a 1-mark question
7. **Multiple choice:** Elimination strategy works!

---

**Last updated:** Based on 12 past papers (2011-2022) set by Willem Bester

**Good luck! 🍀**
