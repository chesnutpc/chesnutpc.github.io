---
layout: default
title: Caesar Cipher Encryptor
---

## Caesar Cipher Encryptor

### Question
You’re given a non-empty array of positive integers representing the amounts of time that specific queries take to execute. Only one query can be executed at a time, but the queries can be executed in any order.

A query’s waiting time is defined as the amount of time that it must wait before its execution starts. In other words, if a query is executed second, then its waiting time is the duration of the first query; if a query is executed third, then its waiting time is the sum of the durations of the first two queries.

Write a function that returns the minimum amount of total waiting time for all of the queries. For example, if you’re given the queries of durations [1, 4, 5], then the total waiting time if the queries were executed in the order of [5, 1, 4] would be (0) + (5) + (5 + 1) = 11. The first query of duration 5 would be executed immediately, so its waiting time would be 0, the second query of duration 1 would have to wait 5 seconds (the duration of the first query) to be executed, and the last query would have to wait the duration of the first two queries before being executed.

Note: The input array may be mutated.

Sample Input:
queries = [3,2,1,2,6]

Sample Output:
17

### Solution
```
def minimumWaitingTime(queries):
    # To minimize the wait time, we will want to
    # sort the array in ascending order.  This can
    # be done in place with the sort method.
    queries.sort()

    # Now we just need to iterate through the array
    # summing up waiting times.  We use the enumerate
    # function to index the list.
    sumOfWaitingTime = 0
    for idx, duration in enumerate(queries):
        # duration get added to all remaining queries
        sumOfWaitingTime += duration * (len(queries) - (idx + 1))

    return sumOfWaitingTime
```
O(1) queries is sorted in place\
O(n log(n) + n) [sort + loop] = O(n log n)
