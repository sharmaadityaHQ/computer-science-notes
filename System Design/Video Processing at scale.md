## How Netflix onboards new content?

- Different video formats (High quality, intermediate, low) as internet connection qualities differ.

- Different resolutions (1080p, 720p) for different device sizes.

- Number of videos to be processed (No. of formats * No. of resolutions)

- Netflix breaks videos into chunks. 1 task includes processing 1 chunk in 1 resolution and 1 format.

- Initially the video file was broken into chunks of 3 mins each. Now it is divided into multiple shots of 4 seconds each to create a scene.

- Netflix treats the video as a set of chunks. If the user arbitrarily goes to different points in the video then the prediction algorithm detects it as a sparse video and does not send lots of data. It only sends the data the user wants. If the video is detected as dense then it predictively fetches the future parts for display to the user.

- Amazon S3 is used to store the video chunks. S3 is used to store static data.

- Netflix also provides open connect servers to internet service providers, which acts like a cache of movies. Most requests to Netflix can be served by this cache, and the remaining are sent over the network. This reduces the bandwidth and time required for Netflix to operate at scale.