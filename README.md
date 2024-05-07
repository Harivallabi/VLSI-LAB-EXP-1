EXP-01    SIMULATION OF LOGICS GATES,ADDER,SUBTRACTOR
DATE:
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

verilog code:
```
Module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
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
```
output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/159146834/2965c28d-ddca-400a-a332-9844b224ed16)




Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

verilog code:
```
module ha(x,y,a,b);
input x,y;
output a,b;
xor x1(a,x,y);
and x2(b,x,y);
endmodule
```

output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/159146834/8fbd7a33-eb61-41b9-9622-4b812f7fe82b)




Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

verilog code:
```
module fa(a,b,cin,sum,carry);
input a,b,cin;
output sum,carry;
wire w1,w2,w3;
xor x1(w1,a,b);
and x2(w2,a,b);
xor x3(sum,w1,cin);
and x4(w3,w1,cin);
or x5(carry,w3,w2);
endmodule
```
output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/159146834/ac345e41-7d77-4b50-b09c-e4e17dbe0c73)




Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)
verilog code:
```
module hs(x,y,d,b);
input x,y;
output d,b;
wire w;
xor x1(d,x,y);
not n1(w,x);
and a1(b,y,w);
endmodule
```
output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/159146834/6fbca922-73b4-49ef-8fa1-8b06d313eea9)






Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)
verilog code:
```
module fs(a,b,cin,d,e);
input a,b,cin;
output d,e;
wire w1,w2,w3,w4,w5;
xor x1(w2,a,b);
not n1(w1,a);
and a1(w4,w1,b);
xor x2(d,w2,cin);
not n2(w3,w2);
and a2(w5,w3,cin);
or o1(e,w5,w4);
endmodule
```
output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/159146834/2ee62656-4891-4df1-8e66-4c4957c664c1)





8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

verilog code:
```
module fa(a,b,cin,sum,carry);
input a,b,cin;
output sum,carry;
wire w1,w2,w3;
xor x1(w1,a,b);
and x2(w2,a,b);
xor x3(sum,w1,cin);
and x4(w3,w1,cin);
or x5(carry,w3,w2);
endmodule

module rca(a,b,cin,sum,carry);
input [3:0]a,b;
input cin;
output[3:0]sum;
output carry;
wire w1,w2,w3;
fa g1(.a(a[0]),
      .b(b[0]),
      .cin(cin),
      .s(sum[0]),
      .carry(w1)
      );
fa g2(.a(a[1]),
      .b(b[1]),
      .cin(w1),
      .s(sum[1]),
      .carry(w2)
      );
 fa g3(.a(a[2]),
      .b(b[2]),
      .cin(w2),
      .s(sum[2]),
      .carry(w3)
      );
 fa g4(.a(a[3]),
      .b(b[3]),
      .cin(w3),
      .s(sum[3]),
      .carry(carry)
      );
  endmodule
```



OUTPUT:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/159146834/68219bc4-6925-440b-8226-629ed1471ed9)


RESULT:
Thus ,the given logic gates,half adder,full adder,half subtractor are simulated and synthesis are excuted successfully .

