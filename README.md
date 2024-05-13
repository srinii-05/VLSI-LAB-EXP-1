# VLSI-LAB-EXPERIMENTS-1
**Simulation and Implementation of Logic Gates, Adders and Subtractors**

**AIM:** To simulate and synthesis full adder,full subtractor,half adder,half subtractor,logic gates,ripplecarryadder_4bit,ripplecarryadder_8bit using vivado 2023.2.

**APPARATUS REQUIRED:** vivado 2023.2

**PROCEDURE:**
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:
Logicgates:
~~~
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
~~~
OUTPUT:
![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/2dc28223-f3a3-4a64-b3a1-d27c8b2a89ca)
![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/e90ca13d-492b-411c-8004-8a679f1118d8)

Halfadder:
~~~
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry;
or(sum,a,b);
and(carry,a,b);
endmodule
~~~
OUTPUT:
![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/3e71c806-6478-4aeb-955c-5d620405b28f)
![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/e24f1589-f8c1-47f5-baaa-2b8d82673383)


Fulladder:
~~~
module full_adder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
  assign sum=(a^b^c);
  assign carry=(a&b)|(b&c)|(a&c);
endmodule
~~~
OUTPUT:
![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/5a88418d-03bd-488c-a923-36dc99f8dc42)
![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/26a137dd-55a1-41cb-8a1b-d997fac45ffd)


Fullsubtractor:
~~~
module half_subtractor(d,b0,a,b);
input a,b;
output d,b0;
  assign d=a^b;
  assign b0=(~a)&b;
endmodule
~~~

OUTPUT:

![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/c03c41c4-91df-4e9b-83ec-fe03b6f6ee8f)

![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/518b4bb1-4bef-4d91-83f6-d4d477f98446)
4 Bit Ripple Carry Adder:
~~~
module rippe_adder(S, Cout, X, Y,Cin);
 input [3:0] X, Y;
 input Cin;
 output [3:0] S;
 output Cout;
 wire w1, w2, w3;
 fulladder u1(S[0], w1,X[0], Y[0], Cin);
 fulladder u2(S[1], w2,X[1], Y[1], w1);
 fulladder u3(S[2], w3,X[2], Y[2], w2);
 fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
  input X, Y, Ci;
  output S, Co;
  wire w1,w2,w3;
  xor G1(w1, X, Y);
  xor G2(S, w1, Ci);
  and G3(w2, w1, Ci);
  and G4(w3, X, Y);
  or G5(Co, w2, w3);
endmodule
~~~

OUTPUT:

![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/35b7f7e7-7873-4e0b-9d7e-ab6e267308b2)

![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/5900e596-2793-4190-a72c-4da0f382dbda)


8 Bit Ripple Carry Adder:
~~~
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
~~~

OUTPUT:

![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/ae89b60f-6201-417f-9b71-3a32ef1e38b3)

![image](https://github.com/Desika11/VLSI-LAB-EXP-1/assets/165646570/44c4f0dd-abcf-410f-8ea5-8982c1b87244)

**RESULT:**
Hence the simulation and synthesis of full adder,full subtractor,half adder,half subtractor,logic gates,ripplecarryadder_4bit,ripplecarryadder_8bit using vivado 2023.2. was successfully simulated using vivado.2023.3.
