Review the file or function in $ARGUMENTS for performance and efficiency issues.

If $ARGUMENTS is empty, ask what to optimize.

Steps:
1. Read the target code carefully
2. Identify the language, framework, and runtime environment
3. Check for existing benchmarks or performance tests

Look for these categories of issues:

**Algorithm & data structures**
- O(n²) or worse loops that could be O(n) with a map/set
- Repeated linear searches that should use indexed lookups
- Unnecessary sorting of already-sorted data

**Database / I/O**
- N+1 query patterns (queries inside loops)
- Missing indexes on filtered/sorted columns
- Fetching full rows when only a few columns are needed
- Synchronous I/O blocking the main thread

**Memory**
- Accumulating large collections in memory when streaming would work
- Object creation inside hot loops
- Unbounded caches with no eviction

**Network**
- Chatty APIs (many small requests vs one batched request)
- Missing pagination on large result sets
- No caching on repeated identical requests

**Frontend specific**
- Rendering on every keystroke instead of debouncing
- Missing memoization on expensive computed values
- Unnecessary re-renders from unstable object/array references

For each issue found:
- State the problem clearly
- Estimate the impact (low / medium / high)
- Show the fix with a before/after code snippet

Only flag real issues. Do not suggest micro-optimizations with negligible impact. Do not refactor style or structure unless it directly causes a performance problem.

End with a prioritized list: fix these first (highest impact, lowest effort).
