# ALU_Zero_Flag
In the [Mixed Signal SoC Design Hackathon]https://esim.fossee.in/mixed-signal-soc-design-marathon), the problem statement is to implement the proposed design using skywater 130nm PDK technology. After doing the literature survey the [Initial report](https://github.com/gaeyasrisatyavinnakota/ALU_Zero_Flag/blob/mainLITERATURESURVEY.pdf) was submitted. The design was implemanted and this is the final Report Submission of successfully completed Design of ALU with Zero Flag, for  [Mixed Signal SoC Design Hackathon]https://esim.fossee.in/mixed-signal-soc-design-marathon)
## Table of Contents
1. [Abstract](#abstract)
2. [Details of the Circuit](#details-of-the-circuit)
3. [Working of the Circuit](#working-of-the-circuit)
4. [Implemented Design](#implemented-design)
5. [Output Waveforms](#output-waveforms)
6. [Schematic Netlist](#schematic-netlist)
7. [Challenges and Limitations](#challenges-and-limitations)
8. [References](#references)
9. [Acknowledgements](#acknowledgements)
10. [Author](#author)
## Abstract
This report describes the design and Implementation of 32 bit ALU with zero flag

## Details of the Circuit
Circuit designed is as shown below
<figure>
<p align="center"><img src="https://github.com/gaeyasrisatyavinnakota/ALU_Zero_Flag/blob/main/Screenshot%20(367).png" width="300" height ="300"></p>
<figcaption><p align = "center">Figure Circuit Implementation </p></figcaption>
</figure>

The ALU operations is as shown below,

<table align="center">
  <tr>
    <th>ALU_Sel</th>
    <th>operation</th>
  </tr>
  <tr>
    <td>4'b0000</td>
    <td>addition</td>
  </tr>
  <tr>
    <td>4'b0001</td>
    <td>Subtraction</td>
  </tr>
  <tr>
    <td>4'b0010</td>
    <td>multiplication</td>
  </tr>
  <tr>
    <td>4'b0011</td>
    <td>division</td>
  </tr>
  <tr>
    <td>4'b0100</td>
    <td>left shift</td>
  </tr>
  <tr>
    <td>4'b0101</td>
    <td>right shift</td>
  </tr>
  
  <tr>
    <td>4'b0110</td>
    <td>logical and</td>
  </tr>
  <tr>
    <td>4'b0111</td>
    <td>logical or</td>
  </tr>
  <tr>
    <td>4'b1000</td>
    <td>logical xor</td>
  </tr>
  <tr>
    <td>4'b1001</td>
    <td>nand</td>
  </tr>
  <tr>
    <td>4'b1010</td>
    <td>nor</td>
  </tr>
  <tr>
    <td>4'b1011</td>
    <td>xnor</td>
  </tr>
  <tr>
    <td>4'b1100</td>
    <td>rotate left</td>
  </tr>
  <tr>
    <td>4'b1101</td>
    <td>rotate left</td>
  </tr>
  <tr>
    <td>4'b1110</td>
    <td>rotate left</td>
  </tr>
</table>
The code used is given below,

```
module VGSS_ALU(
	input [31:0] ALU_IN1,ALU_IN2,
	input [3:0] ALU_SEL,
	output reg [31:0] ALU_OUT);
always@(*)
begin
case(ALU_SEL)
4'b0000:
ALU_OUT = ALU_IN1 + ALU_IN2;
4'b0001:
ALU_OUT = ALU_IN1 - ALU_IN2;
4'b0010:
ALU_OUT = ALU_IN1 * ALU_IN2;
4'b0011:
ALU_OUT = ALU_IN1 / ALU_IN2;
4'b0100:
ALU_OUT = ALU_IN1 << ALU_IN2;
4'b0101:
ALU_OUT = ALU_IN1 >> ALU_IN2;
4'b0110:
ALU_OUT = ALU_IN1 & ALU_IN2;
4'b0111:
ALU_OUT = ALU_IN1 | ALU_IN2;
4'b1000:
ALU_OUT = ALU_IN1 ^ ALU_IN2;
4'b1000:
ALU_OUT = ~(ALU_IN1 & ALU_IN2);
4'b1001:
ALU_OUT = ~(ALU_IN1 | ALU_IN2);
4'b1010:
ALU_OUT = ~(ALU_IN1 ^ ALU_IN2);
4'b1011:
ALU_OUT = ALU_IN1 >>> ALU_IN2;
4'b1100:
ALU_OUT = {ALU_IN1[30:0],ALU_IN1[31]};
4'b1101:
ALU_OUT = {ALU_IN1[0],ALU_IN1[31:1]};
4'b1110:
ALU_OUT = (ALU_IN1 == ALU_IN2)?32'b0 : 32'b1;
4'b1111:
ALU_OUT = ~(ALU_IN1);
default: ALU_OUT = ALU_IN1;
endcase
end
endmodule
```

## Output Waveforms


The output waveforms obtained after the simulation are as shown below
<figure>
<p align="center"><img src=""https://github.com/gaeyasrisatyavinnakota/ALU_Zero_Flag/blob/main/Screenshot%20(365).png" width="1000" height ="300"></p>
<figcaption><p align = "center"> Waveforms obtained</p></figcaption>
</figure>

## Challenges and limitations
- The main challange is to design the zero flag here the approah used is to use nor gate as the nor gate gives the output logic high when all the inputs are low.
- the second challenge is the complexity due to the data width being 32 bits.
## References
[1] https://en.wikipedia.org/wiki/Arithmetic_logic_unit
[2]	https://en.wikipedia.org/wiki/Zero_flag


## Acknowledgements
- http://iitb.ac.in/
- https://www.google.co.in/
- https://fossee.in/
- https://spoken-tutorial.org/
- https://www.vlsisystemdesign.com/
- https://www.c2s.gov.in/
- [VLSI System Design](https://www.vlsisystemdesign.com/)
- [Kunal Ghosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836/)
- [Sumanto Kar](https://www.linkedin.com/in/sumanto-kar-0424391a9/)
## Author
[Gaeya Sri Satya Vinnakota](https://www.linkedin.com/in/vgss/), BTech IV year, Electronics Engineering Department, [Sardar Vallabhbhai National Institute Of Technology](https://www.svnit.ac.in/)
