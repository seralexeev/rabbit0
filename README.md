```yaml
id: 188
date: 03-10-2026
media:
  - 188-1.jpg
  - 188-2.jpg
```

Drew all the wiring for the new architecture with Claude: every wire, pin, protocol and gauge. A few fun things came up along the way:

-   the RoboClaw E-stop latches by default and its input is pulled up, so a broken wire means "go ahead". We flipped it: the Pi holds the line only while the safety process is alive, and a broken wire or a hang means stop
-   the bumpers don't go to the stop line, otherwise a robot that hit a wall couldn't back away from it
-   the RoboClaw datasheet says outright that USB drops in a noisy environment and doesn't recover on its own. The main link will be UART
-   each of the four ToF sensors sits on its own I2C bus, so no address changes and one hung bus doesn't kill the others
-   the LD19 is discontinued, the lidar will be an RPLIDAR C1

The shopping list came to ~A$825, more than half of everything I already have.
