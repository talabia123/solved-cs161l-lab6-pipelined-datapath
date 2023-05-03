Download Link: https://assignmentchef.com/product/solved-cs161l-lab6-pipelined-datapath
<br>
You will need to submit a set of files to test your Pipelined Datapath (similar to you Single Cycle Datapath. The test includes an init.coe​, a corresponding ​.asm​ (assembly translation of the ​.coe​) and a ​processor_tb.v​ file to test the instructions. The individual instruction test from the previous lab should still work (all instructions are independent), but your whole program test won’t work the way it is written.  Write a new ​.asm​ and ​.coe​ file to test the whole program and at the header of the ​.asm​ file write (in comments) what changes needed to be made to get it to work and why?

<h2>Deliverables</h2>

<table>

 <tbody>

  <tr>

   <td width="96"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>




<table width="838">

 <tbody>

  <tr>

   <td width="192">init.coe</td>

   <td width="319">init.asm</td>

   <td width="327">processor_tb.v</td>

  </tr>

  <tr>

   <td width="192">Machine code translation of the ​init.asm​ file &gt;&gt;&gt;</td>

   <td width="319"># What changes were made to the .asm from  # the previous lab?# Why were those changes necessary?</td>

   <td width="327">Extend the ​process_tb.v​ from the previous lab for the new test case (​.coe​ and .asm​      ​)</td>

  </tr>

 </tbody>

</table>

<h1>Introduction</h1>

In the real world, a signal must travel through the entire circuit from it’s source to it’s destination within one clock cycle. As the circuit’s length increases so too does the time it takes for the signal to propagate. The longest path within a design is referred to as the ​<strong>critical path</strong>​. Knowing the critical path’s length allows us to determine the circuit’s maximum clock frequency.




In the previous lab, we designed a processor with the PC as the source and destination of all paths. This results in a processor with a longer critical path and a low clock frequency. To improve this we can ​<strong>pipeline</strong>​ the processor, or divide the datapath into stages and at each stage, we ​<em>register</em>​ the inputs and outputs. These registers act as new sources and destinations for the circuit’s paths. This reduces the length critical path of the circuit allowing for an improved clock frequency.




Pipelining also has the benefit of processing multiple instructions concurrently. However, there are drawbacks. With multiple instructions executing data dependencies between them must be maintained. An instruction could read a register before the previous one has finished writing the new data back. There are a number of techniques to deal with these hazards that will be discussed in class, but for this lab, you can assume pipeline stalls will be inserted by the compiler to ensure correct execution in the processor.

<h1>Deliverables</h1>

For this lab, you are to extend your datapath from the previous Single Cycle Datapath lab to a pipelined version (a fresh template is provided in the zip file, but you will likely want to extend your solution from the previous lab). This is done by placing registers between each stage to hold the signals for one cycle. In this way, each set of registers can hold one instruction. A pipelined version of the datapath (shown below) can be found in your textbook