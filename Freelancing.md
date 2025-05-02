---
layout: default
title: Optimal Freelancing
---

## Optimal Freelancing

### Question
You recently started freelance software development and have been offered a variety of job opportunities. Each job has a deadline, meaning there is no value in completing the work after the deadline. Additionally, each job has an associated payment representing the profit for completing that job. Given this information, write a function that returns the maximum profit that can be obtained in a 7‑day period.

Each job will take 1 full day to complete, and the deadline will be given as the number of days left to complete the job. For example, if a job has a deadline of 1, then it can only be completed if it is the first job worked on. If a job has a deadline of 2, then it could be started on the first or second day.

Note: There is no requirement to complete all of the jobs. Only one job can be worked on at a time, meaning that in some scenarios it will be impossible to complete them all.

Sample Input:
jobs = [
        {"deadline": 1, "payment": 1},
        {"deadline": 2, "payment": 1},
        {"deadline": 2, "payment": 2},
]

Sample Output:
3

### Solution
```
def optimalFreelancing(jobs):
    # Note that it makes sense to do the jobs on 
    # the last possible day to leave room to do
    # jobs that have an earlier deadline.
    profit = 0
    # We need to sort the jobs in descending order by payment
    jobs.sort(key=lambda job: job["payment"], reverse=True)
    # timeline will keep track of days that are still available
    # False = available for job, True = not available for job
    timeline = [False] * 7
    for job in jobs:
        # here we find the last day that the job can be completed
        maxTime = min(job["deadline"], 7)
        # Now we go through timeline and "place" the job at the 
        # last possible and available day. We then add the payment
        # to profit.
        for time in reversed(range(maxTime)):
            if timeline[time] == False:
                timeline[time] = True
                profit += job["payment"]
                break
    return profit
```
O(1) space because we create and return an array of size 7\
O(n log(n) ) time for the sort
