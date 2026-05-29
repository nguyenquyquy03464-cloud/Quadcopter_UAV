# Quadcopter_UAV
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
