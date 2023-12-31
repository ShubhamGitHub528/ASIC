
# RTL Design using Verilog with SKY130 Technology.


## Day 1: Introduction to Verilog RTL Design and Synthesis.

<details>
 <summary> Installation of required Tools </summary>

<details>
 <summary> Yosys </summary>
    Commands to install Yosys on Linux.
	
```

$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master 
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install

```
Below is the screenshot showing sucessful Launch:
![yosys1](./softwares/yosys.png)

</details>	


<details>
 <summary> iVerilog </summary>
    Commans to install iVerilog
    
	
```

sudo apt-get install iverilog.

```

Below is the screenshot showing sucessful Launch:
![iVerilog](./softwares/iVerilog.png)
</details>
 <details>
 <summary> gtkwave </summary>


 I installed gtkwave using the following command:
  ```bash
sudo apt-get install gtkwave
 ```

Below is the screenshot showing sucessful Launch:
![Gtkwave](./softwares/Gtkwave.png)

</details>

 <details>
 <summary> ngspice </summary>


 I downloaded the tarball from https://sourceforge.net/projects/ngspice/files/ to a local directory and unpacked it using the following commands:
 ```bash
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure  --with-x --with-readline=yes --disable-debug
make
sudo make install
 ```
Below is the screenshot showing sucessful Launch:

![ngspice](./softwares/ngSPICE.png)

</details>

 <details>
 <summary> magic </summary>


 I installed magic using the following commands:
  ```bash
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev
 ```
 Below is the screenshot showing sucessful Launch:

![magic](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c3a15599-6a5e-43a8-bb88-f04c4d993b41)

 </details>

  <details>
 <summary> OpenSTA </summary>


 I installed and built OpenSTA (including the needed packages) using the following commands:
 ```bash
sudo apt-get install cmake clang gcctcl swig bison flex
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake ..
make
```
Below is the screenshot showing sucessful Launch:

![OpenSTA](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/bfd8d812-4a8a-4afa-8952-42cc15e36e2f)

</details>

<details>
 <summary> Introduction to iverilog, Design and Test Bench</summary>


#### Simulation

* RTL design is checked for adherence to the spec by simulating the design
* Simulator is the tool used for simulating the design
* iverilog is the tool used for this course


#### Design
* Design is the actual Verilog code or set of Verilog codes which has the intended functionality to meet with the required specifications

#### TestBench
* TestBench is the setup to apply stimulus (test _vectors) to the design to check its functionality
![Screenshot from 2023-08-11 23-07-19](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/3e60167b-7fbe-46b2-9d15-156672e5cce5)


#### How simulator works
* Simulator looks for the changes on the input signals
* Upon change to the input the output is evaluated
* If no change to the input, no change to the output!
* Simulator is looking for change in the values of input!

![Screenshot from 2023-08-11 22-57-07](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/dd5d073b-c2c4-4bb1-b69f-53c56648e6c5)

</details>
<details>
 <summary> Demostration of the Icarus Verilog and GTKWave </summary>

![Screenshot from 2023-08-12 01-57-59](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/94cbeb1b-d879-492a-9b24-be2ea81b7f9b)
</details>

</details>


<details>
 <summary> Introduction to Yosys </summary>

	
Yosys is an open-source software framework for Verilog RTL (Register Transfer Level) synthesis. It's commonly used in digital design and electronic engineering to convert high-level hardware descriptions written in Verilog into optimized gate-level representations that can be used for ASIC (Application-Specific Integrated Circuit) or FPGA (Field-Programmable Gate Array) implementations. Yosys provides a range of synthesis tools and optimization techniques to generate efficient and compact hardware designs. It's widely used in the hardware design community and is known for its flexibility, extensibility, and ability to handle complex designs.
</details>
 <details>
 <summary> Labs using Yosys and Sky130 PDKs </summary>
	 
To invoke yosys Type ```yosys```.
![Screenshot from 2023-08-12 00-40-27](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5f73071f-e10b-4694-9bbd-c1d859912455)

*Note: We should be in the directory in which we have cloned the github link.
![Screenshot from 2023-08-12 00-40-04](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d0c2d7bd-3949-45ee-8c59-7ea41ca7a181)


All libraries will be in ```myLib```

**Step-1:** Read the Library 
```
read_liberty -lib ../PATH
```
This command reads in a Liberty format library for use in technology mapping.

