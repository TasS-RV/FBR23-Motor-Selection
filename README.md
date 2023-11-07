# FBR23-Motor-Selection
Program used to calculate the acceleration time taken for the FBR23, if the engine was theoretically replaced by an EV motor (with same drive ratio, coupled to rear axle).

There are some parameters to take heed of:

Edit these in the parameters.py file:_______________________________________________
1. rc - Diameter of engine sprocket on the engine (mm)
2. rs - Diameter of the sprocket on the rear axle (mm)
3. car_mass - Dry mass of car used(kg)
4. grip_mu - coefficient of friction between tyre and asphalt (this is neglected in the first version of this model, as we assume infinitely sticky tyres from the start...)
5. wheel_rad - centre to outer surface of (rear) tyre radius (m)

6. drag_coeff - An arbitrary coefficient of drag used for FS cars
7. frontal_area - maximum assumed cross-sectional area (assuming wings do nothing and are ramming into the air perpendicular) (m)
8. resolution - not a car parameter, but simply number of divisions whih motor speed is split into. The higher the value, the better the accuracy of torque value from the motor (as we interpolate the torque curve).

Edit these parameters in the Motors_def Excel file:__________________________________

Next to each is (rather confusingly) the Parameter number to which is corresponds to on the Inetic datasheet.
1. w1 - Speed at which the peak torque of the motor starts to drop-off (RPM) - parameter 2
2. w3 - Maximum rotational speed of the motor (RPM) - parameter 4
3. T_nominal - rated continuous running torque (Nm) - parameter 1
4. P_nominal - rated continuous running power (W) - parameter 3
5. T_peak - Peaktorque (Nm) - parameter 6
6. P_peak - Peak power (W) - parameter 7

![image](https://github.com/TasS-RV/FBR23-Motor-Selection/assets/93861976/4e82b7a1-f13f-48f4-bcac-c2caf11eee27)
   
The naming convention includes the main model (say, 180, or 230 etc...), the flow-rate specification (1U, 2U...)
and A, B, D etc... arbitrarily, just to distinguish between motors that are the same U specification.

Note for modelling the accelerations, we have used the rated torque instead of Peak torque, but you can edit this in the for loop iterating over each motor in the Plotter.py file.

Running:
1) Install the requirements.txt file in your virtual environment to have all necessary packages. There are more fundamental packages than needed, as Linux required some additional libraries for visualisation.
2) You only need to run Plotter.py. It will automatically save any graphs into the /Graphs folder for viewing.
3) At the moment it can only accept 3 motors in the spreadsheet at once. However, changing the code towards the bottom of the ____Motors Selection ____ section in Parameters.py is trivial if you want to add more motors into 'motors_list'.
