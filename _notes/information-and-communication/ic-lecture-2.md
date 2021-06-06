---
date: 2021-05-26
title: IC Lecture 2
author: Agrim Rawat
code: ec5.102
number: 2
---

## Communication

### Definition

**Communication** can be defined as transmission, reception and reconstruction of a transmitted signal.

### Some Terms

1. Channel: It is the medium/space through which the information signal is transmitted. It is not completely under the control of the person designing the system.
2. Noise/Disturbance: It is error or undesired random disturbance of a useful information signal. This could be due to environmental disturbances or overlapping with other unwanted signals.
3. Modulation: It is the process of varying a property of a carrier signal, with the original signal (modulating signal) containing information to be transmitted.
4. Amplification: Increasing the power of the signal.

### Communication System Models

![img-50](/assets/images/ic_lec2_basiccommmodel.png)

1. Transmitter side<br>The source sends out information which is modulated, amplified and sent across the channel through an antenna.

![img-50](/assets/images/ic_lec2_transmitter.png)

1. Receiver side<br>The receiver receives the signal through the channel which is then demodulated and decoded to estimate the signal.

![img-50](/assets/images/ic_lec2_receiver.png)

**NOTE:**

- In ideal situations there is no noise that gets added to the transmitted signal. But in real life, there exists some noise in the received signals. So, a mathematical model which takes the noise into account to interpret the information from the signal is needed.
- To decrease the error in the received signal we can send the signal repeatedly for a long time which is also called **channel coding**. This will be decoded on the receiving side to estimate the information in the signal.

### User requirements from a communication system

1. Low probability of error.
2. Fast reception/high rate communication.
3. High Range communication-captured in the channel itself.
4. Latency - Time delay between transmission and loading is very small.

### Types of Communication Models

1. Point-to-Point<br>In point-to-point system, a signal is transmitted between two points of communication through a channel.
2. One source, multiple receivers or Broadcast<br>Examples : radio broadcast, wireless cellular down-link.<br>It has the following sub-types:
    - The transmitter sends all receivers the same signal
    - The transmitter sends different signals to different receivers
    - Both
3. One receiver, multiple sources or Multiple access channel<br>Examples : Cellular up-link

![img-50](/assets/images/ic_lec2_commexamples.png)