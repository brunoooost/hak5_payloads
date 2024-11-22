# Make Big File for MacOS, Windows and GNU/Linux

This **DuckyScript** code determines the operating system of the target machine (`$_OS`) and creates a file of a specified size on macOS, Linux, or Windows using system-specific commands.

### Code Explanation

1. **Operating System Check**:
   - The script begins with conditional checks for `$_OS` to determine whether the system is **macOS**, **Linux**, or **Windows**.

---

2. **For macOS**:
   ```ducky
   IF ($_OS == MACOS) THEN
   GUI SPACE
   DELAY #STANDARD_DELAY
   STRINGLN TERMINAL
   DELAY #STANDARD_DELAY
   STRINGLN mkfile #FILE_SIZE_IN_GBg #FILE_PATH#FILE_NAME; exit
   ```
   - **GUI SPACE**: Simulates pressing `Cmd + Space`, opening **Spotlight**.
   - **STRINGLN TERMINAL**: Types "Terminal" and presses `Enter` to open the macOS terminal.
   - **mkfile**: Uses the `mkfile` command to create a file:
     - `#FILE_SIZE_IN_GBg`: Specifies the file size in gigabytes.
     - `#FILE_PATH#FILE_NAME`: Specifies the file's path and name.
   - **exit**: Closes the terminal after execution.

---

3. **For Linux**:
   ```ducky
   ELSE IF ($_OS == LINUX) THEN
       CTRL-ALT t
   DELAY #STANDARD_DELAY
   STRINGLN fallocate -l #FILE_SIZE_IN_GBG #FILE_PATH#FILE_NAME; exit
   ```
   - **CTRL-ALT t**: Opens the Linux terminal using a common keyboard shortcut.
   - **fallocate**: Uses the `fallocate` command to create a file:
     - `-l #FILE_SIZE_IN_GBG`: Specifies the file size in gigabytes.
     - `#FILE_PATH#FILE_NAME`: Specifies the file's path and name.
   - **exit**: Closes the terminal after execution.

---

4. **For Windows**:
   ```ducky
   ELSE IF ($_OS == WINDOWS) THEN
   GUI r
   DELAY #STANDARD_DELAY
   STRING cmd
   CTRL SHIFT ENTER
   DELAY #STANDARD_DELAY
   STRINGLN fsutil file createnew #FILE_PATH#FILE_NAME #FILE_SIZE_IN_GB737418240; exit
   ```
   - **GUI r**: Simulates `Win + R`, opening the Run dialog.
   - **STRING cmd**: Types "cmd" to launch the Command Prompt.
   - **CTRL SHIFT ENTER**: Opens the Command Prompt as an administrator.
   - **fsutil file createnew**: Uses the `fsutil` command to create a file:
     - `#FILE_PATH#FILE_NAME`: Specifies the file's path and name.
     - `#FILE_SIZE_IN_GB737418240`: Calculates the file size in bytes (N GB = N,073,741,824 bytes).
   - **exit**: Closes the Command Prompt after execution.

---

### Key Notes:
- **Placeholders**: The script uses placeholders (`#FILE_SIZE_IN_GBg`, `#FILE_PATH#FILE_NAME`) that must be replaced with actual values before execution.
- **#STANDARD_DELAY**: This placeholder ensures a delay between actions to allow the system to process commands.
- **Cross-platform Approach**: The script dynamically adapts to the detected OS, ensuring compatibility and proper command execution on macOS, Linux, and Windows.
