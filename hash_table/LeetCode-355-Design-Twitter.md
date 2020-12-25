### LeetCode-355-Design-Twitter

> 题目链接

[LeetCode-355-Design-Twitter](https://leetcode.com/problems/design-twitter/)

> 思路

用hashMap检索每个用户的关联关系和主动发的微博，通过关联关系，找出n个人的微博，寻找出最新的10条

> 代码

```java
class Twitter {
    private static int timestamp = 0;
    private Map<Integer, User> userMap;
    
    public Twitter() {
        userMap = new HashMap<>();
    }
    
    public void postTweet(int userId, int tweetId) {
        if (!userMap.containsKey(userId)) {
            User new_user = new User(userId);
            userMap.put(userId, new_user);
        }
        
        userMap.get(userId).post(tweetId);
    }
    
    public List<Integer> getNewsFeed(int userId) {
        List<Integer> result = new ArrayList<>();
        if (!userMap.containsKey(userId)) {
            return result;
        }
        Set<Integer> tempSetUsers = userMap.get(userId).followed;
        PriorityQueue<Tweet> maxHeap = new PriorityQueue<>(tempSetUsers.size(), (a, b) -> b.time - a.time);
        for (int u : tempSetUsers) {
            Tweet head = userMap.get(u).tweet_head;
            if (head != null) 
                maxHeap.offer(head);         
        }
        int count = 0;
        while (!maxHeap.isEmpty() && count < 10) {
            Tweet t = maxHeap.poll(); 
            result.add(t.tweet_id);
            count++;  
            if (t.next != null)
                maxHeap.offer(t.next);
        }
        return result;
    }
    
    public void follow(int followerId, int followeeId) {
        if (!userMap.containsKey(followerId)) {
            User new_user1 = new User(followerId);
            userMap.put(followerId, new_user1);
        }
        if (!userMap.containsKey(followeeId)) {
            User new_user2 = new User(followeeId);
            userMap.put(followeeId, new_user2);
        }
        userMap.get(followerId).follow(followeeId);
    }
    
    public void unfollow(int followerId, int followeeId) {
        if (!userMap.containsKey(followerId) || followerId == followeeId) {
            return;
        }
        userMap.get(followerId).unfollow(followeeId);
    }
    
    private class User {
        public int user_id;
        public Set<Integer> followed;
		public Tweet tweet_head;
        
        public User (int id) {
			this.user_id = id;
			followed = new HashSet<>();
			follow(user_id);
			tweet_head = null;
		}

		public void follow (int id) {
			followed.add(id);
		}

		public void unfollow (int id) {
			followed.remove(id);
		}
        
        public void post (int t_id) {
            Tweet tweet = new Tweet(t_id);
            tweet.next = tweet_head;
            tweet_head = tweet;
        }
    }
    
    private class Tweet {
        public int tweet_id;
		public int time;
		public Tweet next;

		public Tweet(int id){
			this.tweet_id = id;
			time = timestamp++;
			next = null;
		}
    }
}
```

> 复杂度分析

getNewsFeed，需要查表，遍历相关联的用户，取最新的10个数据，时间复杂度O(n * m)

额外使用hashMap来保存数据,每个用户的微博链表保存，空间复杂度O(n * m)

> 总结

Runtime: 20 ms, faster than 99.89% of Java online submissions for Design Twitter.

Memory Usage: 44.5 MB, less than 81.10% of Java online submissions for Design Twitter.
