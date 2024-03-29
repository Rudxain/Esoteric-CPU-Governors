# Esoteric CPU Governors

[Context](https://forum.xda-developers.com/t/cpu-governors-explained.1736168)

## BogoGov

Just like BogoSort, it sets the freq to a random value every `gen_rate` milliseconds, default param value is `1`. It doesn't even sample CPU load.

## Median

It locks the freq at the mid index.

Example: if the list is [600, 800, 1000], it doesn't choose 600MHz because it's closest to half the max, it chooses 800 because it's the median.

## ThanosCPU

Works like Median, but allows the CPU to randomly jump to min or max, with a bias based on workload.

So if the load is low, the bias is towards min speed. Conversely, if load is high, it biases towards max speed.

## Passive-Aggressive-CPU

If the kernel detects the user is being a jerk, the CPU will do the opposite of what MinMax does. It sets the freq to low when there's a high load, and high when idle.

The "jerk detection" algorithm is implementation-defined. It could be based on keyboard input, mouse movements, neuralink, all combined, etc...

