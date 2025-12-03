# Installation Instructions (Offline ComfyUI + Torch 2.9 + CUDA 12.8)

This is the full installation procedure I personally tested on my own system.  
The goal was simple: no pip deciding what it thinks is better, no internet pulls, no cross-contamination, and no surprises.

Everything here assumes you are using:
- ComfyUI Portable 0.2.4  
- Embedded Python 3.12  
- CUDA 12.8 wheels  
- Torch 2.9  

## 1. Prepare the environment
Create a folder such as:
C:\AI\Offline_Wheels\Torch2.9

Place every wheel inside that folder.  
Do not rename anything.  
Do not mix wheel sources.  
Do not mix CUDA versions.  
Keep this folder clean.

## 2. Extract ComfyUI Portable 0.2.4
This build includes Python 3.12 embedded, which is required for Torch 2.9.
You are not using your system Python.  
You are not using pip from system installations.  
Everything stays in this portable environment.

## 3. Open a terminal inside the portable Python directory
Shift + Right-click → “Open PowerShell window here.”

## 4. Install wheels in the exact order
See `WHEEL_ORDER.md` for the sequence.

Torch must go first.  
TorchVision second.  
TorchAudio third.  
Triton before FlashAttention.  
FlashAttention before SageAttention.  
Xformers gets installed, but only as a dependency placeholder.

The order is not negotiable.  
Changing it breaks the environment.

## 5. Install ComfyUI-Manager dependencies
These two are required or the Manager will not show up:
- gitdb  
- GitPython

Install them inside the embedded Python environment.

## 6. Fix the template package
ComfyUI Portable 0.2.4 cannot use the 0.7.x template package.  
Replace the broken version with the older 0.2.4 templates.

The Template Fix folder in this repo includes the working version.

## 7. Launch ComfyUI
Use the included launchers inside the LAUNCHERS directory:
- `run_5090_only.bat` if you want ComfyUI to ignore the 4090.  
- `run_dual_gpu.bat` if you want ComfyUI to see both.  

## 8. Expect one harmless popup
Xformers will complain about an entry point.  
This is expected under Torch 2.9 on Windows.  
FlashAttention and Triton take over Xformers’ role.  

Click through it.  
Performance is unaffected.

At this point, you’re fully operational with a clean offline install.
