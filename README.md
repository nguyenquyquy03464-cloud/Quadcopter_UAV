# Quadcopter_Mission_Planner_UAV compete build
UAV is the future field of Robotics, as Robotic engineer experiment in the drone field is reasonable. base on my experiment i will give out a simple guide to build up a drone.



hardware component 

- Pixhawk 6x
- SiK Telemetry Radio V3
- ELRS receiver
- RTX & VTX
- tarot 650 frame

Assembly 

i built my drone base on this diagram

<img width="2304" height="3153" alt="Image" src="https://github.com/user-attachments/assets/70dbcb62-5054-44e7-b88c-3ba91eeaf4a5" />


<img width="3024" height="4032" alt="Image" src="https://github.com/user-attachments/assets/f08fb547-8b18-4a83-95a3-42e7c9b84203" />

put your Pixhawk cube in the central of your drone because the IMU is put in there and the arrow of GPS unit on the same line with arrow of the pix

<img width="3024" height="4032" alt="Image" src="https://github.com/user-attachments/assets/3cea5f1a-95cb-491b-85f6-9901bd15ce74" />

install firmware

i use Mission planner. Reasons , the software is built quiet good with huge community to support

https://ardupilot.org/planner/index.html

in the other hand, i use ExpressLRS  radio it requires more steps to set up with compare 

https://www.youtube.com/watch?v=N0ajKoef3qs

https://docs.px4.io/main/en/getting_started/rc_transmitter_receiver

https://www.expresslrs.org/quick-start/installing-configurator/

after basic set up we can go to tuning part. in this part we will work with a important part of automatic controller system that is PID controller. PID is sort for Proportional-Integral-Derivative Controller  in Robotic field, it helps drone operate stably.

a PID (Proportional-Integral-Derivative) controller is the brain stem of a quadcopter. It is a continuous feedback loop that takes the desired state (e.g., "hover perfectly level") and compares it to the actual state measured by the onboard gyroscope and accelerometer. The difference between these two states is the Error.

Here is the fundamental equation running inside the flight controller:

<img width="542" height="139" alt="Image" src="https://github.com/user-attachments/assets/8e787b5e-701e-44c1-bd60-9163f82c2448" />

Where:

- u(t) is the output control signal sent to the motors.
- e(t) is the current error (Desired Angle - Actual Angle).$
- K_p, K_i, and K_d are the tunable gains (multipliers) for each term.

Let's break down exactly what each term does to the drone's flight dynamics.

1. Proportional (P): The Muscle
The P-term looks at the present error. It applies a corrective force directly proportional to how far the drone is from its target angle.

- Analogy: Think of it as a mechanical spring snapping the drone back to level. The further it leans, the harder the spring pulls.
- Low P: The drone feels sluggish, "mushy," and struggles to maintain its angle.
- High P: The drone snaps back quickly but overshoots the target, oscillating rapidly back and forth (like a spring that is too stiff).

2. Derivative (D): The Damper
The D-term looks at the future by calculating the rate of change of the error. It actively resists rapid movement, acting as a shock absorber for the P-term.

- Function: As the P-term aggressively pulls the drone back toward level, the D-term realizes the error is shrinking rapidly and counteracts the P-term to slow the drone down before it overshoots.
- Low D: The drone will oscillate at the end of a movement (overshoot).
- High D: The drone feels overly robotic and stiff. If pushed too high, it amplifies high-frequency sensor noise, causing the motors to twitch rapidly. This twitching introduces the exact micro-vibrations you want to avoid when carrying sensitive camera payloads.


3. Integral (I): The Memory
The I-term looks at the past. It accumulates the error over time.

- Function: If the drone is instructed to be perfectly level, but a constant crosswind or an off-center payload (like a heavy multispectral sensor) is causing it to drift by 2 degrees, the P and D terms might settle into this slightly tilted state because the immediate error is too small to trigger a strong response. The I-term notices this stubborn 2-degree error persisting over time, continuously grows in strength, and eventually provides the extra push needed to get the drone perfectly back to zero.
- Low I: The drone drifts in the wind or sags when carrying asymmetrical weight.
- High I: The accumulation happens too fast, causing slow, low-frequency wobbles as the controller over-compensates for past errors.
 
it is complicate yes it is, however there is other way for you to tune quicker but result is great. that you can apply 
****" quick tune mode" -> "auto tune mode"**** 

for quick tune mode

https://ardupilot.org/copter/docs/quiktune.html

auto tune mode

https://ardupilot.org/copter/docs/autotune.html

question is why i not jump direct to auto tune , the answer is safety, you drone can crash if the wind change  suddenly, a sub step will safe 


result 

https://github.com/user-attachments/assets/50999b36-94db-4be9-a81a-472b13d4ee87

quite stable
