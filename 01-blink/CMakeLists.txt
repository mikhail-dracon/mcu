# Требуем минимальную версию cmake
cmake_minimum_required(VERSION 3.15)

# Задаем параметры для Pico SDK
set(PICO_BOARD pico)
set(PICO_PLATFORM rp2040)

# Подключаем Pico SDK
include(pico_sdk_import.cmake)

# Создаем проект
project(01_blink)

# Инициализируем SDK
pico_sdk_init()

# Добавляем файлы с исходным кодом
add_executable(01_blink
    ${CMAKE_CURRENT_SOURCE_DIR}/main.c
)

# Указываем библиотеки
target_link_libraries(01_blink
    pico_stdlib
)

# Указываем линкер скрипт (обрати внимание на .ld вместо .ltd)
pico_set_linker_script(01_blink ${CMAKE_CURRENT_SOURCE_DIR}/memmap_rp2040.ld)

# Добавляем дополнительные форматы (uf2, bin, hex)
pico_add_extra_outputs(01_blink)