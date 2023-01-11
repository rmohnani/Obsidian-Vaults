---
tags:
- leetcode
---
**Title**: 355. Design Twitter
**Link**: https://leetcode.com/problems/design-twitter/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/heap_pq 
**Status**: #leetcode/status/completed  
**Time**: 01 : 17 : 10

---
# Problem Statement
Design a simplified version of Twitter where users can post tweets, follow/unfollow another user, and is able to see the `10` most recent tweets in the user's news feed.

Implement the `Twitter` class:

-   `Twitter()` Initializes your twitter object.
-   `void postTweet(int userId, int tweetId)` Composes a new tweet with ID `tweetId` by the user `userId`. Each call to this function will be made with a unique `tweetId`.
-   `List<Integer> getNewsFeed(int userId)` Retrieves the `10` most recent tweet IDs in the user's news feed. Each item in the news feed must be posted by users who the user followed or by the user themself. Tweets must be **ordered from most recent to least recent**.
-   `void follow(int followerId, int followeeId)` The user with ID `followerId` started following the user with ID `followeeId`.
-   `void unfollow(int followerId, int followeeId)` The user with ID `followerId` started unfollowing the user with ID `followeeId`.

---
# My Solution
```python
class User:
    def __init__(self, userId: int):
        self.userId = userId
        self.user_tweets = []
        heapq.heapify(self.user_tweets)
        self.follows = {self.userId}
    
    def post_tweet(self, tweetId: int, tweet_order: int):
        heapq.heappush(self.user_tweets, (tweet_order, tweetId))
    
    def follow(self, followeeId: int):
        self.follows.add(followeeId)
    
    def unfollow(self, followeeId: int):
        if followeeId in self.follows:
            self.follows.remove(followeeId)

class Twitter:

    def __init__(self):
        self.user_id_to_Users = {}
        self.tweet_order = -1

    def initialize_user(self, userId: int) -> None:
        if userId not in self.user_id_to_Users:
            user = User(userId)
            self.user_id_to_Users[userId] = user

    def postTweet(self, userId: int, tweetId: int) -> None:
        self.initialize_user(userId)
        self.user_id_to_Users[userId].post_tweet(tweetId, self.tweet_order)
        self.tweet_order -= 1
        

    def getNewsFeed(self, userId: int) -> List[int]:
        self.initialize_user(userId)
        user = self.user_id_to_Users[userId]
        follower_heaps = [self.user_id_to_Users[f].user_tweets for f in user.follows]
        feed = list(heapq.merge(*follower_heaps, key = lambda x: x[0]))
        heapq.heapify(feed)
        ret = []
        feed_count = 10
        while feed_count > 0 and feed:
            ret.append(heapq.heappop(feed)[1])
            feed_count -= 1
        return ret

    def follow(self, followerId: int, followeeId: int) -> None:
        self.initialize_user(followerId)
        self.initialize_user(followeeId)
        follower = self.user_id_to_Users[followerId]
        follower.follow(followeeId)
        

    def unfollow(self, followerId: int, followeeId: int) -> None:
        self.initialize_user(followerId)
        self.initialize_user(followeeId)
        follower = self.user_id_to_Users[followerId]
        follower.unfollow(followeeId)
        


# Your Twitter object will be instantiated and called as such:
# obj = Twitter()
# obj.postTweet(userId,tweetId)
# param_2 = obj.getNewsFeed(userId)
# obj.follow(followerId,followeeId)
# obj.unfollow(followerId,followeeId)
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution

notes: 
time complexity: 
space complexity: 

---

