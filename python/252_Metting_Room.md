#### Time complexity:
O(nlogn)

#### Space complexity:
O(1)

#### 思路：
利用sort实现


```python
class Solution:
    def canAttendMeetings(self, intervals: List[List[int]]) -> bool:
        if not intervals:
            return True
        intervals.sort()
        for i in range(1, len(intervals)):
            prev_end_time = intervals[i - 1][1]
            start_time = intervals[i][0]
            if start_time < prev_end_time:
                return False
        return True
```