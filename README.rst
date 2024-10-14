Trouble shooting
****************

This repository is a copy of the "samples/subsys/fs/fs_sample" Zephyr OS example. It is used to access the microSD on the XMC4700 Relax Kit.
Unfortunately, I am getting error messages from the flashed code.

.. code-block:: console

    *** Booting Zephyr OS build v3.7.0-4375-g52540d841263 ***
    [00:00:00.206,000] <err> sd: Card error on CMD0
    [00:00:00.206,000] <inf> sd: Card does not support CMD8, assuming legacy card
    [00:00:00.409,000] <err> main: Storage init ERROR!
    [00:00:00.615,000] <err> sd: Card error on CMD0
    [00:00:00.615,000] <inf> sd: Card does not support CMD8, assuming legacy card
    [00:00:00.817,000] <err> fs: fs mount error (-5)
    Error mounting disk.
    [00:00:00.817,000] <err> fs: fs not mounted (mp == 0x20000000)


I think there is a bug in the devicetree overlay for the XMC4700. Because during compilation I get the following message.

.. code-block:: console

    ....
    -- Including generated dts.cmake file: /home/trifu/Projekte/ZephyrOS/zephyrproject/trifu_projects/XMC4700_microSD/build/zephyr/dts.cmake
    CMake Warning at /home/trifu/Projekte/ZephyrOS/zephyrproject/zephyr/cmake/modules/dts.cmake:415 (message):
    dtc raised one or more warnings:

    
    /home/trifu/Projekte/ZephyrOS/zephyrproject/trifu_projects/XMC4700_microSD/build/zephyr/zephyr.dts:345.27-368.5:
    Warning (spi_bus_bridge): /soc/usic@40030200: node name for SPI buses
    should be 'spi'

    <stdout>: Warning (spi_bus_reg): Failed prerequisite 'spi_bus_bridge'

    Call Stack (most recent call first):
    /home/trifu/Projekte/ZephyrOS/zephyrproject/zephyr/cmake/modules/zephyr_default.cmake:133 (include)
    /home/trifu/Projekte/ZephyrOS/zephyrproject/zephyr/share/zephyr-package/cmake/ZephyrConfig.cmake:66 (include)
    /home/trifu/Projekte/ZephyrOS/zephyrproject/zephyr/share/zephyr-package/cmake/ZephyrConfig.cmake:92 (include_boilerplate)
    CMakeLists.txt:4 (find_package)


    Parsing /home/trifu/Projekte/ZephyrOS/zephyrproject/trifu_projects/XMC4700_microSD/Kconfig
    ....


