# AI solution verification challenge
## Selected Problem: Buggy merge sort implementation.

## The Bug:
In the merge function, the loop meant to iterate through the left array used the wrong increment:

while (i < left.length) {
  result.push(left[i]);
  j++; // Wrong
}

This prevented pointer i from advancing, causing incorrect output or infinite loops.

## AI’s Fix:

while (i < left.length) {
  result.push(left[i]);
  i++; // Correct
}

Why the Fix Makes Sense:
The loop is processing the left array, so only i should increment. Incrementing j never progresses through left.

## Verification Strategy 1: Testing
My tests:
- [3,1,2]
- [1,2,3]
- [3,2,1]
- []
- [5]
- [2,1,2]

AI also suggested:
- Large arrays
- All identical values
- Negative numbers

All tests passed after the fix.

## Verification Strategy 2: Alternatives Considered
- Merge Sort: Stable, guaranteed O(n log n).
- Quick Sort: Faster on average, but worst-case O(n²).
- Built-in .sort(): Best practical option unless stability is required.

## What I Learned
- Small pointer errors break entire algorithms.
- Always test edge cases.
- AI solutions still need verification.
- Understanding assumptions makes code more reliable.

Biggest Lesson:
Verification isn’t just checking correctness—it builds understanding and improves code quality.