***Step-2:** Read Design

```
read_verilog FILE NAME
```
This command reads in Verilog source files for synthesis. Replace <filename> with the actual file name.

![Screenshot from 2023-08-12 00-41-41](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/4da8bc2f-f1ff-4ccf-b0a1-42185984bd53)


***Step-3:** Synthesis 
```
synth -top FILE NAME
```

**Step-4:** Genetare Netlist 

abc is command to convert RTL file to gate. And to what gate is need to specify is Written in the Path. 
```
abc -liberty ../PATH
```

Report Generated
![Screenshot from 2023-08-12 00-42-02](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/794992ae-0ea1-438c-b70f-7221e702bfe4)

To see logic realised
```
show
```
![Screenshot from 2023-08-12 00-55-53](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5b0e096b-4f0b-47f1-8882-d2f4399c3ae9)

**Step-5:** To write Netlist 
```
write_verilog FILE NAME
```
![Screenshot from 2023-08-12 01-18-05](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/e180b3e8-7319-4307-8281-71505772bbab)

</details>

</details>


## Day 2: Timing libs, hierarchical vs flat synthesis and efficient flop coding styles.

 <details>
 <summary> Introduction to Timing libs </summary>

**Introduction to .lib File**

*A .lib file, also known as a Liberty file, is a standard format used to describe the timing, power, and logical characteristics of cells in a digital library. These libraries are essential for the process of logic synthesis and technology mapping in digital design.*

![Screenshot from 2023-08-12 11-47-53](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c10f441c-52d4-4dd7-8f4b-6ff4fbacf5a0)
**PVT parameters**

![WhatsApp Image 2023-08-12 at 8 34 36 PM](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/4475ef7d-54e0-4ca0-af78-4dceaa97ff3e)
</details>

 <details>
 <summary> Hierarchical vs Flat Synthesis </summary>
	 
**Flatten**

*In Yosys, the "flatten" command is used to perform this flattening process. When you run the command, Yosys attempts to inline instances of submodules, removing the module hierarchy. This can be useful before performing certain types of optimizations that might work better on a flattened design.*
  
**Different versions of the same logic gate**

![Screenshot from 2023-08-12 12-53-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/132be748-8774-4ac2-a979-9b14e0151e16)

**Multiple Modules**

![Screenshot from 2023-08-12 14-00-16](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c9ae3b7a-b781-45cd-b3c5-c22b5384685c)

```
/* Generated by Yosys 0.31+16 (git sha1 b04d0e09e, clang 14.0.0-1ubuntu1.1 -fPIC -Os) */

module multiple_modules(a, b, c, y);
  input a;
  wire a;
  input b;
  wire b;
  input c;
  wire c;
  wire net1;
  output y;
  wire y;
  sub_module1 u1 (
    .a(a),
    .b(b),
    .y(net1)
  );
  sub_module2 u2 (
    .a(net1),
    .b(c),
    .y(y)
  );
endmodule

module sub_module1(a, b, y);
  wire _0_;
  wire _1_;
  wire _2_;
  input a;
  wire a;
  input b;
  wire b;
  output y;
  wire y;
  sky130_fd_sc_hd__and2_0 _3_ (
    .A(_1_),
    .B(_0_),
    .X(_2_)
  );
  assign _1_ = b;
  assign _0_ = a;
  assign y = _2_;
endmodule

module sub_module2(a, b, y);
  wire _0_;
  wire _1_;
  wire _2_;
  input a;
  wire a;
  input b;
  wire b;
  output y;
  wire y;
  sky130_fd_sc_hd__or2_0 _3_ (
    .A(_1_),
    .B(_0_),
    .X(_2_)
  );
  assign _1_ = b;
  assign _0_ = a;
  assign y = _2_;
endmodule
```
![Screenshot from 2023-08-12 14-19-45](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/64e65436-3374-45db-8622-2ebd0f1062e7)
![Screenshot from 2023-08-12 14-22-13](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/eba3c825-a546-4a39-ad4c-ad31cdbc86ba)
</details>
 <details>
 <summary> Flop Codings </summary>

**Why Flops?**
They provide memory and state-holding capabilities, allowing circuits to store data and make decisions based on history and current inputs. Combinational circuits use logic gates to directly process inputs without memory elements.

**Asynchronous**

