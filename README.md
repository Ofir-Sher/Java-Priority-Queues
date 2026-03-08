# Advanced Customizable Heaps

A versatile and advanced priority queue implementation in Java 21, developed for the Data Structures course at Tel Aviv University. 

This project goes beyond a standard heap implementation by providing a single, unified data structure that can morph into four distinct types of advanced heaps based on its initialization parameters. It also tracks deep internal metrics for empirical and theoretical amortized analysis.

## 🚀 Features & Heap Configurations

The heap's behavior is governed by two immutable boolean flags set during instantiation: `lazyMelds` and `lazyDecreaseKeys`. Depending on these flags, the structure operates as one of the following:

* **Fibonacci Heap** (`lazyMelds = true`, `lazyDecreaseKeys = true`): Delivers O(1) amortized time for insertions and melds, utilizing cascading cuts for key reductions.
* **Binomial Heap** (`lazyMelds = false`, `lazyDecreaseKeys = false`): Enforces strict structure with immediate successive linking and standard heapify-up operations.
* **Lazy Binomial Heap** (`lazyMelds = true`, `lazyDecreaseKeys = false`): Defers tree consolidation (successive linking) until a `deleteMin` is called.
* **Binomial Heap with Cuts** (`lazyMelds = false`, `lazyDecreaseKeys = true`): A custom hybrid variant that forces strict structure (no lazy melds) but utilizes the cascading cuts mechanism of a Fibonacci heap.

## 🛠️ Supported Operations

| Operation | Description |
| :--- | :--- |
| `insert(key, info)` | Inserts a new element into the heap. |
| `findMin()` | Returns the element with the minimum key. |
| `deleteMin()` | Removes the minimum element and triggers successive linking to consolidate the root list. |
| `decreaseKey(node, diff)` | Decreases the key of a specific node, applying cascading cuts or heapify-up depending on configuration. |
| `delete(node)` | Removes a specific node from the heap. |
| `meld(heap2)` | Merges another heap into the current one. May trigger immediate O(log n) successive linking if `lazyMelds` is false. |

## 📊 Analytical Metrics Tracking

To facilitate the study of amortized time complexities, the heap internally tracks operations over its lifecycle:
* **Total Links:** The cumulative number of tree linkings performed.
* **Total Cuts:** The cumulative number of cascading cuts executed.
* **Total Heapify Costs:** The total distance nodes have traveled during heapify-up operations.
* **Marked Nodes & Tree Counts:** Tracks the number of roots and marked nodes for internal structure monitoring.

## 👥 Authors
* Ofir Sher
* Roy Dolev
