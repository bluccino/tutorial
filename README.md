![Bluccino Banner](https://user-images.githubusercontent.com/39674928/145687742-748bacf8-e285-45de-ac3b-af922959222a.jpg)


## What the Hell is Bluccino?

#### Bluccino Sweet Spots

* Bluccino is a messaging framework for event driven applications
* Bluccino is a rapid prototyping platform for Bluetooth BLE and Mesh networking applications
* Bluccino app code closes-up the essential (event driven) message flow by super-super simple code while blurring out all unessential details
* Bluccino is a simple and elegant language independent unit testing framework (mocking platform)

#### But there's even more ...

* Bluccino is a programming philosophy for platform independent Bluetooth networking applications
* Bluccino is platform, hardware and language independent (C, C++, Python, ...)
* Bluccino is a universal paradigm for event driven system
* Bluccino saves efforts, cost and development time
* Bluccino saves efforts, cost and development time
* Bluccino is open source with open tutorials
* Bluccino is a slim code layer
* Bluccino is awesome and makes great fun

## Lot's of bold statements, but what exactly can be done with Bluccino?

Bluccino was developed in parallel to the firmware development of our Bluenetics connector.
This is a Bluetooth mesh application, running either on one or alternatively on two processors, which also needs to offer some small BLE service set. When we learnt about Bluetooth mesh we started to study the simplest Zephyr mesh example which is called onoff_app (zephyr/samples/boards/nrf/mesh/onoff-app). The README file of this app sample mentions the following text

```
This is a simple application demonstrating a Bluetooth mesh multi-element node.
Each element has a mesh onoff client and server
model which controls one of the 4 sets of buttons and LEDs .
```

This sounded promising, especially the phrase 'simple'. When we examined the 'simple application' we found one source file main.c which has 647 lines. Whoppa - more than 600 lines of source code for a 'simple application'? Let's go back to the year 1978 when Brian W. Kernighan and Dennis M. Ritchie published their book "The C Programming Language". In a very early section they presented the world's most famous program:  

<p align="center">
   <img src="https://user-images.githubusercontent.com/17394277/145695547-f0345886-8ad6-487f-973e-6e99c6c4ccbc.png" width="400">
</p>

Whoppa - this is what we would call a 'simple' program - five non-blank code lines! But let's keep it as it is and call the 647-line source code of onoff_app a 'simple application', what would just mean that 'hello world' is super-super-super simple.

If we analyse the 'onoff_app' and ask what the code exactlay does when the node is provisioned (on-boarded to a mesh network), then below diagram will tell us everything: The phrase 'for (i=1:4)' just means that we have 4 similar setups, each setup (refering to index i) comprising a button, a mesh client model, a mesh server model and an LED. The i-th button is connected with the i-th client, indicating that a button preess would send an ON message via Bluetooth mesh to the i-th server, while a double button press causes the i-th client to send an OFF message to the i-th server which is forwarded as an ON or OFF message to the LED module causing the i-th LED going either on or off. That's it.  

<p align="center">
  <img src="https://user-images.githubusercontent.com/17394277/145696057-b7fba735-ed74-4f4e-b8b9-9a1e0d1c1407.png" width="600">
</p>

Let's see now the C++ program running such functionality on a Bluccino framework!

<p align="center">
   <img src="https://user-images.githubusercontent.com/17394277/145696286-a38c4422-be82-47da-837c-e6a5cef88d17.png" width="600">
</p>

As the C++ code has 25 lines instead of 5 we will intentionally avoid to call this code super-super-super simple, but the reader might agree that we deal with a super-super simple Bluetooth Mesh app. What we see is a button object of class Button, a client object (cli) of class GooCli (generic OnOff client), and a server object (srv) of class GooSrv (generic OnOff server). When the button is pressed the button module fires a message which by subscription of the button's when-callback will forward the OnOff message to the client. The client sends the message via Bluetooth channel to the server, which fires the received message to the server's when-callback, which will forward the message to the LED module causing the LED going ON or OFF

## The Bluccino Effect

The whole high-level semantics of a more than 600 line's source code is summarized by a C++ code chunk of 25 lines?

<p align="center">
  <img src="https://user-images.githubusercontent.com/17394277/145707739-c5629929-801c-4625-8259-06e20cfef7ff.png" width="200">
</p>


#### We call it the *Bluccino effect*:

* Close-up the essential app workflow
* in terms of a super-super simple code
* while blurring out the unessential details 


## Is Bluccino Free?

For the firmware development at Bluenetics Bluccino brought a huge value. 
* the efficiency of writing re-usable pre-tested software modules
* the clear software architecture which is defined within each Bluccino application
* the rapid development of a clear application message flow framework
* the efficient module interfaces
* the easy possibility of single module testing (utilizing Blucino's mocking capabilities)
* the re-usability of software modules (we use modules both on a nRF52832 and STM32L051 SoC)
increased the efficiency of software development at Bluenetics by more than a factor of 10! 

If you don't make money with Bluccino then we will leave you such benefit for free, and you don't have to give us money, since in such case Bluccino is free to use for you. 

On the other hand if you are making money with Bluccino, give us a little back for the value we provide to you! Does this sound fair? 

Whether you use Bluccino for commercial or non-commercial use you need a license for it. This license is included in the git repository, you are not allowed to download the code without the license document, and you implicitely agree to the license terms whenever you download the repository including the license document. You should be aware that this license always grants you free non-commercial use of the Bluccino code. For commercial use contact us please, you will see the license is affordable, no matter whether you are a big enterprise or a tiny start-up company.  

## Want to see Bluccino in Action?

Definitely a great idea! Let's go and see an intro!
