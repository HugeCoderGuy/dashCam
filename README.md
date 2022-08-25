# Raspberry Pi Dash Camera
Like anyone else who needs a dash camera, has the hardware sitting around from past projects, and enjoys learning, I decided to build my own!
![alt text](https://github.com/HugeCoderGuy/dashCam/blob/main/example_video.gif)
Above video captures the chaos of driving through Kings Beach (Tahoe) durring summer.

## Features
- Video capture and saving implemented in seperate threads for improved preformance
- Memory management function that deletes 7 day old videos, double checks system memory, and will delete additional videos if available memory is less than 5GB
- Long drives greater than 30mins are seperated into 30min segments with intermittent system memory checks
  - RasPi cross checks ignition before powering down so that power cycling car doesn't prevent next video session
- Videos continue for 30s after car powers off and videos are labeled with ignition state when closing out
- Timed relay powers down RasPi after 60s to prevent unnecessary current draw from car battery

Overall, my car hasn't died on me yet and my not-so-official circuit has held up. The circuit powering the pi can be seen below.
![alt text](https://github.com/HugeCoderGuy/dashCam/blob/main/raw_honda_fit.jpg?raw=true)
