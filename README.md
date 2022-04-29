# PWM-free novel boost converter for battery-powered IoT applications
A repository (to be updated) containing schematics, simulation results and physical layout of four power delivery circuits for comparison purposes.

## Summary
This design contains a novel non-PWM boost converter for extension of the battery life in IoT application, a traditional PWM boost converter and a switched-capacitor boost converter. The purpose is to perform a comparative analysis between the non-PWM boost converter and the other topologies for a 1.5 V battery source scenario in order to point out the significance of the non-PWM boost converter via the metrics of power efficiency, load regulation, quiescent current.

<img src="/Resources/chip.png" width="570" height="432" />

## Design Goals
IoT devices have become very widespread and as such the need for efficient power management has increased. Specifically, battery powered IoT devices in remote networks benefit greatly from efficient power delivery systems that can utilize as much of the stored energy as possible, extending service intervals and reducing maintenance costs. Our design contains a non-PWM novel boost converter topology that can deliver high load currents and maintain high output voltage even at low battery levels, alongside a traditional PWM and a switched-capacitor boost circuit. We aim to compare their performance characteristics for various load currents and minimum output voltages and examine their peak efficiency as well as their behavior as the input voltage drops due to battery discharge, thus concluding the useful lifetime they allow.

## Description
This design is composed of four circuits. A PWM boost converter, two versions of a novel non-PWM boost converter, one including a transformer on the chip and one without, and a switched-capacitor circuit. These circuits cover a range of battery powered IoT devices’ power demands with current draws in the range of single digit to a couple of tens of milliamperes.

The PWM boost converter contains a PWM block on chip, consisting of a Schmitt trigger and an Integrator that feeds a Comparator. Through its feedback, this implementation can provide good output voltage regulation but with the associated power consumption the PWM block itself brings. It will be the benchmark against which we compare the novel booster topologies.

<img src="/Resources/pwmboost.png" width="570" height="432" />

The switched-capacitor circuit will consist of a four-phase non overlapping clock generator and a four-stage parallel charge pump. It implements a burst-mode pulse frequency modulation to achieve better efficiency in a large range of load currents. Due to its nature, this circuit cannot provide very high load currents.

<img src="/Resources/scc.png" width="570" height="432" />

The PWM-free novel boost converter aims to bridge the gap between existing low-voltage low-current converters such as switched capacitor-converters and traditional PWM boost converters. It features a single stage topology and the absence of a PWM block that reduces total dissipated power and complexity, while maintaining high power efficiency.

<img src="/Resources/pwmfreeboost.png" width="570" height="432" />

The circuit consists of a bipolar junction transistor current mirror connected to a transformer with inverted secondary winding, forming a closed loop and generating positive feedback for voltage boosting. The current mirror transistor on the output side is driven by a pulse train and it determines the output voltage. The frequency of the pulses is largely determined by the transformer characteristics and the selected output goals.
This topology has the potential of high output current and maintaining a minimum output voltage for an extended period of time as the input voltage decreases, thus can be an excellent alternative with the potential to outperform traditional analogous circuits.

## Target Performance Summary

|  |  |
| ------ | ------ |
| Peak Efficiency | 77.5% |
| Minimum operational Vin -> Vout = 1.8 V | 0.43 V |
| Min Input Voltage for Iout 2.38 mA | 0.43 V |
| Max Iout for Vin of 1.5 V | 20 mA |
| Frequency for Vout = 1.8 V | 21.6 KHz |

## References
[1] Andreas Tsiougkos, Vasilis F. Pavlidis, “A PWM-free DC-DC Boost Converter with 0.43 V
Input for Extended Battery Use in IoT Applications”, 2021 IEEE International Midwest Symposium on Circuits and Systems (MWSCAS).

[2] A. Veerabathini and P. M. Furth, "A Low Output Voltage Ripple Fully-Integrated Switched-Capacitor DC-DC Converter," 2019 IEEE 62nd International Midwest Symposium on Circuits and Systems (MWSCAS).

## Team Members
B.Eng. Stefanos Kontogiannis\
M.Sc. Andreas Tsiougkos\
Ph.D. Vasilis F. Pavlidis
