# Windows Junction and Registry Manipulation Tool

## Overview
This program is a Windows-based tool written in C that performs two key operations:
1. **Creates a junction (symbolic link)** between two directories.
2. **Modifies the Windows registry** to schedule file operations during the next system reboot.

It demonstrates low-level system manipulation techniques, including reparse point creation and registry key modification.

---

## Features
- **Junction Creation**: Creates a symbolic link (`C:\Program-Files`) that redirects to `C:\Program Files`.
- **Registry Modification**: Updates the `PendingFileRenameOperations` registry key to schedule file operations for the next reboot.
- **Low-Level System Access**: Uses Windows API functions like `DeviceIoControl` and `RegSetValueExW` for direct system manipulation.

---

## How It Works

### 1. **Junction Creation**
The program creates a junction (`C:\Program-Files`) that redirects to `C:\Program Files`. This is achieved by:
- Opening the source directory with reparse point manipulation flags.
- Setting a reparse point using the `FSCTL_SET_REPARSE_POINT` control code.

### 2. **Registry Modification**
The program modifies the `PendingFileRenameOperations` registry key:
- **Key**: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager`
- **Value**: Adds a multi-string (`REG_MULTI_SZ`) entry to schedule file operations involving `CrowdStrike\CSFalconService.exe`.

---

## Requirements
- **Operating System**: Windows
- **Compiler**: A C compiler that supports Windows API (e.g., MinGW, MSVC)
- **Privileges**: Administrator privileges are required to run the program.

---

## Usage

### 1. **Clone the Repository**
Clone the repository or download the source code:
```bash
git clone https://github.com/your-username/junction-registry-tool.git
cd junction-registry-tool
```

### 2. **Compile the Program**
Compile the program using a C compiler. For example:
```bash
gcc -o junction-tool junction-tool.c
```

### 3. **Run the Program**
Run the compiled program as an administrator:
```bash
junction-tool.exe
```

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
