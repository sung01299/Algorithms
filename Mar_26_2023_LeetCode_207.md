# 207. Course Schedule

**Difficulty: Medium**

*Related Topics: DFS/BFS, Graph, Topological Graph*

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return true if you can finish all courses. Otherwise, return false.

Example 1:

Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0. So it is possible.

Example 2:

Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.

## Code:

```python
from collections import deque

class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        degree = {}
        for i in range(len(prerequisites)):
            if prerequisites[i][0] in degree:
                degree[prerequisites[i][0]] += 1
            else:
                degree[prerequisites[i][0]] = 1

        for i in range(numCourses):
            if i not in degree:
                degree[i] = 0

        myq = deque()
        for i in degree:
            if degree[i] == 0:
                myq.append(i)
        while myq:
            curr = myq.popleft()
            for i in prerequisites:
                if i[1] == curr:
                    degree[i[0]] -= 1
                    if degree[i[0]] == 0:
                        myq.append(i[0])
        
        if sum(degree.values()) == 0: return True
        else: return False
```        
