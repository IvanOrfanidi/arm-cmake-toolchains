## arm-cmake-toolchains
Тулчейн файлы интеграции CMake с компилятором GCC(arm-none-eabi)
Отладчик `gdb` можно установить из пакета `gdb-multiarch`.
После прописать линк на него:
`ln -s /usr/bin/gdb-multiarch /usr/bin/arm-none-eabi-gdb`.

### Файлы
* `arm-gcc-toolchain.cmake` - тулчейн файл для компилятора GCC
* `utils.cmake` - тулчейн файл для генерации hex/bin файлов.
* `examples` - папка с примерами быстрого старта.

### Примеры
В папке `examples` находятся:
* пример `CMakeLists.txt` проекта;
* в папке `.vscode` настройки VS Code при интеграция сборки с отладчиком;
* файл конфигурации отладчика OpenOCD.
