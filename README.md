# Lab 4: Concept Review

This lab reviews the foundational concepts of algorithms and data structures that we have covered in the first half of the course. 

**Instructions:** To complete this lab, you may work in groups, but you must write your solutions yourself. Choose two of the topics below that you need to review and complete the corresponding problems. Where relevant, you are given the answer and must provide the justification as your solution. Once you have completed the lab, push your changes to your forked repository.

**Topics:** asymptotic analysis, data structures, empirical comparison of algorithms, pseudocode, greedy algorithms. 

## Asymptotic Analysis

1. Use the rules from lecture 07 to prove that $T(n) = 5 \log n + 7n$ is $\mathcal{O}(n)$.

2. True/False/Possibly: $T(n)$ is $\mathcal{O}(n^2)$?

**Answer**: Yes

**Justification**:

3. True/False/Possibly: $T(n)$ is $\Omega(n \log n)$?

**Answer**: No

**Justification**:

4. For any algorithm, we can give a trivial lower bound. What is that lower bound?

**Answer**: $\Omega(1)$

**Justification**:

5. Is there a corresponding trivial upper bound? Why or why not?

**Answer**: No

**Justification**:


## Data Structures

1. You are programming a robot to navigate a maze. As the robot moves forward, it records each intersection it passes. When it hits a dead end, it needs to retreat to the most recently visited intersection to try a different path.

**Answer**: Stack

**Justification**: When a program is running in a stack it goes based on LIFO (Last In First Out). This is important because when the robot hits a dead end, it's program requires it to backtrack to most recently visited intersection, which would be the last piece of data added

2. A server receives a massive influx of data packets from a streaming video application. To prevent the video from skipping or playing out of order on the user's end, the server must process and forward these packets in the exact sequence they were received.

**Answer**: Queue

**Justification**: This program is a Queue because a Queue works by going off of FIFO (First In First Out), and in this case the server is processing and forwarding the packets in the order of what it recieved first to what it recieved last

3. An atmospheric monitoring system reads temperature data from 10,000 sequentially numbered sensors (IDs 0 through 9999). Throughout the day, the system needs to constantly update and read the current temperature of randomly selected sensors based on their ID number to build localized weather maps.

**Answer**: Array

**Justification**: This is an Array because the data is in sequential order and is indexed. 

4. You are building a lightweight syntax checker for a code editor. Its sole job is to scan a document and ensure that every opened parenthesis `(`, bracket `[`, and brace `{` is matched with its corresponding closing character in the correct nested order.

**Answer**: Stack

**Justification**: A stack is required over a Queue because you can use (), [], and {}, inside of eachother, and if it ran on a Queue it could cause complications. For instance if a sentence goes "Dr. Jones discussed the new smoking policy (an authority on the issue under review [smoking cessation strategies]) at length in his paper." a Queue would be stuck on the paranthesis and pair the ( with the ] which would be incorrect, while a stack would properly move to the brackets and correctly pair the () and []

## Empirical Comparison of Algorithms

1. A student is benchmarking an algorithm that takes a list as its input. They run it on progressively larger randomly generated lists, doubling the number of elements ($n$) and record the following execution times:

- $n = 1000$: 0.12 seconds
- $n = 2000$: 0.94 seconds
- $n = 4000$: 7.61 seconds
- $n = 8000$: 60.85 seconds

 Based on this empirical data, what is the most likely asymptotic time complexity of the algorithm? **Hint**: Calculate the doubling ratio between each pair of consecutive runs.

 **Answer**: Cubic time complexity, $\mathcal{O}(n^3)$

**Justification**: The most likely asymptotic time complexity is cubic because everytime the sample size doubles the execution time on average octuples in size which matches the ratio of $\mathcal{O}(n^3)$

 2. Two students write separate algorithms to compute a metric over an array of 10 million integers. Both algorithms perform exactly one mathematical operation per element, meaning both have a theoretical time complexity of $O(N)$. However, during benchmarking, Algorithm A consistently runs 15x faster than Algorithm B. Why might theoretical Big-O analysis fail to predict this massive performance gap? 

**Answer**: The theoretical Big-O analysis might fail to predict the massive performance gap because of the dropping constants property. While both algorithms have a theoretical time complexity of $O(N)$ one could be just T(N) = N while the other equals T(N) = 15n

 3. Scenario: To measure the running time of algorithms for an empirical comparison, a developer writes the following benchmarking script:

```python
import time

large_array = [i for i in range(1000000)]
start = time.time()
myAlg(large_array)
end = time.time()

print("Time:", end - start)
```

They run this script exactly once for each algorithm on their laptop while streaming a movie in the background. Identify at least three distinct methodological flaws in this benchmarking setup that make the results unreliable.

**Answer**: One problem could be how little they're running the script. To get more accurate results they should run the script multiple times to get an average. Another problem is that they are still using the laptop for other activities which moves a portion of the focus of the GPU away from the script, which will result in it running slower. A third problem could be that the array should have random values inside of it for the length of the list since in real world applications the data wouldn't be in sequential order

## Pseudocode

1. Analyze the exact number of times the `do_work()` function is called in the following pseudocode, assuming $N \ge 1$.

```
count = 0
for i = 1 to N do
    for j = i to N do
        do_work()
```

Write a closed-form expression for the number of times `do_work()` is called in terms of $N$.

2. Analyze the exact number of times the `do_work()` function is called in the following pseudocode, assuming $N \ge 1$.

```
i = N
while i > 0:
    for j = 1 to i:
        do_work()
    i = floor(i / 2)
```

If $N=16$, how many times is `do_work()` called?

**Answer**: 31

**Justification**:

## Greedy Algorithms

You are organizing a film festival but only have access to a single screen. You are given a list of $n$ films, each with a specific `start_time` and `end_time`. You want to screen the maximum number of films possible.

Consider the following three greedy strategies:

- **Shortest First**: Always pick the film with the shortest duration (that doesn't conflict with already chosen films).
- **Earliest Start**: Always pick the film that starts the earliest (that doesn't conflict).
- **Earliest Finish**: Always pick the film that finishes the earliest (that doesn't conflict).

Which of these three strategies guarantees an optimal solution (maximum number of films)? For the two strategies that fail, provide a counter-example (a small set of film times) where the greedy choice results in a sub-optimal schedule.

**Answer**: The earliest finish strategy guarantees an optimal solution.

**Justification**: