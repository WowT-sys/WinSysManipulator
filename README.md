# WinSysManipulator

## Overview
**WinSysManipulator** is a Windows-based tool written in C that performs low-level system operations, including:
1. **Creating junctions (symbolic links)** between directories.
2. **Modifying the Windows registry** to schedule file operations during the next system reboot.

This tool demonstrates advanced techniques for file system and registry manipulation using the Windows API.

---

## Features
- **Junction Creation**: Creates a symbolic link (`C:\Program-Files`) that redirects to `C:\Program Files`.
- **Registry Modification**: Updates the `PendingFileRenameOperations` registry key to schedule file operations for the next reboot.
- **Low-Level System Access**: Utilizes Windows API functions like `DeviceIoControl` and `RegSetValueExW` for direct system manipulation.

---

## Requirements
- **Operating System**: Windows
- **Compiler**: A C compiler that supports Windows API (e.g., MinGW, MSVC)
- **Privileges**: Administrator privileges are required to run the program.

---

## Installation

### 1. **Clone the Repository**
Clone the repository to your local machine:
```bash
git clone https://github.com/WowT-sys/WinSysManipulator.git
cd WinSysManipulator
```

### 2. **Compile the Program**
Compile the program using a C compiler. For example:
```bash
gcc -o WinSysManipulator WinSysManipulator.c
```

### 3. **Run the Program**
Run the compiled program as an administrator:
```bash
WinSysManipulator.exe
```

---

## Usage

### Junction Creation
The program creates a junction (`C:\Program-Files`) that redirects to `C:\Program Files`. This allows redirection of file or directory access.

### Registry Modification
The program modifies the `PendingFileRenameOperations` registry key to schedule file operations involving `CrowdStrike\CSFalconService.exe` for the next system reboot.

---

## Output
If successful, the program will output:
```
Junction created successfully.
PendingFileRenameOperations set successfully.
```

If any operation fails, the program will return an error code:
- `0` if the junction creation fails.
- `2` if the registry modification fails.

---

## Code Breakdown

### Key Functions
1. **`setup_junction()`**:
   - Creates a junction (`C:\Program-Files`) that redirects to `C:\Program Files`.

2. **`set_registry_value()`**:
   - Modifies the `PendingFileRenameOperations` registry key to schedule file operations.

3. **`main()`**:
   - Orchestrates the junction creation and registry modification.

---

## Warning
⚠️ **CAUTION**:  
This program performs low-level system operations that can:
- Disrupt system functionality if used improperly.
- Bypass security mechanisms or disable security software.

Use this tool responsibly and only in environments where you have explicit permission to perform such operations.

---

## Legal Disclaimer
This program is provided for **educational and research purposes only**. The author is not responsible for any misuse or damage caused by this program. Use it at your own risk and ensure compliance with applicable laws and regulations.

---

## Contributing
Contributions are welcome! If you have suggestions or improvements, feel free to open an issue or submit a pull request.
