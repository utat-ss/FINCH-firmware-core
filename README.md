# Firmware Core MCU libraries

This repo is for the development of complete MCU configurations, and code intended to be loaded onto flight MCUs. All other development and work using the Nucleo devkits is done in [firmware-dev](https://github.com/spacesys-finch/firmware-dev).

There are two child folders in this repo:

- [H743](H743/) holds a base MCU for the _STM32H743IIT6_, the 169-pin version of the H743. This is our high-powered MCU used for Pay-Elec.
    - This is slightly different from the _STM32H743**ZIT6**_ (144 pins) with more pins. Unless the Imaging Architecture project is able to overcome some challenges with voltage level translation, this is likely the model that will be used.
- [G431](G431/) holds a base MCU for the _STM32G431RBT6_, the 64-pin version of the G431. This is the general-purpose MCU used for OBC and ADCS.

The `main` branch serves as a basis, and other branches are used for specific subsystems and rebased as needed. If you need to add another onboard MCU model, contact the Firmware lead.

## How to use this repo (subsystem components)

1. Clone the repo onto your local machine; click the green "Clone" button in the top right corner, copy the URL, and run the following in your terminal to clone into a folder and enter it:

    ```bash
    git clone [URL]
    cd firmware-core
    ```

2. Fork a branch for the subsystem MCU you're targeting. Continuing with our HT323 reaction wheel example, you'll be programming the ADCS G431 MCU, so fork from that branch, using a name including the component and target MCU:

    ```bash
    git checkout ADCS-STM32G431RBT6
    git checkout -b HT323-driver-ADCS
    ```

3. Open STM32CubeIDE. Click "File", then "Open Projects from File System...". Click "Directory...", and select the `firmware-core` folder.
4. Leave the target MCU checked. For example, the ADCS MCU would be called `ADCS-STM32G431RBT6`, so only keep that one checked. Then click Finish to open the repo.
    - Similarly, make sure that your work from `firmware-dev` is also open.
5. Save your changes and push the branch to GitHub:

    ```bash
    git add .
    git commit -m "[HT323-driver] Initial commit"
    git push -u origin HT323-driver-ADCS
    ```

6. Copy over the contents/files of your work into the onboard MCU projects. Use the STM32CubeMX (.ioc) file to enable needed drivers and timing features.
7. Run all necessary builds, testing, and modifications needed to ensure that both the existing and new functionality works. For help, contact the relevant systems (ex. Firmware and ADCS in this case).
8. Once testing is complete, rebase your changes against the target branch so they will be added to the latest version of the MCU:

    ```bash
    git commit -m "Relevant commit message"
    git rebase ADCS-STM32G431RBT6
    git push --force
    ```

9. [Create a pull request](https://github.com/spacesys-finch/firmware-core/compare). The "base" branch will be the target (`ADCS-STM32G431RBT6`), and the "compare" will be your branch. Fill out the template and open the pull request.
10. Notify the relevant leads to perform a code review and have the changes merged.

## How to use this repo (subsystem MCU)

**These steps should be performed once per MCU. Make sure the MCU branch does not exist before following these steps.**

1. Clone the repo onto your local machine; click the green "Clone" button in the top right corner, copy the URL, and run the following in your terminal to clone into a folder and enter it:

    ```bash
    git clone [URL]
    cd firmware-core
    ```

2. Fork form the `main` branch to create a branch for the MCU, with the naming scheme `<SUBSYSTEM>-<MCU>`. For example, the ADCS is currently planned to use the STM32G431RBT6 MCU:

    ```bash
    git checkout -b ADCS-STM32G431RBT6
    ```

3. Open STM32CubeIDE. Click "File", then "Open Projects from File System...". Click "Directory...", and select the `firmware-core` folder.
4. Leave the template for the MCUs that you want to target checked. For example, ADCS would only leave `G431` checked. Then click Finish to open the repo.
5. Right click on the project in the Project Explorer on the left (the icon says "IDE"), and select Rename. Give your project the same name as the branch (ex. `ADCS-STM32G431RBT6`), leave the "Update references" box checked, and click Ok.
6. Delete the folder with template for the other MCUs.
7. Finally, commit the changes and push the branch to GitHub. In the terminal, from the `firmware-core` folder:

    ```bash
    git add .
    git commit -m "[ADCS-STM32G431RBT6] Initial commit"
    git push -u origin ADCS-STM32G431RBT6
    ```
