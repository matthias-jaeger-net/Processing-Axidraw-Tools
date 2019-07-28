# Processing-Axidraw-Tools
Personal collection of ideas and code to run the Axidraw in my studio from Processing

## Talking to the Axidraw - [Session One]

### Finding the correct port
To talk to the machine we need an instance of a Serial object. As pointed out by this example (https://www.processing.org/reference/libraries/serial/) we can scan for all available ports and see them listed in the console. 

```java 
// Make the serial library available
import processing.serial.*;

// List all the available serial ports
printArray(Serial.list());

// Output 
// [0] "Your port's name"
// [1] "Maybe an other port"
// [.] "...."
```

### Connect to the port
After printing the ports in the console we saw which one of the listed ports actually was the plotter's port and store it globally in ``myPortName``. To connect we have to create the serial object, that all examples called ``myPort``. With this we are able to send commands to the plotters serial port. 
```java
String myPortName = "Your port's name";
int    myBoudRate = 38400; // Number used in examples, looked up meaning
Serial myPort = new Serial(this, myPortName, myBoudRate);
```
### Sending commands to the port
The examples are wrapping the lines that actually send things to the port in a lot of code. We were reading the code and collecting different commands here. 

#### Basic command structre
A command to the port is sent as a single line of characters followed by a return in the form of a ``String``
```java
// Prints the version number of the port
String myCommand = "v/r"; 
myPort.write(myCommand);
```


#### Print the version number 
```java
myPort.write("v\r");
```


# Interesting links
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
