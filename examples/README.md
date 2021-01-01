### Быстрый старт

* `CMakeLists.txt` пример проекта.

* `.vscode` настройки VS Code при интеграция сборки с отладчиком.
##### cmake-kits.json
```javascript
[
    {
        "name": "GCC ARM NONE EABI",
        "toolchainFile": "arm-cmake-toolchains/arm-gcc-toolchain.cmake"
    }
]
```

##### settings.json
```javascript
    "cortex-debug.armToolchainPath": "/usr/bin",
    "cortex-debug.openocdPath": "/usr/bin/openocd"
```

##### launch.json
```javascript
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "OpenOCD",
            "cwd": "${workspaceRoot}",
            "executable": "./build/blinking_led.elf", // Путь к исполняемому файлу
            "request": "launch", // Вид запуска
            "type": "cortex-debug",
            // Путь к нативному компилятору GCC (arm-none-eabi-gdb)
            "armToolchainPath": "/usr/bin/",
            "serverpath": "/usr/bin/openocd", // Исполняемый файл отладчика
            "servertype": "openocd", // Тип отладчика
            "serialNumber": "", // Серийный номер отладчика(если не один)
            "interface": "swd", // Интерфейс отладчка jtag/swd
            "runToMain": true, // Старт с функции main
            "device": "STM32F103RC", // МК
            "svdFile": "/home/orfanidi/SVD_Files/ST/STM32F103.svd", // Файл карты памяти МК для отладки
            "configFiles": [
                "STM32F103RC.cfg" // Файл конфигурации отладчика OpenOCD
            ]
        }
    ]
}
```

#### STM32F103RC.cfg файл конфигурации отладчика OpenOCD.
```cmd
source [find interface/jlink.cfg]

transport select "swd"

source [find target/stm32f1x.cfg]
```
