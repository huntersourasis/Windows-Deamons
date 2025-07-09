# 🛠️ Windows Daemon / Service Setup (C & Python)

Create and manage background services (daemons) on Windows using **C** or **Python**. These services run silently in the background and are perfect for monitoring, logging, or persistent background tasks like file system crawlers.

---

## 🚀 Supported Languages

- ✅ C (via Windows API)
- ✅ Python (with `pywin32`)

---

## 📁 Project Structure

```
Windows-Daemons/
├── my_c_service.c           # C service source
├── logger.py                # Python service script
├── logger.exe               # Compiled C service
├── README.md                # This file
└── my_c_service_log.txt     # Log output
```

---

## 🐍 Python Service Setup

> 🧩 Requires: `pip install pywin32`

### 🔧 Install the Service

```bash
python logger.py install
```

### ▶ Manage the Service

```bash
python logger.py start      # Start the service
python logger.py stop       # Stop the service
python logger.py remove     # Uninstall the service
```

---

## 💻 C Service Setup

> 🛠 Compile using:
```bash
gcc my_c_service.c -o logger.exe -ladvapi32
```

### 🔧 Install the Service

```powershell
sc.exe create pathcrawler binPath= "C:\Full\Path\To\logger.exe"
```
> ⚠️ Make sure there is a **space** after `binPath=`

### ▶ Manage the C Service

```powershell
sc.exe start pathcrawler         # Start the service
sc.exe stop pathcrawler          # Stop the service
sc.exe query pathcrawler         # Check status
sc.exe delete pathcrawler        # Uninstall the service
```

---

## ⚠️ Common Errors & Fixes

| Error / Code                        | Cause                                | Fix                                 |
|------------------------------------|--------------------------------------|--------------------------------------|
| `Access is denied`                 | Using Microsoft Store Python         | Install Python from [python.org](https://www.python.org/) |
| `Cannot access log file`          | File is in use by service            | Stop or kill the service             |
| `sc.exe remove` fails              | `remove` is not a valid command      | Use `sc.exe delete` instead          |
| `1061: cannot accept control`     | Service stuck during startup         | Kill the process or reboot           |

---

## 📁 Log Output

Service logs output to:
```
C:\my_c_service_log.txt
```

Example entries:
```
C:\Windows
C:\Program Files
C:\Users\Admin\Documents
```

---

## 💡 Tips

- 🔐 Run CMD/PowerShell as **Administrator**
- 🔎 Check service status: `sc query <servicename>`
- 💀 Kill stuck services: `taskkill /IM logger.exe /F`
- 🔁 You can scan only certain file types with filters in C

---

## 🧠 Want More Features?

- [ ] Log only `.txt`, `.exe`, etc.
- [ ] Write logs to Event Viewer
- [ ] Auto-delete or rotate logs
- [ ] Self-uninstalling service
- [ ] Voice control via Maya AI

---

## 👨‍💻 Maintained By

**Sourasis Maity**  
Building system daemons and intelligent voice assistants for Windows.  
📫 *Happy coding!*
