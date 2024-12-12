# rfid_project1
Execution Flow of the RFID Project
System Startup:

All peripherals are initialized (UART, SPI, RTC, LCD, KPM).
The system synchronizes the date and time with an external source (PC).
The admin card ID is loaded from the EEPROM.

Waiting for Card:

The system displays a "PLACE CARD" prompt and the current time and date on the LCD.
The system is waiting for a card scan via UART1 (from the RFID reader).

Card Scanning:

When a card is scanned, the UART_ISR() receives the card ID via UART1.
The card ID is compared with the admin card ID stored in the EEPROM.
The card ID is compared with the admin card ID stored in the EEPROM.
If the card is recognized as the admin card, the system displays "ADMIN ACCESS" and allows the admin to perform specific tasks via the keypad.
If it’s a regular user card, the system logs the card ID and timestamps it with the current time and date, sending this data to the PC for record-keeping.

Admin Functions:

If an external interrupt is triggered (e.g., pressing an admin button), the menu() function is called.
The admin can change settings like the admin card ID or password, view attendance logs, or reset data.
Data Logging and Processing:

Card data (ID, timestamp) is sent via UART0 to the PC for further processing, such as updating attendance records.
The PC can respond with acknowledgment messages (e.g., "Attendance Updated"), which are handled by the system.


Continuous Operation:

The system continuously monitors for RFID card scans and admin interactions, logging attendance and providing real-time feedback via the LCD.
