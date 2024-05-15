# SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS
# AIM:
To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

# APPARATUS REQUIRED:
vivado 2023.2.

# PROCEDURE:
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# LOGIC DIAGRAM

# ENCODER

![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/13a9dd6f-c38c-4994-ae16-62c507727a6e)


# DECODER

![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/3051001a-0da0-4c5a-a053-e412ee8331c4)


# MULTIPLEXER

![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/d901a333-caca-497e-9f0e-493898e786af)


# DEMULTIPLEXER

![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/8f4df971-c652-4d02-aab9-85902f571391)


# MAGNITUDE COMPARATOR

![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/c6f349af-94dd-4582-9ce8-5cc6e1bf21b4)


# VERILOG CODE
# 8-3 ENCODER:
module encoder(d,a,b,c);

input [7:0]d; output a,b,c;

or (a,d[4],d[5],d[6],d[7]);

or (b,d[2],d[3],d[6],d[7]);

or (c,d[1],d[3],d[5],d[7]);

endmodule

# 3-8 DECODER:
module decoder(A,E,Y);

input [1:0]A;

input E;

output [3:0]Y;

assign Y[0]=~A[1]&~A[0]&E;

assign Y[1]=~A[1]&A[0]&E;

assign Y[2]=A[1]&~A[0]&E;

assign Y[3]=A[1]&A[0]&E;

endmodule

module decoder(A,Y);

input[2:0]A;

output[7:0]Y;

decoder_2_4 d1(A[1:0],~A[2],Y[3:0]);

decoder_2_4 d2(A[1:0],~A[2],Y[7:4]);

endmodule

# 8-1 MULTIPLEXER:
module multi(i,s,y);

input[7:0]i;

input[2:0]s;

output reg y;

always@(*)

begin

case({s[2],s[1],s[0]})

3'b000:y=i[0];

3'b001:y=i[1];

3'b010:y=i[2];

3'b011:y=i[3];

3'b100:y=i[4];

3'b101:y=i[5];

3'b110:y=i[6];

3'b111:y=i[7];

endcase end

endmodule

# 1-8 DEMULTIPLEXER:
module demultiplexer(d1,d2,d3,d4,d5,d6,d7,d8,i,s0,s1,s2);

input i,s0,s1,s2;

output d1,d2,d3,d4,d5,d6,d7,d8;

wire w1,w2,w3;

not g1(w1,s0);

not g2(w2,s1);

not g3(w3,s2);

and g4(d1,w1,w2,w3,i);

and g5(d2,w1,w2,s2,i);

and g6(d3,w1,s1,w3,i);

and g7(d4,w1,s1,s2,i);

and g8(d5,s0,w2,w3,i); and g9(d6,s0,w2,s2,i);

and g10(d7,s0,s1,w3,i);

and g11(d8,s0,s1,s2,i);

endmodule

# 2 BIT MAGNITUDE COMPARATOR :
module mag_com(a,b,gt,it,eq);

input [3:0]a,b;

output reg gt,it,eq;

always @(a,b)

begin

if(a>b)

begin

gt = 1'b1;

it = 1'b0;

eq = 1'b0;

end else if(a<b)

begin

gt = 1'b0;

it = 1'b1;

eq = 1'b0;

end

else

begin

gt = 1'b0;

it = 1'b0;

eq = 1'b1;

end

end

endmodule

# OUTPUT WAVEFORM:
# ENCODER:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/2e343ac7-44d3-4b40-9a70-020e78e132ee)


# DECODER:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/c73aab59-d00f-4398-bab6-2d6d981688fe)


# MULTIPLEXER:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/bd81a8b8-2016-44a3-9d39-da543402fe56)


# DEMULTIPLEXER:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/d4b5367a-5e28-40c5-909f-8594db093088)


# 2 BIT MAGNITUDE COMPARATOR:
![image](https://github.com/Ocharan10/VLSI-LAB-EXP-2/assets/162343019/f2701b18-ae19-40c0-88ea-76251777aa0a)


# RESULT:
Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.
