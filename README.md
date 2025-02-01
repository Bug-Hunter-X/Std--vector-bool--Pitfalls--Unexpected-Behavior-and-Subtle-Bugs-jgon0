# std::vector<bool> Pitfalls: A common C++ gotcha

This repository demonstrates a common source of confusion and bugs in C++: the `std::vector<bool>` specialization. Unlike other `std::vector` types, `std::vector<bool>` optimizes memory usage by packing booleans into bits.  This optimization, while seemingly beneficial, leads to significant differences in behavior that can easily trip up developers.

The `vectorBoolBug.cpp` file shows example code that makes assumptions about `std::vector<bool>`'s behavior that are incorrect.

The `vectorBoolSolution.cpp` file provides a corrected version demonstrating how to safely and correctly use `std::vector<bool>` or use an alternative like `std::vector<char>` or `std::vector<bool>` to avoid the pitfalls.

**Key Differences:**
* **Iteration:** Iterators for `std::vector<bool>` don't provide direct access to the underlying bits; they provide proxies.
* **Memory Usage:** Significantly less memory than a `std::vector<char>` or `std::vector<int>`, but this comes at the cost of additional complexity.
* **Element Access:** Accessing elements requires additional operations.

**Recommendation:** Unless memory usage is a critical concern, it's usually best to avoid `std::vector<bool>` and use a `std::vector<char>` (if space is at a premium) or a `std::vector<bool>`(for clarity).