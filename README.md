**LOAD-FLOW-ANALYSIS-USING-GAUSS--SEIDAL-METHOD**
# INTRODUCTION
The Gauss–Seidel method is an iterative numerical technique used to solve the nonlinear load-flow equations. Starting from an initial voltage estimate, the bus voltages are updated successively using the latest available values until the change between iterations satisfies a specified convergence tolerance. In this teaching activity, students explore the method conceptually and use ETAP to construct a network model and perform load-flow studies.
The activity connects the mathematical procedure—bus classification, specified power, voltage updates, and convergence—with the practical interpretation of ETAP results. The software is used as a simulation and visualization environment; the underlying numerical method is discussed separately so that students understand what the solver is calculating.

# SOFTWARE REQUIRED:
ETAP Software
 
# PROBLEM FORMULATION: 
   
The performance equation of a power system may be written as  
[Ibus]=[Ybus][Vbus] ----------------------------(1) 
Selecting one of the buses as reference bus, we get (n-1) simultaneous equations. The bus 
loading equations can be written as: 

 <img width="681" height="587" alt="4PSA1IMG" src="https://github.com/user-attachments/assets/3ad6c3db-7a5f-4832-9527-d53011800485" />
   
The above equation is required formula. This equation can be solved for bus voltages in 
iterative manner. During each iteration, we compute all the bus voltages and check for the 
convergence is carried out by comparison with voltages obtained at the end of previous 
iteration. 
 
  After the solution is obtained, the slack bus real and reactive powers, the 
reactive power generation at the other generator buses and line flows can be calculated. 
 
  This method is easier when compared with other methods, because the 
calculations are very simple. This is used for making a good initial start for Newton-Raphson 
method.


# ALGORITHM: 
```
1. Read the data such as line data, specified bus powers, specified voltages, 
Q limits at generator buses and tolerance for convergence. 
2. Compute Y-bus matrix. 
3. Initialize all the bus voltages. 
4. Iter=1. 
5. Consider i=2 where i is the bus number. 
6. Check whether this P-V bus or P-Q bus. If it is P-Q bus, go to step 8. Otherwise 
go to next step. 
7. Compute Qi. Check for Q- limit variation. Qgi=Qi+QLi. 
If Qgi>Qimax, then equate Qgi to Qimax there by converting it in to P-Q bus. Qi=Qimax-Qi, then go to 
step 8. 
Similarly, if Qgi<Qimin, then equate Qgi to Qimin there by converting it in to P-Q bus. Qi=Qimin-QLi, 
then go to step 8. 
If Qgi is with in the upper and lower limits, don’t change Qgi. where 
Qi=Qgi-QLi, then go to step 8. 
8. Calculate the new value of the bus voltage using Gauss-Seidal formula. 
.Adjust the voltage magnitude of 
the bus to specified magnitude if Q limits are not violated. 
9. If all the buses are considered, go to step 10.Otherwise increment 
the bus number i=i+1 and go to step 6. 
10. Check for convergence. If there is no convergence go to step 12. 
11. Update the bus voltages using the formula 
Vi= V old + α (Vinew – V old) 
i 
i 
(i= 1, 2, 3 …n) 
12. Calculate the slack bus power at P-V buses, real and reactive line 
flows, real and reactive line losses and print all the results 
including all the complex bus voltages and all the bus angles. 
13. Stop. 
```

# CIRCUIT DIAGRAM:
<img width="975" height="578" alt="image" src="https://github.com/user-attachments/assets/5cef0960-0f22-42ee-bc2a-738160808357" />

# OUTPUT: 
S.No.	Observation	Voltage (kV) / Current (A)
1	Bus 1 Voltage	14.03 kV
2	Bus 2 Voltage	4.16 kV
3	Bus 3 Voltage	4.16 kV
4	Bus 4 Voltage	4.16 kV
5	Bus 5 Voltage	4.16 kV
6	Source feeder current	137.6 A
7	Transformer T1 feeder current	760.9 A
8	Bus 3 feeder current	744.8 A
9	Bus 5 feeder current	744.8 A
10	Bus 4 feeder current	473.1 A

# CONCLUSION:
The ETAP-supported learning activity provides students with an applied understanding of load-flow analysis and the Gauss–Seidel iterative concept. By connecting bus classification and voltage-update theory with a practical single-line network model, students can observe how system data influence bus voltages and power flows. The activity encourages analytical thinking, software familiarity, and interpretation of power-system operating conditions

