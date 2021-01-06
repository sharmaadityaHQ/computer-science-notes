1. Estimate YouTube's daily video storage requirements.

- No. of active users: 1B
- 1 in 1000 users uploads video
- No. of uploaders: 1B/1000 = 1M
- Avg. length of 1 video: 10 minutes
- Total uploaded video: 1M*10 = 10M minutes
- Total video size: 10M * 3MB = 30TB (size calculation below)
- To offer redundancy: 30TB * 3 = 90TB
- Multiple Resolutions: Assume 720p takes XMB then 480p+360p+240p+144p = X/2+X/4+X/8+X/16 = XMB; Total: 2XMB
- Total: 90TB * 2 = 180TB

- 2 hr movie average size: 4GB
- Optimized codec and compression savings: 90%
- 2 hr YouTube video average size: 0.4GB
- 1 min YouTube video average size: 3MB

2. Estimate cache requirements for video metadata.

- Things that are visible to the user like thumbnail, title, small description can be cached.
- Thumbnail is heavier as it is an image (10KB).
- We only need to cache popular (last 90 days) and evergreen videos. (10KB * 90 * 1M = 1TB RAM). Multiple computers will be needed. Taking 1 16GB computer (1TB/16GB = 64 nodes)
- To offer redundancy (64 * 3)
- If any node crashes then there will be a cascading failure as every node is running at peak capacity. Hence, keep each node at around 50% capacity. (64 * 3 * 2 = 500 nodes)

3. Estimate no. of processors required to process videos

- We need to process 10^7 mins of video in a day.
- Video processing involves Read + Processing + Write
- To process 1MB data we need 50ms = 10ms + 20ms + 20ms