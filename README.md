# CSC3050 Project 4 – Cache Simulator & Matrix‐Multiply Analysis
A hands‑on implementation of:

Part 3: Multi‑level cache simulator with two L1 optimizations (stride prefetch & FIFO replacement).

Part 4: Trace‑driven performance analysis of five matrix‑multiply loop orders (including a blocked version).

Demo video: 

![p4](./image/p4.gif)


## 📦 Repository Contents
```bash
├── include/            # Headers (Cache.h, MultiLevelCacheConfig.h, etc.)
├── src/                # Source files (cache simulator & matmul programs)
├── trace/              # Part 3 & Part 4 trace files
├── docs/               # Demo video thumbnail, WeChat QR code
└── README.md           # This file
```

## 🚀 Quick Start
1. Build
```bash
mkdir build && cd build
cmake ..
make
```

2. Run the cache simulator (Part 3)
- Prefetch: `./CacheMulti -p ../trace/Part3/test2.trace`

- FIFO: `./CacheMulti -f ../trace/Part3/test2.trace`

4. Run the matmul analysis (Part 4)
`./matmul ../trace/Part4/matmul0.trace`

Results (L1 miss rates, cycle counts) are printed to stdout and also written to CSV under trace/Part3 or trace/Part4.

## 📝 Project Approach

### Part 3

- Prefetch: Detect fixed stride after three consecutive strides and prefetch the next block only while the pattern persists.

- FIFO: Turn L1 into fully‑associative and evict the oldest block first.

### Part 4

- matmul0–3: Compare the classic ijk, register‑optimized, kij, and jki loop orders and observe their L1 miss rates.

- matmul4: Implement a blocked (16×16 tile) version to exploit spatial & temporal locality, achieving the lowest miss rate and fastest cycles.

### 🤝 Need Help?
If you’re working on the CSC3050 cache simulator or matrix‑multiply assignment and would like personalized guidance, feel free to reach out on WeChat:

WeChat ID: coder199608

Scan to add:

![wechat](https://raw.githubusercontent.com/coder199608/pictures/main/images/wechat_qr.png)

I’m happy to walk you through the design, debugging strategies, or performance tuning—just drop me a message!

### 📝 License
This work is provided for educational purposes only. Feel free to fork and adapt for your own lab assignments, but please do not redistribute or claim as your own.
