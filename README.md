# Processing-Axidraw-Tools
Personal collection of ideas and code to run the Axidraw in my studio from Processing

### Interesting links
* https://wiki.evilmadscientist.com/AxiDraw_User_Guide
* https://cdn.evilmadscientist.com/dl/ad/public/AxiDraw_Guide_v40_r3.pdf

### Code to review
* Original example
* * https://github.com/evil-mad/AxiDraw-Processing
* Turtle Exapmle 
* * https://github.com/ralphcrutzen/AxiTurtle
* JS Turtle, fun to play
* * https://forresto.github.io/turtle-svg/

### Libraries used by examples
* Animation library, used for Timings I think
* *  http://www.looksgood.de/libraries/Ani/

# What we found out so far

## Talking to the Axidraw

### Connection
To talk to the machine we need an instance of a Serial object. As pointed out by this example (https://www.processing.org/reference/libraries/serial/) we can scan for all available ports and see them listed in the console. 

```java 
// Make the serial library available
import processing.serial.*;

// List all the available serial ports
printArray(Serial.list());

// Output 
// [0] "The port's name"
// [1] "Maybe an other port"
// [.] "...."
```
#### More about the Serial object 

### Finding the correct port
, that all examples called ``myPort``. With this we are able to send commands to the plotters serial port. 
In the examples we found a ``scanSerial();`` function, located in ``utils.pde`` and spotted the relevant lines. We manually run the function and saw in the console output the names of all available ports on our Macbook. We took note of it as a constant and called it ``portName``

```java
// Initial
Serial myPort;
Serial.list()
myPort = new Serial(this, portName, 38400);
```
