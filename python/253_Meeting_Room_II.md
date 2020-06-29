Leetcode: https://leetcode.com/problems/meeting-rooms-ii/

Finish Date: 5/28/2020

Solved with Hint: No

Approach: Heap 

The underlying rule of getting a new meeting room is that all current meeting room's ending time is later than new meeting's start time.
Considering this, we need a data structure to store the end time of current meeting and get earliest finish time efficiently. Heap is a good choice intuitively.


```python
import heapq
class Solution:
    def minMeetingRooms(self, intervals: List[List[int]]) -> int:
        if not intervals:
            return 0
        intervals.sort()
        heap = []
        heapq.heappush(heap, intervals[0][1])
        max_rooms = 1
        for i in range(1, len(intervals)):
            if intervals[i][0] < heap[0]:
                heapq.heappush(heap, intervals[i][1])
                max_rooms = max(max_rooms, len(heap))
            else:
                heapq.heappop(heap)
                heapq.heappush(heap, intervals[i][1])
        return max_rooms
```
