# Firmware Core MCU libraries

This repo is for the development of complete MCU configurations, and code intended to be loaded onto flight MCUs. All other development is done in [firmware-dev](https://github.com/spacesys-finch/firmware-dev).

There are two child folders in this repo:

- [H743](H743/) holds a base MCU for the _STM32H743IIT6_, the 169-pin version of the H743. This is our high-powered MCU used for Pay-Elec.
  - This is slightly different from the _STM32H743**ZIT6**_ (144 pins) with more pins. Unless the Imaging Architecture project is able to overcome some challenges with voltage level translation, this is likely the model that will be used.
- [G431](G431/) holds a base MCU for the _STM32G431RBT6, the 64-pin version of the G431. This is the general-purpose MCU used for OBC and ADCS.

The `main` branch serves as a basis, and other branches are used for specific subsystems and rebased as needed.
