---
title: ICT Lecture 3
author: Pratyaksh Gautam
code: cs0.100
number: 3
---
## Batteries and charging

All electronic systems (hardware) require DC power to function. Batteries function as portable sources of DC power.
We can also use a DC *power supply* instead, which takes in standard AC mains and converts it to a stable DC current.
There are also *'battery eliminators'*, power supplies designed to replace the batteries.
Our main topic of discussion will be **battery chargers**.

Both power supplies and chargers have the same basic elements:
- Rectifier
- Filter
- Regulator

The *rectifier* and *filter* work to convert DC to AC, and the *regulator* steadies the output current.
Battery chargers have an additional block to handle the [charge profiles](https://support.delta-q.com/hc/en-us/articles/360015387312-What-is-an-Algorithm-Charge-Profile-), but we won't discuss that in much detail.

![block](/assets/images/ict003fig1.png)
For the most part, the graph says it all.

## AC to DC Conversion

For AC mains there are two popular standards, 220V/50Hz and 110V/60Hz, in India we use the former.

*Why is AC mains a sinusoidally-varying wave?*
AC Mains varies as a sinusoidal function, essentially because of the way it is commonly generated.
We use turbines, which are rotated in some form or the other to generate our electricity, often by steam or falling water. Assuming an ideal case where we are able to rotate the turbines at a constant angular velocity $\omega$
Then the magnetic flux through the coil which we use in the generator is given by $\phi = nAB\cos{\omega t}$, and by Faraday-Lens' Law, we have the induced potential difference,
$$E = - \frac{d\phi}{dt} = nAB\omega \sin{\omega t}$$

To get DC, we must first *rectify* the sine wave, so that it only has one polarity, and then we must *filter* it to smooth it out into a better, more stable current. These are our two main steps.

We must also lower the voltage of the current with a *transformer*, since most household appliances run on around ~10V to ~24V. We can conveniently change the transformation ratio by changing the number of coils, since in a transformer
$$\frac{V_{ P }}{V_{ S }} = \frac{N_{ P }}{N_{ S }}$$

We also have to deal with varying load conditions. When a large current is drawn from a battery, in practical situations its peak voltage is reduced. This is a natural consequence of Ohm's Law when a battery has any internal resistance. We can calculate the terminal potential difference $V_{ 0 }$ as
$$V_{ 0 } = V_{ in } - IR_{ in } = \frac{R_{ load }}{R_{ load } + R_{ in }}$$
where $V_{ in }$ is the EMF of the cell.

## Switching Mode Power Supply (SMPS)

As different regions run on different AC standards, it would be nice to have something that can work on either of the two popular standards, which is exactly what an SMPS does.
The basic idea is as follows:
1. put the AC through a rectifier and filter so you get DC, which is still at a high voltage.
2. then a switch converts this to a very high frequency AC (~50kHz).
3. this AC is then put through a transformer to get a low voltage AC, still at 50kHz.
4. now we pass this again through a rectifier and filter to get low voltage DC.
5. finally this output is regulated before being sent to the appliance.
6. the switch itself is controlled according to the need of the appliance by a switch control.

*Note: The first two lectures of the course were very introductory and general in nature, and did not require detailed notes.*
