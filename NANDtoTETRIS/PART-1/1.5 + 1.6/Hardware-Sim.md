# Hardware Simulation ([unit 1.5](https://www.coursera.org/learn/build-a-computer/lecture/jmAls/unit-1-5-hardware-simulation))

The chips built using the HDL can be simulated using a software called '**_Hardware Simulator_**'. Here in this course we use a native hardware simulator written in java.

There are 3 ways of simulating a hardware component on a simulator:

1. Interactive
2. Script-based
3. With/without compare files

## Interactive Simulation

Here we load the HDL file into the simulator and run the code by entering values like '0' and '1' and verify if the output is correct.

We can:

* Evaluate the chip's logic
* Inspect the resulting values at internal and output pins

## Script-Based 

Here we have a test-script with which we can produce outputs for preset inputs. 

This script:

* can be used repeatedly
* directly prints the output to an output file

## Script-Based with a compare file

Compare files are the output files[^1] of the simulation of the well-behaved version hardware component we are building.

It helps us to verify the output of the the component simulated.

The process is:

* The simulator checks the output line-by-line and checks it with the compare file
* If any line is different, it throws an error

## Hardware construction Projects

* The players [^2]
    1. The system architect
    2. The developer

* Given the problem statement, the system architect decides the chip needed.

* The architect creates the following for each chip:
    1. The chip API
    2. A test script
    3. A compare file

* With these resources, the developer creates the chip

## Bus

A series/collection of bits which are needed to be manipulated together is called a bus.

* Bus is considered to be a single entity
    ```verilog
    Bus1[16], Bus2[16];
    ```
    we can notice that the representation[^3] of a bus is similar to that of an array in programming languages.

* Individual bits of a bus can be accessed by using     their index[^4] number (similar to that of array elements)

* Buses can be composed of and broken into sub-buses

In the HDL we are using here:
* Overlapping of sub-buses is allowed
* Width of the internal pins is deduced automatically
* "**false**" and "**true**" can be uses as buses of any width

### Note

Use the in-lecture quiz questions for revision



[^1]: The chip's code is written in a high-level language and the outpt of that simulation is the compare file
[^2]: There are many other players involved. We condiser only two of them for now.
[^3]: The given representation is that of a 16 bit bus.
[^4]: The indexing starts from 0 and the right-most index is '0'.