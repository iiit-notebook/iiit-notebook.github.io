---
title: ICT Lecture 4
code: cs0.100
number: 4
---
## Rectifier

Its function is to convert alternate current to direct current.
What we need is a "current steering block" to take this output with its constantly switching polarity, and put it back out in only one single direction.
One implementation is to use switches in a diamond configuration, turning them on and off according to our requirement, but implementing this with mechanical switches would be very difficult.
We can instead use *diodes*. A diode is a 2-terminal electronic device, which allows current to pass through it when *forward-biased* and will block the current when *reverse-biased*. Thus we can construct what is known as a **bridge rectifier**.

![block](/assets/images/ict004fig1.png)

## Filter

After rectifying the wave and limiting it to one polarity, we get quite a bumpy waveform ($\lvert\sin{x}\rvert$), so this wave form has to be filtered to allow us to get something which better approximates a pure DC. This is done by filtering, and to do this we attach a capacitor in parallel. The charge-discharge cycle of the capacitor causes the current to not vary as much.
There is a bit of a "ripple" still left over, and we select the rating of our capacitor accordingly.  Since the ripple is formed by the charge/discharge of the capacitor, we can reduce the ripple by selecting C such that discharge time constant is much greater than the period of our rectified wave.
$$R_{L} C >> T; T= \frac{1}{f}; $$
where $f$ is the frequency of the rectified wave.
$$\frac{V_{L}}{I_{Lmax}} >> \frac{1}{f}$$
$$C >> \frac{I_{Lmax}}{fV_{l}}$$

While designing this we use 
$$R_{LC} = \alpha\frac{1}{f}$$
where $\alpha$ is our *design parameter*

Suppose $V_{Lmax} = 5V; I_{Lmax} = 1A$.
Then if $f = 100Hz$, 
$$C = \alpha \frac{1}{(100)(5)}$$
Instead, if $f = 50kHz$, 
$$C = \alpha \frac{1}{(5\times10^4)(5)}$$

So by increasing the frequency, we greatly decrease the capacitance needed to filter our output, something of great significance in appliances like mobile chargers.

## Regulator

For the purpose of regulating our output to be a constant voltage, we take the assistance of a **zener diode**, a special kind of diode with the amazing property that under reverse bias, it can lock the voltage to a fixed value under 'zener breakdown'.

![block](/assets/images/ict004fig2.png)

We place our zener diode in reverse bias in parallel across our load. We also need a minimum *'knee current'* across the zener in order to ensure it behaves as a voltage regulator.
We used the fact that because of this the voltage across the load is constant and equal to zener voltage, and a simple application of Ohm's law, to get the useful equations
$$I_{L} = I_{S} - I_{Z} = V_{Z}(\frac{1}{R_{L}})$$
$$I_{S} = (V - V_{Z})(\frac{1}{R_{S}})$$

### Zener regulator design
![block](/assets/images/ict004fig3.png)
