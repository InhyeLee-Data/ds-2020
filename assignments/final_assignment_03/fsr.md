# fsr

*measures physical pressure, squeezing and weight*

Product: [Round Force-Sensitive Resistor (FSR) - Interlink 402](https://www.adafruit.com/product/166)

#### Tools needed: 

- Particle Photon or Electron
- Hook up wires
- 10K ohm resistor

## Setup

![photo of setup](img/fsr.JPG)

## Starter Code

*Adapted from an example in the [Particle docs](https://docs.particle.io/guide/getting-started/examples/photon/#read-your-photoresistor-function-and-variable)*

``` cpp
// -----------------------------------------
// Force Sensitive Resistor (FSR)
// -----------------------------------------

// In this example, we're going to register a Particle.variable() with the cloud so that we can read the level of a FSR.

int fsr = A0; // This is the input pin where you read the value of the sensor.

int analogvalue; // Here we are declaring the integer variable analogvalue, which we will use later to store the value of the sensor.

void setup() {

    // This lets the device know which pin will be used to read incoming voltage.
    pinMode(fsr,INPUT);  // Our sensor pin is input (reading the sensor)

    // We are going to declare a Particle.variable() here so that we can access the value of the sensor from the cloud.
    Particle.variable("analogvalue", &analogvalue, INT);
    // This is saying that when we ask the cloud for "analogvalue", this will reference the variable analogvalue in this app, which is an integer variable.

}

void loop() {

    // check to see what the value of the sensor is and store it in the int variable analogvalue
    analogvalue = analogRead(fsr);
    delay(100);
    
}
```