![Screenshot from 2023-08-12 18-29-17](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5903e52f-3fe8-4e24-af77-eefadf698c66)

**Synchronous** 
	
![Screenshot from 2023-08-12 18-39-30](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/e6d1db4f-81b3-4c05-a672-1bfd46c63377)

Synthesis

![Screenshot from 2023-08-12 19-37-35](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5ade8840-ea39-4dd5-b323-7a50ccb7674a)


**Optimization**
![Screenshot from 2023-08-12 20-03-12](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/9b19d7f9-bfb9-4e62-ad36-88bcac8db02f)


</details>

## Day 3 : Combinational and sequential optimizations
*Combinational and sequential optimizations are two different approaches used in digital circuit design to improve the performance, efficiency, and reliability of electronic systems. These optimizations target different aspects of the design process and address various challenges that arise when designing complex digital circuits.*

 <details>
 <summary> Combinational Optimizations </summary>
Common techniques for combinational optimization include:

* Gate-Level Optimization: This involves simplifying logic expressions and minimizing the number of logic gates needed to implement a particular function.
* Technology Mapping: Selecting the optimal gate library for implementing a logic function based on the available manufacturing technology.
* Boolean Algebra Simplification: Applying algebraic identities and theorems to simplify Boolean expressions and reduce the complexity of the logic.
* Logic Synthesis: Automatically generating optimized gate-level representations of a design from a high-level description.

**Example AND Gate**

![Screenshot from 2023-08-13 11-48-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/3c49111a-a728-4e59-a019-794f1831d4ab)


**Example OR Gate**
Nand inverted and Gate

![Screenshot from 2023-08-13 11-50-59](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/fc5b74ca-c6a7-411f-97b7-13117df6392a)

</details>


 <details>
 <summary> Sequential Optimizations </summary>
	 
*Sequential circuits contain memory elements, such as flip-flops and registers, which allow them to store and process data over time. Sequential optimization focuses on improving the clock frequency, reducing power consumption, and ensuring proper timing and synchronization in these circuits.*

Common techniques for sequential optimization include:

* Pipeline Optimization: Breaking down a computation into smaller stages that can be processed concurrently, thus increasing throughput and reducing the critical path delay.
* Clock Gating: Disabling clock signals to specific circuit blocks when they are not needed, reducing power consumption.
* Retiming: Reordering registers within a design to optimize the timing paths and improve the clock frequency.
* State Machine Optimization: Reducing the number of states or transitions in finite state machines to simplify control logic and improve performance.


**Example dff_const1**

```
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end

endmodule
```

![Screenshot from 2023-08-13 12-18-07](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/801bda1b-74d1-4bf0-8ba7-455989f365e2)

Synthesis

![Screenshot from 2023-08-13 12-23-41](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5a92d016-245c-4ce9-9d8f-09020eb2b1df)

**Example dff_const2**

```
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end

endmodule
```
![Screenshot from 2023-08-13 12-34-08](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/41d83c88-99e3-4c4b-ab95-4274d0d87e66)

**Example dff_const3**
```
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```

Waveform

![Screenshot from 2023-08-13 13-09-10](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/3cc095b7-db02-4725-859a-041c86927ce1)

Synthesis

![Screenshot from 2023-08-13 13-12-07](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/f1f3786d-268a-4bfa-9341-eb2808e863d5)

**Example dff_const4**

```
module dff_const4(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b1;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
![Screenshot from 2023-08-13 15-21-38](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d71e4195-e9d4-4cf0-9ab7-a92e10a98393)


**Example dff_const5**

```

