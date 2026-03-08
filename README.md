# Java-Priority-Queues
A versatile Java 21 implementation of advanced priority queues, capable of acting as a Fibonacci, Binomial, or Lazy Binomial heap based on dynamic configuration flags.
# Advanced Customizable Heaps

[cite_start]A versatile and advanced priority queue implementation in Java 21, developed for the Data Structures course at Tel Aviv University[cite: 96, 97, 108]. 

This project goes beyond a standard heap implementation by providing a single, unified data structure that can morph into four distinct types of advanced heaps based on its initialization parameters. [cite_start]It also tracks deep internal metrics for empirical and theoretical amortized analysis[cite: 111, 133, 184].

## 🚀 Features & Heap Configurations

[cite_start]The heap's behavior is governed by two immutable boolean flags set during instantiation: `lazyMelds` and `lazyDecreaseKeys`[cite: 109, 110]. Depending on these flags, the structure operates as one of the following:

* [cite_start]**Fibonacci Heap** (`lazyMelds = true`, `lazyDecreaseKeys = true`): Delivers O(1) amortized time for insertions and melds, utilizing cascading cuts for key reductions[cite: 121, 128].
* [cite_start]**Binomial Heap** (`lazyMelds = false`, `lazyDecreaseKeys = false`): Enforces strict structure with immediate successive linking and standard heapify-up operations[cite: 115, 126, 128].
* [cite_start]**Lazy Binomial Heap** (`lazyMelds = true`, `lazyDecreaseKeys = false`): Defers tree consolidation (successive linking) until a `deleteMin` is called[cite: 126, 128].
* [cite_start]**Binomial Heap with Cuts** (`lazyMelds = false`, `lazyDecreaseKeys = true`): A custom hybrid variant that forces strict structure (no lazy melds) but utilizes the cascading cuts mechanism of a Fibonacci heap[cite: 128, 163, 164].

## 🛠️ Supported Operations

| Operation | Description |
| :--- | :--- |
| `insert(key, info)` | [cite_start]Inserts a new element into the heap[cite: 133]. |
| `findMin()` | [cite_start]Returns the element with the minimum key[cite: 133]. |
| `deleteMin()` | [cite_start]Removes the minimum element and triggers successive linking to consolidate the root list[cite: 118, 133]. |
| `decreaseKey(node, diff)` | [cite_start]Decreases the key of a specific node, applying cascading cuts or heapify-up depending on configuration[cite: 119, 121, 126, 133]. |
| `delete(node)` | [cite_start]Removes a specific node from the heap[cite: 133]. |
| `meld(heap2)` | Merges another heap into the current one. [cite_start]May trigger immediate O(log n) successive linking if `lazyMelds` is false[cite: 115, 133, 166]. |

## 📊 Analytical Metrics Tracking

[cite_start]To facilitate the study of amortized time complexities, the heap internally tracks operations over its lifecycle:
* [cite_start]**Total Links:** The cumulative number of tree linkings performed[cite: 133].
* [cite_start]**Total Cuts:** The cumulative number of cascading cuts executed[cite: 133].
* [cite_start]**Total Heapify Costs:** The total distance nodes have traveled during heapify-up operations[cite: 133].
* [cite_start]**Marked Nodes & Tree Counts:** Tracks the number of roots and marked nodes for internal structure monitoring[cite: 133].

## 👥 Authors
* Ofir Sher
* Roy Dolev
