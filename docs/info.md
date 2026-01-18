# C Program Runner Chip

## How it works

This chip implements a simple C program interpreter that runs on an ILI9341 display with SD card support. When powered on, the system:

1. **Initializes the ILI9341 display** - Sets up the 240x320 TFT display with SPI communication
2. **Loads `program.c` from SD card** - Reads a C program file from the simulated SD card
3. **Displays the interface** - Shows program status, output values, and variable states
4. **Waits for user input** - The COMPILE_BUTTON triggers program execution
5. **Parses and executes C code** - The interpreter can handle:
   - Variable assignments (e.g., `x = 10;`)
   - Arithmetic expressions (e.g., `sum = x + y;`)
   - Print statements (e.g., `print(value);`)
   - Comments (e.g., `// This is a comment`)

The interpreter maintains variable storage and executes statements line by line, displaying results in real-time on the screen.

## How to test

1. **Power up the chip** - Connect VCC (3.3V) and GND
2. **Check display initialization** - The screen should show:
   - "C PROGRAM RUNNER" title
   - "FILE: program.c" status
   - "STATUS: READY" message
   - "Press button to run" instruction
3. **Press the COMPILE_BUTTON** - This triggers program execution
4. **Observe results** - The display will show:
   - Status changes to "RUNNING" then "READY"
   - Output value from the program
   - Variable values and their assignments
   - Any error messages if the program has syntax issues

## External hardware

- **ILI9341 TFT Display** (240x320 pixels, SPI interface)
  - Requires: VCC, GND, CS, RST, DC, MOSI, SCK, LED (backlight), MISO
- **SD Card Module** (for program storage)
  - Requires: SD_CS, SD_DI, SD_DO, SD_SCK, SD_CD (card detect)
- **Momentary push button** (for COMPILE_BUTTON)
  - Connect between COMPILE_BUTTON pin and GND (active low)