module dff_const5(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b0;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end

endmodule
```
![Screenshot from 2023-08-13 15-33-39](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/42de69de-478f-40e3-b100-e1990f452f3c)

**Counter_opt**

```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```
![Screenshot from 2023-08-13 16-12-28](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/63c83c51-3b74-4578-9d50-ad8592bb8632)


</details>

## Day 4: GLS, Blocking vs Non-Blocking and Synthesis - Simulation mismatch

 <details>
 <summary> GLS Flow</summary>

**GLS concept flow using iverilog**

*The GLS flow is crucial for ensuring that the gate-level netlist faithfully represents the intended behavior of the original RTL design. It helps catch issues that might have been missed during RTL simulation and ensures that the design is ready for further downstream processes.*

![Screenshot from 2023-08-13 18-09-35](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/bd06e244-ba78-4a3b-9659-e82e7453ca8a)

</details>
 <details>
 <summary>Synthesis Simulation mismatch</summary>
	 
**Ternary Operator**

```
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
	endmodule
```

Waveform

![Screenshot from 2023-08-13 22-12-03](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/cf98805f-5ad2-422e-bb13-d1d3502a02c6)

Synthesis

![Screenshot from 2023-08-14 10-02-51](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/8127551a-35ec-407f-98f2-bb25c7bfcbcf)

Waveform using Standers cells.

![Screenshot from 2023-08-14 10-29-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/7523f397-8456-47f6-968a-8d5dbbb4530c)

 
**Bad_Mux**
```
module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```

In this Wavefrom we cannot see changes in Y as of changes in i0. It just act as a flop which changes as their are changes in select line. 

![Screenshot from 2023-08-14 10-44-49](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5f7897b0-cd48-416b-859f-031eee406211)

Synthesis

![Screenshot from 2023-08-14 10-48-20](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/ea5eacb8-e397-420b-a714-3988fed30935)

In this Wavefrom we can see changes in Y as of changes in i0. 

![Screenshot from 2023-08-14 10-48-39](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/506da874-c031-4b02-9ed5-dfb3f9822a88)


</details>
 <details>
 <summary> Blocking and Non-Blocking </summary>

**Blocking_Coveat**
```
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
	d = x & c;
	x = a | b;
end
endmodule
```

In this waveform thier is *Synthesis Simulation mismatch* due to Blocking Statements.

![Screenshot from 2023-08-14 11-12-28](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/9aff427f-a806-4d2d-9644-e22f6a2ba5c1)

Synthesis 

![Screenshot from 2023-08-14 11-15-43](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c1ff26e5-3c04-41e3-b036-9b921abcd235)

Netist code after write_verilog.

![Screenshot from 2023-08-14 12-26-20](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/59b0d750-78b8-40aa-a001-72515efc7da5)

Waveform using Standers cells.

![Screenshot from 2023-08-14 12-26-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/6b362ce8-baac-46ce-91cc-ff5c3920b43e)


</details>

</details>

## Day 5: If,Case,for loop and for generate.


 <details>
 <summary> If Constructs </summary>
	 
**incomp_if**
```
module incomp_if (input i0 , input i1 , input i2 , output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
end
endmodule
```
Waveform - *Here Y behaves as a Latch*

![Screenshot from 2023-08-14 18-24-12](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/f5dc6d8f-da6e-4e69-b5dd-fcf892ab00c1)

Statistics - *We can see here we have infered a DLATCH*

![Screenshot from 2023-08-14 18-25-35](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/8b1d8996-6b92-4132-a540-85ec5b38c6ad)

Synthesis - 

![Screenshot from 2023-08-14 18-26-58](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/8af7cd25-1745-4f4e-9ed2-1da67332b03a)

**incomp_if2**
```

module incomp_if2 (input i0 , input i1 , input i2 , input i3, output reg y);
always @ (*)
begin
	if(i0)
		y <= i1;
	else if (i2)
		y <= i3;

end
endmodule
```
Waveform- *Latching when both io & i1 are zero*

![Screenshot from 2023-08-14 18-35-00](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/32af67ac-a451-4468-9c65-5891f64ea120)

Statistics *Infered a DLATCH*

![Screenshot from 2023-08-14 18-36-25](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/0647c0b6-64ce-46c1-a288-99a4ee916908)

Synthesis- *The OR operation of i0 &i1 will be given to enable of DLATCH*

![Screenshot from 2023-08-14 18-37-02](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/dc42bd6f-5219-4ab6-be1e-f686df29f418)



 </details>
 <details>
 <summary> Case Constructs </summary>
	 
**incomp_case**
```
module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
	endcase
end
endmodule
```
Waveform- *Latching when sel= 10 or sel= 11* It will continue matching the value of Y which was before.

![Screenshot from 2023-08-14 18-49-42](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/7030c10b-84be-4cef-83cb-5f5a1bb94b93)

Statistics

![Screenshot from 2023-08-14 18-51-49](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/e3140cde-d263-4a1b-b157-ab2836a6c93f)

Synthesis

![Screenshot from 2023-08-14 18-53-59](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/eb278226-a35b-403e-ae3b-5b5824f04b9b)

**comp_case**
```


module comp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
	case(sel)
		2'b00 : y = i0;
		2'b01 : y = i1;
		default : y = i2;
	endcase
end
endmodule
```

Waveform 

![Screenshot from 2023-08-14 18-59-49](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/66a69bed-c881-41af-9700-ad4c2bb3e006)

Statistics- *No Latch involved*

![Screenshot from 2023-08-14 19-02-01](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/50ab42e3-b9dc-4be9-93ca-1ddb2304c005)

Synthesis- *4x1 Mux*

![Screenshot from 2023-08-14 19-02-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/7036fc2c-79eb-4504-bebc-0213fe01e502)


**partial_case_assign**
Statistics- *Only one Latch infered in Path of X*

![Screenshot from 2023-08-14 19-12-27](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/4e96bd67-3374-4f9e-8d1b-53f045518887)

Synthesis

![Screenshot from 2023-08-14 19-13-35](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/9f35077a-92d5-4254-86b8-9cc5f0bca6be)

**bad_case**
```
module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```
Waveform- *Output gets confused when sel= 10 or sel=11 and hence behaves as a LATCH*

![Screenshot from 2023-08-14 23-54-08](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c23c5f73-0124-4cde-a62c-7be73a3bdeb2)

Statistics- *No LATCH involved*

![Screenshot from 2023-08-14 22-36-49](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/3a396e94-7182-4630-bf29-4282b4c1b581)

Synthesis- 

![Screenshot from 2023-08-14 22-38-36](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/dde6e462-b481-42cf-8a7d-f0488aa96c52)

Waveform- *using standered cell models and testbench*

![Screenshot from 2023-08-14 22-55-00](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/a7ece238-913d-474e-a056-612a7b188334)


</details>
 <details>
 <summary> For Loop and For generate </summary>

**mux_generate**
```
module mux_generate (input i0 , input i1, input i2 , input i3 , input [1:0] sel  , output reg y);
wire [3:0] i_int;
assign i_int = {i3,i2,i1,i0};
integer k;
always @ (*)
begin
for(k = 0; k < 4; k=k+1) begin
	if(k == sel)
		y = i_int[k];
end
end
endmodule


```

Waveform

![Screenshot from 2023-08-15 15-39-59](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/24efa353-de2d-413a-8155-d3745bc72657)

Synthesis

![Screenshot from 2023-08-15 15-48-51](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/6891f611-7dac-4975-a73a-f9abc0cecb3f)

**demux_case**

```
module fa (input a , input b , input c, output co , output sum);
	assign {co,sum}  = a + b + c ;
endmodule
```
Waveform

![Screenshot from 2023-08-15 15-49-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/24ac3ce3-32e2-4334-b6f6-e827be945c61)

Synthesis

![Screenshot from 2023-08-15 15-51-45](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/546fdf8f-0186-40bc-9612-ebede3520a5a)

**demux_generate**
```

module demux_generate (output o0 , output o1, output o2 , output o3, output o4, output o5, output o6 , output o7 , input [2:0] sel  , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;
always @ (*)
begin
y_int = 8'b0;
for(k = 0; k < 8; k++) begin
	if(k == sel)
		y_int[k] = i;
end
end
endmodule


```
Waveform- *Here we can see that the waveform is same as of demux_case but the code is Optimised*

![Screenshot from 2023-08-15 16-04-01](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/04da75f5-f2f9-4727-8198-f2b2d726663a)

**rca**

Code of Full Adder(fa).
```
module fa (input a , input b , input c, output co , output sum);
	assign {co,sum}  = a + b + c ;
endmodule
```

Code of Ripple Carry Adder(rca).
```
module rca (input [7:0] num1 , input [7:0] num2 , output [8:0] sum);
wire [7:0] int_sum;
wire [7:0]int_co;

genvar i;
generate
	for (i = 1 ; i < 8; i=i+1) begin
		fa u_fa_1 (.a(num1[i]),.b(num2[i]),.c(int_co[i-1]),.co(int_co[i]),.sum(int_sum[i]));
	end

endgenerate
fa u_fa_0 (.a(num1[0]),.b(num2[0]),.c(1'b0),.co(int_co[0]),.sum(int_sum[0]));


assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule

```

**Note**- *Here we have to read the fafile also as our code for FA is in the fa.v file*

Waveform

![Screenshot from 2023-08-15 16-31-37](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/510f3d36-01f9-4bba-a5ae-0c700b409c03)

Statistics

![Screenshot from 2023-08-15 16-45-08](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/bc373d9c-e7d1-46fd-ac43-b3156878825b)

Synthesis of Full Adder.

![Screenshot from 2023-08-15 16-51-27](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/e03654ff-0a56-46b8-adf3-a38190032f8a)

Synthesis of Ripple Carry Adder.

![Screenshot from 2023-08-15 16-52-03](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/dab7e880-0767-4907-944d-60a0aa00e6c9)

Code of Created Netlist(rca_net.v)
```
/* Generated by Yosys 0.31+16 (git sha1 b04d0e09e, clang 14.0.0-1ubuntu1.1 -fPIC -Os) */

module fa(a, b, c, co, sum);
  wire _0_;
  wire _1_;
  wire _2_;
  wire _3_;
  wire _4_;
  wire _5_;
  wire _6_;
  wire _7_;
  input a;
  wire a;
  input b;
  wire b;
  input c;
  wire c;
  output co;
  wire co;
  output sum;
  wire sum;
  sky130_fd_sc_hd__maj3_1 _8_ (
    .A(_3_),
    .B(_5_),
    .C(_4_),
    .X(_6_)
  );
  sky130_fd_sc_hd__xor3_1 _9_ (
    .A(_3_),
    .B(_5_),
    .C(_4_),
    .X(_7_)
  );
  assign _3_ = a;
  assign _5_ = c;
  assign _4_ = b;
  assign co = _6_;
  assign sum = _7_;
endmodule

module rca(num1, num2, sum);
  wire [7:0] int_co;
  wire [7:0] int_sum;
  input [7:0] num1;
  wire [7:0] num1;
  input [7:0] num2;
  wire [7:0] num2;
  output [8:0] sum;
  wire [8:0] sum;
  fa \genblk1[1].u_fa_1  (
    .a(num1[1]),
    .b(num2[1]),
    .c(int_co[0]),
    .co(int_co[1]),
    .sum(int_sum[1])
  );
  fa \genblk1[2].u_fa_1  (
    .a(num1[2]),
    .b(num2[2]),
    .c(int_co[1]),
    .co(int_co[2]),
    .sum(int_sum[2])
  );
  fa \genblk1[3].u_fa_1  (
    .a(num1[3]),
    .b(num2[3]),
    .c(int_co[2]),
    .co(int_co[3]),
    .sum(int_sum[3])
  );
  fa \genblk1[4].u_fa_1  (
    .a(num1[4]),
    .b(num2[4]),
    .c(int_co[3]),
    .co(int_co[4]),
    .sum(int_sum[4])
  );
  fa \genblk1[5].u_fa_1  (
    .a(num1[5]),
    .b(num2[5]),
    .c(int_co[4]),
    .co(int_co[5]),
    .sum(int_sum[5])
  );
  fa \genblk1[6].u_fa_1  (
    .a(num1[6]),
    .b(num2[6]),
    .c(int_co[5]),
    .co(int_co[6]),
    .sum(int_sum[6])
  );
  fa \genblk1[7].u_fa_1  (
    .a(num1[7]),
    .b(num2[7]),
    .c(int_co[6]),
    .co(int_co[7]),
    .sum(int_sum[7])
  );
  fa u_fa_0 (
    .a(num1[0]),
    .b(num2[0]),
    .c(1'h0),
    .co(int_co[0]),
    .sum(int_sum[0])
  );
  assign sum = { int_co[7], int_sum };
endmodule
```
Waveform of GLS.

![Screenshot from 2023-08-15 17-03-52](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/848ace89-3ff6-43d3-895a-d3e4f9de57a4)





</details>


## Word of Thanks
I sciencerly thank **Mr. Kunal Gosh**(Founder/**VSD**) for helping me out to complete this flow smoothly.

## Acknowledgement
- Kunal Ghosh, VSD Corp. Pvt. Ltd.
- Skywater Foundry
- Chatgtp
- Emil, Colleauge(IIIT-B)
- Alwin, Colleauge(IIIT-B)

## References
1. https://yosyshq.net/yosys/
2. https://steveicarus.github.io/iverilog/
3. https://gtkwave.sourceforge.net/
4. https://ngspice.sourceforge.io/
5. https://github.com/The-OpenROAD-Project/OpenSTA
6. http://opencircuitdesign.com/magic/











