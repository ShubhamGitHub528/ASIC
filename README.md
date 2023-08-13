
# Physical Design Using ASIC Class


## Day 1


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

## Day 2
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
***Step-2:** Read Design
```
read_verilog FILE NAME
![Screenshot from 2023-08-12 00-41-41](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/4da8bc2f-f1ff-4ccf-b0a1-42185984bd53)

```
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


 <details>
 <summary> Timing limbs, hierarchical vs flat synthesis and efficient flop coding styles </summary>
 <details>
 <summary> Introduction to .lib File </summary>

![Screenshot from 2023-08-12 11-47-53](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c10f441c-52d4-4dd7-8f4b-6ff4fbacf5a0)
** PVT parameters **
![WhatsApp Image 2023-08-12 at 8 34 36 PM](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/4475ef7d-54e0-4ca0-af78-4dceaa97ff3e)

Different versions of the same logic gate
![Screenshot from 2023-08-12 12-53-57](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/132be748-8774-4ac2-a979-9b14e0151e16)

Multiple Modules
![Screenshot from 2023-08-12 14-00-16](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/c9ae3b7a-b781-45cd-b3c5-c22b5384685c)

![Screenshot from 2023-08-12 14-19-45](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/64e65436-3374-45db-8622-2ebd0f1062e7)
![Screenshot from 2023-08-12 14-22-13](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/eba3c825-a546-4a39-ad4c-ad31cdbc86ba)


</details>
<details>
 <summary> Various Flop Coding Styles </summary>
	
![WhatsApp Image 2023-08-12 at 8 34 36 PM (1)](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d5fea351-8b63-4691-8017-4b3873630a8d)
</details>
<details>
 <summary> Why Flops? </summary>

![WhatsApp Image 2023-08-12 at 8 34 37 PM](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/ef6f5cb4-a9c7-4228-8c4a-519bc28b3ed8)
</details>

<details>
 <summary> Asynchronous  </summary>
	
![WhatsApp Image 2023-08-12 at 8 34 37 PM (1)](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/8029b4a5-e75d-447e-b583-e3baaff4def0)
![Screenshot from 2023-08-12 18-29-17](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5903e52f-3fe8-4e24-af77-eefadf698c66)
</details>
<details>
 <summary> Synchronous </summary>
	
![WhatsApp Image 2023-08-12 at 8 34 38 PM](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/2aece9d0-763f-43d1-b8db-16b58eb14d8c)
![Screenshot from 2023-08-12 18-39-30](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/e6d1db4f-81b3-4c05-a672-1bfd46c63377)

<details>
 <summary> Synthesis </summary>

![WhatsApp Image 2023-08-12 at 8 34 38 PM (1)](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/6d1fa204-4604-459d-9f5a-18a73102fe70)
![Screenshot from 2023-08-12 19-37-35](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5ade8840-ea39-4dd5-b323-7a50ccb7674a)
</details>
</details>

<details>
 <summary> Synchronous & Asynchronous Reset </summary>
	
![WhatsApp Image 2023-08-12 at 8 34 39 PM](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d7bdb2af-5ecf-49aa-9493-9321d018650d)

</details>

<details>
 <summary> Optimization </summary>

![WhatsApp Image 2023-08-12 at 8 34 39 PM (1)](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/b05c4af9-a5e3-4b98-bb1d-2240eaa026f5)
![Screenshot from 2023-08-12 20-03-12](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/9b19d7f9-bfb9-4e62-ad36-88bcac8db02f)

![WhatsApp Image 2023-08-12 at 8 34 40 PM (1)](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/199cc57c-bfb6-46b0-96be-1b2e37a1e134)

</details>
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

![Screenshot from 2023-08-13 12-18-07](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/801bda1b-74d1-4bf0-8ba7-455989f365e2)

Synthesis

![Screenshot from 2023-08-13 12-23-41](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/5a92d016-245c-4ce9-9d8f-09020eb2b1df)

**Example dff_const2**

![Screenshot from 2023-08-13 12-34-08](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/41d83c88-99e3-4c4b-ab95-4274d0d87e66)

**Example dff_const3**
Waveform
![Screenshot from 2023-08-13 13-09-10](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/3cc095b7-db02-4725-859a-041c86927ce1)

Synthesis
![Screenshot from 2023-08-13 13-12-07](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/f1f3786d-268a-4bfa-9341-eb2808e863d5)

**Example dff_const4**

![Screenshot from 2023-08-13 15-21-38](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/d71e4195-e9d4-4cf0-9ab7-a92e10a98393)


**Example dff_const5**

![Screenshot from 2023-08-13 15-33-39](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/42de69de-478f-40e3-b100-e1990f452f3c)

**Counter_opt**
![Screenshot from 2023-08-13 16-12-28](https://github.com/ShubhamGitHub528/ASIC/assets/140998623/63c83c51-3b74-4578-9d50-ad8592bb8632)


</details>
## References
1. https://yosyshq.net/yosys/
2. https://steveicarus.github.io/iverilog/
3. https://gtkwave.sourceforge.net/
4. https://ngspice.sourceforge.io/
5. https://github.com/The-OpenROAD-Project/OpenSTA
6. http://opencircuitdesign.com/magic/











