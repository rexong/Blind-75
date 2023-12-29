<frontmatter>
  title: Graphs - Course Schedule
</frontmatter>

# [Course Schedule](https://leetcode.com/problems/course-schedule/)
#### Difficulty: Medium

### Intuition
Create a adjacency list for each course. <br>
Indication that course cannot be completed when there is a cycle in the graph. <br>
Perform DFS on every course, and its adjacency list.

### Contraints
- $1\leqslant$ numCourses $\leqslant 2000$
- $1\leqslant$ length of prerequisites$\leqslant 5000$
- Every element in prerequisites is length of 2 

## Approach
1. Initialise a dictionary to map course to its prerequisites
2. Create the adjacency list 
3. Initialise empty set as path
4. Define DFS with course
    1. If course in path, return False
    2. If adjacency list is empty, return True
    3. Add course to path
    4. Perform DFS on every prerequisite
        1. If DFS return False, return False
    5. Remove course from path
    6. Empty the prerequisites from the course
    7. Return True
4. For every course
    1. Perform DFS, if False, return False
5. Return True

### Complexity
#### Time Complexity: O(V + E)
V is the number of courses, E is the length of prerequisites. 
Every course and path will be visited once.
#### Space Complexity: O(V + E)
For the dictionary
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        d = defaultdict(set)
        for course, prereq in prerequisites:
            d[course].add(prereq)
        path = set()

        def dfs(course):
            if course in path:
                return False
            if not len(d[course]):
                return True
            path.add(course)
            for prereq in d[course]:
                if not dfs(prereq):
                    return False
            path.remove(course)
            d[course].clear()
            return True

        for course in range(numCourses):
            if not dfs(course):
                return False
        return True
```
</panel>

