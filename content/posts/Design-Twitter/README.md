---
id: 1d57e332-de10-8009-ac14-ecfe845727cd
title: Design Twitter
created_time: 2025-04-14T18:55:00.000Z
last_edited_time: 2025-10-15T18:11:00.000Z
difficulty_level: 'Meduim '
number: null
commit_to_git_hub: 'Yes'
leetcode_problem_list:
  - Neetcode - 150
problem_link: https://leetcode.com/problems/design-twitter/description/
my_confidence_level: Low
last_solved: null
concept_involved:
  - HashSet
  - HashTables
  - heaps
companies_asked:
  - Amazon
problem_name: Design Twitter

---

```python
class Twitter:

    def __init__(self):
        self.count = 0 
        self.followMap = defaultdict(set) # set of all followeeids
        self.tweetMap = defaultdict(list) # [count, tweetid]
        

    def postTweet(self, userId: int, tweetId: int) -> None:
        self.tweetMap[userId].append([self.count,tweetId])
        self.count -= 1
        

    def getNewsFeed(self, userId: int) -> List[int]:
        res = []
        minHeap = []

        self.followMap[userId].add(userId)
        for followeeId in self.followMap[userId]:
            if followeeId in self.tweetMap:
                index = len(self.tweetMap[followeeId]) - 1
                count, tweetId = self.tweetMap[followeeId][index]
                heapq.heappush(minHeap, [count, tweetId, followeeId, index-1])

        while minHeap and len(res) < 10:
            count, tweetId, followeeId, index = heapq.heappop(minHeap)
            res.append(tweetId)
            if index >= 0:
                count, tweetId = self.tweetMap[followeeId][index]
                heapq.heappush(minHeap, [count, tweetId, followeeId, index - 1])
        return res




        

    def follow(self, followerId: int, followeeId: int) -> None:
       
        self.followMap[followerId].add(followeeId)
        

    def unfollow(self, followerId: int, followeeId: int) -> None:
        if followeeId in self.followMap[followerId]: 
            self.followMap[followerId].remove(followeeId)


# Your Twitter object will be instantiated and called as such:
# obj = Twitter()
# obj.postTweet(userId,tweetId)
# param_2 = obj.getNewsFeed(userId)
# obj.follow(followerId,followeeId)
# obj.unfollow(followerId,followeeId)
```

# **Time & Space Complexity**

**Time complexity: O(nlog⁡n)*****O*****(*****n*****log*****n*****) for each getNewsFeed()*****getNewsFeed*****() call and O(1)*****O*****(1) for remaining methods.Space complexity: O(N∗m+N∗M+n)*****O*****(*****N*****∗*****m*****+*****N*****∗*****M*****+*****n*****)**

*   Time complexity: *O*(*n\_log\_n*) for each *getNewsFeed*() call and *O*(1) for remaining methods.

    **O(nlog⁡n)**

    **getNewsFeed()**

    **O(1)**

*   Space complexity: *O*(*N\_∗\_m*+*N\_∗\_M*+*n*)

    **O(N∗m+N∗M+n)**

> Where nn is the total number of followeeIdsfolloweeIds associated with the userIduserId, mm is the maximum number of tweets by any user, NN is the total number of userIdsuserIds and MM is the maximum number of followees for any user.
