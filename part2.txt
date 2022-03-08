#include "mbed.h"

static BufferedSerial pc(USBTX, USBRX);

int main(){

    DigitalOut led(LED1); //set LED1 as an output
    
    // variable declarations
    char msg1[] = "Type 1/0 to turn ON or OFF the LED \r\n";
    char msg2[] = "Please use 1/0 to control the LED \r\n";
    char command;
    pc.write(msg1, sizeof(msg1)); // print on the console
    
    while (true) // infinite loop
        {
            pc.read(&command, 1); //read the keyboard
            if(command =='1'){
            led = 1; // ON LED if 1 is received
            }else if(command == '0'){
            led = 0; // OFF LED if 0 is received
            }else{
            pc.write(msg2, sizeof(msg2));
        }
    }
}