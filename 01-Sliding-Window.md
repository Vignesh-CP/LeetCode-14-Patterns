# Pattern 1: Sliding Window 🪟

## 1. 🎯 The Trigger (When to use it)
Use this pattern when the problem asks for:
*   A **"contiguous"** subarray or substring.
*   The **"longest"**, **"shortest"**, or a **"specific target"** size/sum.
*   *Keywords:* "longest substring without repeating", "minimum size subarray sum".

## 2. 🧠 The Human Logic
Imagine a cardboard frame over the array. 
*   **The Explorer (Right Pointer):** Expands the window by moving forward one step at a time, bringing new elements into the box.
*   **The Enforcer (Left Pointer):** The moment the window breaks the rules (e.g., sum gets too big, duplicate character appears), the Left pointer drags the back of the window forward, kicking elements out until the rules are followed again.

## 3. 💀 The Gotchas (Edge Cases)
*   **Left passing Right:** If a single massive number breaks the rule instantly, the Left pointer might step *past* the Right pointer. Do not panic! This just means the window size is temporarily `0` before the Right pointer moves forward again.
*   **When to update the answer:** If you are looking for the *longest* window, update your max score at the end of the step (when the window is valid). If looking for the *shortest*, update your min score *inside* the shrink loop.

## 4. 🛠️ The Blueprint (Python Code)
```python
def sliding_window_template(nums):
    left = 0
    best_result = 0 # or float('inf') for shortest
    
    # Right pointer expands the window
    for right in range(len(nums)):
        # 1. Add the current element (nums[right]) to your window state
        
        # 2. While the window is INVALID, shrink it!
        while window_is_invalid:
            # Remove nums[left] from the window state
            left += 1
            
        # 3. The window is now VALID again. Update your best result.
        best_result = max(best_result, right - left + 1)
        
    return best_result
