# A Project Template for the Tiva C Series Launchpad

This is an example project for the Tiva C Series Launchpad (EK-TM4C123GXL).

It provides:

- A sample application that blinks the LED on the board in different colors.
- A Vagrant based VM that can be used for building, running tests and deploying to a target board.
- Example unit tests that can be run with Ceedling on the host.
- Builds the TivaWare library and the application for the target.
- Load to the target board.

## Tiva Launchpad

The [Tiva C Series Launchpad (EK-TM4C123GXL)](http://www.ti.com/ww/en/launchpad/launchpads-connected-ek-tm4c123gxl.html) is a low-cost evaluation board from TI for their powerful line of ARM Cortex-M4F-based microcontrollers. You can get it for [about $13](https://store.ti.com/Tiva-C-LaunchPad.aspx).

Tiva C Series Launchpad (EK-TM4C123GXL):

<img src="launchpad-tivac.jpg" width="400">

## Requirements

This build environment requires that [Vagrant](http://www.vagrantup.com/downloads) and [Virtualbox](https://www.virtualbox.org/wiki/Downloads) are installed.

## Starting the Environment

Launch the environment with: `vagrant up`.

Connect to it with: `vagrant ssh`.

Exit the environment with `exit`.

## Building and Loading

Execute all unit tests with `ceedling test:all`.

Run a single test with `ceedling test:<module>`, e.g. `ceedling test:led`.

Load the app on the board with: `ceedling load`.

The load command also builds the application if necessary. Just build the application with: `ceedling release`.

## Example Project Description

Included with this environment is an example project with unit tests. When loaded and run the Launchpad LED flashes -- switching between red, green and blue.

There are two software modules -- **state** and **led** -- used to determine the LED color (the state) and to set the color of the LED. Each of these modules implements units tests. Unit tests are in the **test** folder.

In the **led** module, the TivaWare Peripheral Driver Library is used to initialize and control the GPIO pins connected the multi-color LED. This library is in **lib/TivaWare/driverlib** and is built automatically if necessary.

# TODO
- Add Github actions
- Update compiler
- I think we should remove the dockerfile (and ev scripts) since we need access to the USB device.
