# OpenMind OM1 – Full Setup Guide on WSL (With Audio Input)

This guide walks through a **clean, working installation of OpenMind OM1 on WSL2**, including
fixing audio input so voice interaction works in simulation (Spot / WebSim).

It is written for users who:
- Are on Windows 10 or 11
- Use WSL2 (Ubuntu)
- Want to run OM1 **without robot hardware**
- Want real microphone input in simulation


## System Requirements

- Windows 10 / 11
- WSL2 installed
- Ubuntu 22.04 (recommended)
- Microphone connected to host machine
- OM API key

---

## Step 1: Install WSL2 and Ubuntu

If WSL is not installed:

```powershell
wsl --install
