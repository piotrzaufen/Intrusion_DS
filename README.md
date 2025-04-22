# 🛡️ Windows PowerShell IDS – Lightweight Host-based Monitoring Suite

This project is a lightweight, modular Intrusion Detection System (IDS) written entirely in PowerShell. It provides real-time and on-demand system diagnostics by monitoring key areas of the Windows operating system, including CPU usage, RAM activity, network behavior, file processes, registry changes, and disk performance.

> ⚠️ **Disclaimer:** This tool is designed for educational and experimental use. It does not replace professional IDS/IPS solutions. Use at your own risk.

## 📦 Features

- ✅ Pure PowerShell, no external dependencies  
- ✅ Modular architecture (run only what you need)  
- ✅ Logs system activities to plain text files  
- ✅ Real-time or snapshot mode  
- ✅ Works on most modern Windows systems  
- ✅ Useful for malware sandboxing, forensic research, or system behavior analysis  

## 🧰 Requirements

- PowerShell 5.1 or later  
- Administrator privileges (for certain system calls)  
- Windows 10 / 11 / Server  
- Internet connection: ❌ Not required  

## 🗂️ File Overview

Each PowerShell script represents a self-contained module for monitoring a specific aspect of system activity:

| File                | Functionality                                        |
|---------------------|-----------------------------------------------------|
| `caly.ps1`          | Central script – executes and orchestrates modules  |
| `cpu.ps1`           | Tracks CPU usage per process and logs spikes        |
| `disk.ps1`          | Monitors disk read/write activity and throughput    |
| `ram.ps1`           | Logs memory usage trends and anomalies              |
| `file_proccess.ps1` | Scans active file handles and launched processes    |
| `network.ps1`       | Observes open connections and unusual network ports |
| `registry.ps1`      | Checks registry changes (HKCU/HKLM, auto-run keys)  |

## 🖥️ Installation

1. Download or clone the repository:  
   `git clone https://github.com/yourusername/powershell-ids`  

2. Ensure all `.ps1` files are in the **same folder**.  

3. (Optional) Unblock files if downloaded from the internet:  
   `Get-ChildItem *.ps1 | Unblock-File`  

## 🚀 Usage

### 🔧 Run the whole suite:

```powershell
Start-Process powershell -Verb runAs
cd path\to\your\scripts
.\caly.ps1
```

### 🧩 Run individual modules:

```powershell
.\cpu.ps1          # CPU monitoring
.\network.ps1      # Network monitoring
.\registry.ps1     # Registry snapshot and diff
```

Each script will generate logs inside the working directory (or `%TEMP%` if configured).

## 📄 Sample Log Output

```
[12:03:45] [CPU] Chrome.exe – 85% usage
[12:03:48] [RAM] Memory usage exceeded threshold: 89%
[12:03:52] [NET] Suspicious outbound port: 31337
[12:04:01] [REG] HKCU\Software\Microsoft\Windows\CurrentVersion\Run modified
```

## 🧠 Design Philosophy

- No GUI – pure shell  
- Easy to extend and adapt  
- Understandable even for beginners  
- Log everything → analyze later  
- Designed for **off-the-grid** environments  

## 🚧 Roadmap (maybe)

- [ ] Add event log scraping (`eventlog.ps1`)  
- [ ] Add scheduled task auditing  
- [ ] Introduce time-based baselining  
- [ ] Create an HTML report generator  
- [ ] Optional email notifications  

## 🛠️ Tips for Usage

- Use **Task Scheduler** to run `caly.ps1` every 5 minutes  
- Use **Sysinternals Process Explorer** alongside for correlation  
- Place on **honeypot VM** for behavior capture  
- Redirect output to shared logs for network-wide IDS  

## 📜 License

This project is open-source under the AAP3 License. Do what you want, but don’t blame me if your PC sets itself on fire 🔥.

> If it blinks, logs, or spikes — this script will see it.  
> Simple PowerShell can still be dangerous 💥
