# **Write up of PID Controller**

## Principle of PID Controller
### 1. Intialize the 3 parameters and the 3 error terms:
* Kp = Kp_
* Ki = Ki_
* Kd = Kd_
* p_error = 0.0
* i_error = 0.0
* d_error = 0.0

### 2. Update the error terms according to the new cte:
* p_error = cte
* i_error = i_error + cte
* d_error = cte - p_error

### 3. Return the total error:
* p_error * Kp + i_error * Ki + d_error * Kd

## Parameters adjustment
### 1. P value (Kp_) represents the ability to steer, which indicates the potentiality of how fast the ego car can return to the center of the road. Kp_ should be relative larger. With comparision of several values, 0.1 is determined with a better performance, which can in both sharp and light curve steer safety.
### 2. I value (Ki_) is used to decrease system bias, and only contributs when the ego car is off the road center with a large distance. This value should be relative small. Even set as 0, the ego car can also driving the whole loop. By several test, the Ki_ with value 0.005 represents a better performance.
### 3. D value (Kd_) represents the stability of the system. It has contributs to decrease the oversteer and overcome the swing. Larger Ki_ make the driving behavior stable, which means smaller steer angle and less direction correction. So this value is set as 4, and the ego car can safety driving on the road.