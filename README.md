# baekjoon_tip

**input 보다 sys.stdin.readline() 로 입력받는게 빠름.
sys.stdin.readline()는 /n 도 입력 받아서 .strip() 로 지워주기


```python
import heapq

def solve(arr):
    sum = 0
    heap_max = []
    heap_min = []
  
    for i in range(len(arr)):
        new = arr[i]
    
        if i ==0:
            heapq.heappush(heap_min, new)
        elif i%3 == 0:
            if(new <heap_min[0]):
                heapq.heappush(heap_max, -new)
            else:
                heapq.heappush(heap_max, -heapq.heappop(heap_min))
                heapq.heappush(heap_min, new)
        else:
            if(new <heap_min[0]):
                heapq.heappush(heap_max, -new)
                heapq.heappush(heap_min, -heapq.heappop(heap_max))
            else:
                heapq.heappush(heap_min, new)
        sum +=heap_min[0]
    return sum
```
