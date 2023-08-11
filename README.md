# Physical Design Using ASIC Class

## Week 1
### Day 1


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

## Week 2
### Day 1 : iVerilog & GTKwave
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

### Day 2: Yosys
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

## Week 3
### Day 1: 
 <details>
 <summary> Timing limbs, hierarchical vs flat synthesis and efficient flop coding styles </summary>





</details>

### Day 2 :
 <details>
 <summary> Combinational and sequential optimizations </summary>






</details>




## References
1. https://yosyshq.net/yosys/
2. https://steveicarus.github.io/iverilog/
3. https://gtkwave.sourceforge.net/
4. https://ngspice.sourceforge.io/
5. https://github.com/The-OpenROAD-Project/OpenSTA
6. http://opencircuitdesign.com/magic/











