# pear-security
Next level PyQt5 browser security


## Overview

`security.dll` is a lightweight library designed to provide AES-256 encryption for sensitive data such as browser history. The library is simple to integrate into any project, requiring only a single DLL file and a few lines of code.

## Features
- **AES-256 Encryption**: Provides secure end-to-end encryption.
- **Standalone**: No external dependencies for users.
- **Cross-platform (Windows, with future support for other OS)**.

## Installation

1. **Download the DLL**  
   Get the latest `security.dll` from the [releases](https://github.com/pearsearch633/pear-security/releases) page and place it in your project directory.

2. **Integrate with Your Browser**  
   Add the following code to your project to enable encryption and decryption:

   ```python
   import ctypes
   import os

   dll_path = os.path.join(os.path.dirname(__file__), "security.dll")
   security_lib = ctypes.CDLL(dll_path)

   security_lib.encrypt_data.argtypes = [ctypes.c_char_p]
   security_lib.encrypt_data.restype = ctypes.c_char_p

   security_lib.decrypt_data.argtypes = [ctypes.c_char_p]
   security_lib.decrypt_data.restype = ctypes.c_char_p

   def encrypt(data: str) -> str:
       return security_lib.encrypt_data(data.encode('utf-8')).decode('utf-8')

   def decrypt(data: str) -> str:
       return security_lib.decrypt_data(data.encode('utf-8')).decode('utf-8')
