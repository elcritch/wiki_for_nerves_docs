# UART FAQ's

How to use UART's in Nerves: 
- See [Circuits.UART](https://github.com/elixir-circuits/circuits_uart) or the [Circuit.UART Docs](https://hexdocs.pm/circuits_uart/Circuits.UART.html)

## Basics regarding UART's

You can use a USB-to-serial converter, aka and FTDI, like this one from Adafruit [FTDI](https://www.adafruit.com/product/954). 

However, this can cause weird issues with your computer if your device's power and your computer power have different grounds. They can form [ground loops](https://duet3d.dozuki.com/Wiki/USB_ground_loops). 

My preference therefore is to use another SBC system with a standard debian image as an intermediate and connect to that via wifi/ethernet (not over it's USB cable). This helps prevents damage to your main computer. This is similar to a using a RPi to connect to an Arduino like [Rpi<->Arduino](https://circuitdigest.com/microcontroller-projects/arduino-raspberry-pi-interfacing) but can also be used to connect RPi0w<->Rpi similar. 


## Debugging UART Ports

### Note on RPi3's (& Rpi4's?)

When using UART's on RPi3's using the default Nerves System that `dtoverlay=pi3-miniuart-bt` is configued which switches the RPi3's UART pins to use `ttyAMA0`. 

### Phantom Zeroes / Sparadic Values

Sometimes you can get seemingly random values like these: 

```elixir
iex> flush
{:circuits_uart, "ttyS0", <0,0,0>}
{:circuits_uart, "ttyS0", <0>}
{:circuits_uart, "ttyS0", <0, 0, 0, 0>}
```

If this occurs, check your `speed:` settings. Setting the `speed:` parameter incorrectly when starting Circuits.UART (or any program that reads the UART) can result in the hardware picking up zeroes, or more rarely, random values since it's not synchronized with the signals on the actual RX/TX lines. This can also happen on SPI/I2C devices. 


