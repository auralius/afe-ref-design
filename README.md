# Analog Front End Design
A reproducible, low-noise analog front end for millivolt bridge sensors (e.g., MPS20N0040D, typically used for __hobbyist__ sphygmomanometer), using AD620 instrumentation amplifier and LM358 level shift. This analog front end should also work for other millivolt instruments.


## TINA-TI

DC simulation with TINA-TI:

<img src="https://github.com/auralius/afe-ref-design/blob/main/images/AFE.png" width="600"> 

Instrumentation amplifier gain:

$$ G = 1 + \frac{49.4\text{k}\Omega}{R_g} $$

LM358 offset:

$$ \frac{22\text{k}}{4.7\text{k}} \times 3.3 V \approx 0.7 V$$



## MPS20N0040D
The MPS20N0040D is a millivolt-level bridge (≈50–100 mV full-scale; 4–6 kΩ)

| <img src="https://github.com/auralius/afe-ref-design/blob/main/images/mps20n0040d_1.png" width="300"> | <img src="https://github.com/auralius/afe-ref-design/blob/main/images/mps20n0040d_2.png" width="300"> |
| ----------------------------------------- | ----------------------------------------- |

## LM358
This will be used to offset the instrumentation amplifier, giving headroom for possible undershoot or for signal that goes both ways (positive and negative).

<img src="https://github.com/auralius/afe-ref-design/blob/main/images/lm358.png" width="300"> 

## AD620
This is the instrumentation amplifier that is relatively cheap and widely available in Indonesian market.

| <img src="https://github.com/auralius/afe-ref-design/blob/main/images/ad620_1.png" width="150"> | <img src="https://github.com/auralius/afe-ref-design/blob/main/images/ad620_2.png" width="150"> |
| ----------------------------------------- | ----------------------------------------- |

## Prototype 
We will use STM32F411CE (the black pill) as our digital processor.

| <img src="https://github.com/auralius/afe-ref-design/blob/main/images/prototype1.png" width="250"> | <img src="https://github.com/auralius/afe-ref-design/blob/main/images/prototype2.png" width="330"> |
| ----------------------------------------- | ----------------------------------------- |

## Safety & Notes

- The MPS20N0040D is fragile—avoid over-pressure.
- If powering from USB, beware ground noise from the host PC. A ferrite on the USB cable can help.

## Next-to-Do
- 50/60 Hz notch filter (hum killer), currently there is a simple low pass filter at 59 Hz.
- PCB layouting.
- Performance evaluations.

## Credits

- Instrumentation amplifier intro: https://www.youtube.com/watch?v=O0-iczIq1aU
- INA333 review with AD620 suggestion: https://blog.robertelder.org/cjmcu-333-ina-333-instrumentation-amplifier/
- A Designer’s Guide to Instrumentation Amplifiers (3rd Edition) https://www.analog.com/media/en/training-seminars/design-handbooks/designers-guide-instrument-amps-complete.pdf

