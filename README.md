```yaml
id: 187
date: 03-10-2026
media:
  - 187-1.jpg
```

I want to move the robot to a new architecture. Right now one Jetson runs everything: the camera, maps, navigation, the database, the web and the tunnel, with 8 GB of memory shared by all of them and the GPU. Plus the robot is blind behind, hence the 70 seconds of pushing a wall with its rear.

The idea is to split it into a brain and a body. The Jetson keeps only what needs the GPU: the camera, depth, localization, the map and the planner. My old Raspberry Pi 4 with 8 GB becomes the body: motors, steering, power, a 360° lidar, ToF sensors and bumpers, a rear camera, Forge, the HUD and video. And most importantly, collision protection on the Pi won't depend on whether the camera process is alive.

Along the way I went through the power telemetry. The 12 V step-down for the motors hits its limit on starts and sags to 11.3 V, and the battery current sensor showed 7.6 A against a ceiling of 8.2 A, so it most likely just clipped the peaks. In the new layout every branch has its own fuse, and the Pi can power off and restart a hung Jetson. And there will be a proper power button: 93 of 104 Jetson boots came after the power was simply pulled.
