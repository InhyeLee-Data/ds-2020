# hall effect

*measures magnetic field*

Products: [Hall effect sensor - US5881LUA](https://www.adafruit.com/product/158) and [High-strength 'rare earth' magnet](https://www.adafruit.com/product/9)

#### Tools needed: 

- Particle Photon or Electron
- Hook up wires
- 10K ohm resistor

## Setup

![photo of setup](img/hall.JPG)

## Starter Code

*Adapted from an example in the [Particle docs](https://docs.particle.io/guide/getting-started/examples/photon/#read-your-photoresistor-function-and-variable)*

``` cpp
// -----------------------------------------
// Hall effect sensor
// -----------------------------------------

// In this example, we're going to register a Particle.variable() with the cloud so that we can read the status of a hall effect sensor.

int hall = D0; // This is the input pin where you read the value of the sensor.

int analogvalue; // Here we are declaring the integer variable analogvalue, which we will use later to store the value of the sensor.

void setup() {

    // This lets the device know which pin will be used to read incoming voltage.
    pinMode(hall,INPUT);  // Our sensor pin is input (reading the sensor)

    // We are going to declare a Particle.variable() here so that we can access the value of the sensor from the cloud.
    Particle.variable("analogvalue", &analogvalue, INT);
    // This is saying that when we ask the cloud for "analogvalue", this will reference the variable analogvalue in this app, which is an integer variable.

}

void loop() {

    if (digitalRead(hall) == HIGH) {

        // =0 if magnet is not present
        analogvalue = 0;
        delay(100);
        
    }
    
    else {

        // =1 if manget is present
        analogvalue = 1;
        delay(100);
        
    }
    
}
```

