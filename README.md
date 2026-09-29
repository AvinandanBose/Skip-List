# 📌 Skip List

A comprehensive implementation and analysis of the **Skip List** data structure using **C/C++**, including detailed explanations of probabilistic balancing, dynamic memory allocation, pointer array management, and rigorous mathematical complexity proofs. This repository is designed for students, educators, and developers who want to deeply understand how Skip Lists work internally and mathematically.

---

# Repository Link

🔗Repository: [https://github.com/AvinandanBose/Skip-List](https://github.com/AvinandanBose/Skip-List) 

---

## 📘 Introduction

A **Skip List** is a probabilistic data structure that serves as a highly efficient alternative to balanced binary trees. It allows for quick search, insertion, and deletion of elements by utilizing probabilistic balancing rather than strictly enforced structural balancing.

Unlike ordinary linear lists where a search requires an O(n) node-by-node scan, a Skip List implements "express lanes" by adding additional forward pointers. A node in this structure consists of:

* **Key:** Stores the integer data of the element.


* **Forward Pointers (`**forward`):** A dynamically allocated array of pointers that link to the next nodes across multiple levels.



The number of levels a node occupies is determined probabilistically (via a random coin flip) during creation. This hierarchical, multi-level pointer system allows intermediate nodes to be bypassed entirely during traversal, resulting in rapid expected performance.

---

## 🚀 Key Advantages

* **Quick Operations:** Achieves an expected performance of O(log n) for search, insert, and remove operations.


* **Probabilistic Balancing:** Avoids the degenerate data structures produced by sequential tree insertions without the heavy algorithm overhead of strict tree rebalancing.


* **Fast Traversal:** Upper-level pointers act as "express lanes," significantly reducing the number of horizontal comparisons required to find a target node.



## ⚠️ Trade-offs & Disadvantages

* **Memory Overhead:** Pointer storage increases from approximately $n$ pointers in an ordinary linked list to roughly $2n$ pointers overall.


* **RNG Dependency:** Relies heavily on the system's pseudo-random number generator (PRNG). If `rand()` is not properly seeded (e.g., using `time(0)`), the exact same sequence of random numbers will generate, destroying the randomness of the list structure.


* **Worst-Case Degradation:** In the absolute worst-case scenario where the coin flip consistently fails (all nodes drop to Level 0), the structure devolves into a standard linked list, degrading traversal to O(n) time complexity.



## 🌍 Real-World Applications

* **Dictionaries & Ordered Lists:** Highly effective for abstract data types where elements are queried online and randomly permuting the input sequence is impractical.


* **Database Indexing:** Often utilized under the hood in systems requiring fast, concurrently safe memory storage and retrieval.

## ⚡ Complexity Analysis



### Time Complexity (Main List Operations)

| Operation | Best Case | Worst Case | Average Case |
| --- | --- | --- | --- |
| **Search** | O(1)| O(n)| O(log n)|
| **Insert** | O(1)| O(n)| O(log n)|
| **Delete** | O(1)| O(n)| O(log n)|
| **Random Level Generation** | O(1)| O(MAX_LEVEL) $\approx$ O(1)| O(1)|

### Space Complexity

* **Auxiliary Space:** O(1) for functions like `randomLevel()` and `createNode()` because memory allocations are bounded by a fixed constant (`MAX_LEVEL`).


* **Holistic Space:** O(n), representing the total memory required for $n$ data elements, plus approximately $2n$ forward pointer slots.



## 🛠️ Included Algorithms

This repository implements the following core algorithms:

1. **List Initialization (`createSkipList`):** Allocating the base structure and creating a dummy header node bounded by `MAX_LEVEL`.


2. **Random Level Generation (`randomLevel`):** Utilizing a 50% probability `while` loop to dictate node height, bounded safely by `MAX_LEVEL` to prevent infinite memory allocation.


3. **Insertion & Path Mapping (`insertElement`):** Executing a top-down search to map predecessor nodes using an `update` array, which is safely wiped clean using `<cstring>`'s `memset()` function.


4. **Dynamic Node Creation (`createNode`):** Using `malloc` to dynamically allocate memory for both the node struct and its multi-level `**forward` pointer array.


5. **Pointer Rewiring:** Updating the forward pointers of mapped predecessor nodes to seamlessly splice the new multi-level node into the hierarchy.



---

## 📚 Learning Outcomes

By studying and implementing the code in this repository, you will gain a deep understanding of advanced data structures and algorithmic analysis. Specifically, you will learn how to:

* **Master Probabilistic Data Structures:** Understand how randomized 50/50 coin tosses can replace complex structural rotations to maintain overall list balance.


* **Manage Advanced Pointer Arrays:** Gain hands-on experience handling dynamic pointer-to-pointer (`**forward`) arrays without causing memory leaks or wild pointers.


* **Execute Deep Memory Wipes:** Learn why and how low-level functions like `memset()` are used to safely clear contiguous memory blocks for update tracking.


* **Understand PRNG Mechanics:** Learn the math behind Linear Congruential Generators (LCG) and why seeding random number generators with the Unix Epoch (`time(0)`) is critical for probabilistic algorithms.


* **Perform Rigorous Mathematical Proofs:** Discover how to analyze average case complexity using infinite geometric series, common ratios, and probability distributions to prove the underlying efficiency of the structure.



---

# 👨‍💻 Author

Developed and analyzed by [@AvinandanBose](https://github.com/AvinandanBose)

---

# 📄 License

This project is licensed under the **MIT License**.

---

## ⭐ Support

If you found this helpful:

* ⭐ Star the repository
* 🍴 Fork it
* 📢 Share with others

---
