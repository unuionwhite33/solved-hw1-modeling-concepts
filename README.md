Download Link: https://assignmentchef.com/product/solved-hw1-modeling-concepts
<br>
Verilog HDL modeling language supports three kinds of modeling styles: gate-level, dataflow, and behavioral. The gate-level and datafow modeling are used to model combinatorial circuits whereas the behavioral modeling is used for both combinatorial and sequential circuits. This lab illustrates the use of all three types of modeling by creating simple combinatorial circuits using ISE or Vivado software tool.

<ol>

 <li>Gate-level Modeling</li>

</ol>

The gate-level modeling is useful when a circuit is a simple combinational, as an example a multiplexer. Multiplexer is a simple circuit which connects one of many inputs to an output. In this part, you will create a simple 2-to-1 multiplexer and extend the design to multiple bits.

<ol>

 <li>Create a 2-to-1 multiplexer using gate-level modeling. Specifically, create and add the Verilogmodule with three inputs (x, y, s) and one output (m) using gate-level modeling.</li>

 <li>Create a two-bit wide 2-to-1 multiplexer using gate-level modeling.</li>

 <li>Dataflow Modeling</li>

</ol>

Dataflow modeling style is mainly used to describe combinational circuits. The basic mechanism used is the continuous assignment. In a continuous assignment, a value is assigned to a data type called net. The syntax of a continuous assignment is

Where LHS_net is a destination net of one or more bit, and RHS_expression is an expression consisting of various operators. The statement is evaluated at any time any of the source operand value changes and the result is assigned to the destination net after the delay unit. The gate level modeling examples listed in Part 1 can be described in dataflow modeling using the continuous assignment. For example,

The target in the continuous assignment expression can be one of the following:

<ol>

 <li>A scalar net (e.g. 1st and 2nd examples above)</li>

 <li>Vector net</li>

 <li>Constant bit-select of a vector (e.g. 3rd example above)</li>

 <li>Constant part-select of a vector</li>

 <li>Concatenation of any of the above</li>

</ol>

Let us take another set of examples in which a scalar and vector nets are declared and used

Note that multiple continuous assignment statements are not allowed on the same destination net.

<ol>

 <li></li>

</ol>

<table>

 <tbody>

  <tr>

   <td width="216"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Model a two-bit wide 2-to-1 multiplexer using dataflow modeling with net delays of 3 ns.Specifically, create and add the Verilog module with two 2-bit inputs (x[1:0], y[1:0]), a one bit select input (s), and two-bit output (m[1:0]) using dataflow modeling. Each assignment statement should have 3 units delay. As an example, a one-bit 2-to-1 multiplexer can be described as follows:</li>

</ul>

<ol>

 <li>Create a testbench and Simulate the design for 100 ns and show the output.</li>

 <li>Behavioral Modeling</li>

</ol>

Behavioral modeling is used to describe complex circuits. It is primarily used to model sequential circuits, but can also be used to model pure combinatorial circuits. The mechanisms (statements) for modeling the behavior of a design are:

initial Statements always Statements

A module may contain an arbitrary number of initial or always statements and may contain one or more procedural statements within them. They are executed concurrently (i.e. to model parallelism such that the order in which statements appear in the model does not matter) with respect to each other whereas the procedural statements are executed sequentially (i.e. the order in which they appear does matter). Both initial and always statements are executed at time=0 and then only always statements are executed during the rest of the time. The syntax is as follows:

where a procedural_statement is one of:

procedural assignment conditional_statement case_statement loop_statement wait_statement

The <strong>initial </strong>statement is non-synthesizable and is normally used in testbenches. The <strong>always</strong> statement is synthesizable, and the resulting circuit can be a combinatorial or sequential circuit. In order for the model to generate a combinatorial circuit, the always block (i) should not be edge sensitive, (ii) every branch of the conditional statement should define all output, and (iii) every case of case statement should define all output and must have a default case. More detailed coverage of this topic is covered in

Lab 7. The destination (LHS) should be of reg type; either scalar or vector. For example,

<ol>

 <li>Create a 2-to-1 multiplexer using behavioral modeling. Specifically, Create and add the Verilogmodule with three inputs (x, y, s) and one output (m) using behavioral modeling. Use the example code given below:</li>

 <li>Create a two-bit wide 2-to-1 multiplexer using behavioral modeling. Specifically, create and add theVerilog module with two-bit input (x[1:0], y[1:0]), a one bit select input (s), and two-bit output (m[1:0]) using behavioral modeling.</li>

 <li>Mixed-design Style Modeling</li>

</ol>

Complex systems can be described in Verilog HDL using mixed-design style modeling. This modeling style supports hierarchical description.

As an example of a mixed-style modeling, following diagram shows how one can build a 3-to1 multiplexer using multiple instances of 2-to-1 multiplexer. It also shows the symbol and the truth table.

In the above diagram, u, v, w are data inputs whereas S0, S1 are select signals, and the output is m. It uses two instances of 2-to-1 multiplexer.

<ol>

 <li>a) Model a 3-to-1 multiplexer using 2-to-1 multiplexers. Specifically, create a top-level Verilog module with three data inputs (u, y, w), two select inputs (s0, s1), and one bit output (m) using the previously defined 2-to-1 multiplexer. You can use any style designed 2-to-1 multiplexer (1, 2, or 3). Wire them up as shown in the above diagram.</li>

 <li>Model a BCD to 7-Segment Decoder.</li>

</ol>

A 7-segment display consists of seven segments, numbered a to g which can be used to display a character. Depending on the input type, a type conversion may be needed. If want to display a binary coded decimal (BCD) using 4-bit input, a BCD to 7-segment decoder is required. The table below shows the bit pattern you need to put to display a digit (note that to turn ON a segment you need to put logic 0 on the segment and the anode of the display needs to be driven logic 0 on this board).

<ol>

 <li>a) Create a top-level Verilog module, named bcdto7segment_dataflow with 4-bit data input (x[3:0]), anode enable output signals (an[3:0]), and 7-bit output (seg[6:0]) using dataflow modeling (Hint: You will have to derive seven expressions for the 7 segments on paper). Assign appropriate logic to an[3:0] in the model so you can display only on the right most display..</li>

</ol>