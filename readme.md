# Offline ComfyUI Install for RTX 5090 / Torch 2.9 / CUDA 12.8  
A practical, repeatable, offline installation method for running ComfyUI on a 5090 or any other Blackwell-series NVIDIA GPU.  

This repo is not theoretical.  
It exists because after fighting through dependency hell, mismatched wheels, broken builds, and pip silently replacing versions I never asked for, I finally landed on a setup that works. It works repeatedly, cleanly, and without pulling anything online once the wheels are in place.

This guide is built from direct experience, not guesswork.

## What this repo solves
- A clean offline installation with zero pip shenanigans.  
- Correct Torch 2.9 + CUDA 12.8 stack required for RTX 5090.  
- A portable ComfyUI environment that cannot be contaminated by other Python installs.  
- A strict wheel install order that prevents the usual DLL explosions.  
- FlashAttention, SageAttention, and Triton all installed correctly.  
- No reliance on Xformers (still required as a placeholder).  
- A known-good workflow template fix for ComfyUI Portable 0.2.4.  
- Hidden dependencies required for ComfyUI-Manager to appear.

## Why Torch 2.9 matters for the 5090
The RTX 5090 (Blackwell) architecture will not perform correctly on Torch 2.8 or earlier.  
Torch 2.9 introduces the necessary CUDA 12.8 support and updated kernels.  
If you're running a 5090 and still on Torch 2.8, you're leaving performance on the table and inviting compatibility problems.

This repo takes care of matching:
- Python version  
- CUDA version  
- Torch major/minor  
- ABI compatibility  
- Triton kernel compatibility  
- FlashAttention expectations  

Everything here is aligned to run properly on Windows with a 5090.

## What this repo does not do
- It does not use pip to fetch anything online.  
- It does not mix Python versions.  
- It does not assume pip knows better than you.  
- It does not assume a venv magically isolates dependencies.  
- It does not tell you “this should work” based on documentation instead of real-world testing.  

This method is built around what actually works, not what should work.

## Who this is for
- Anyone with a 5090 or dual-GPU system (4090 + 5090).  
- Anyone tired of pip downgrading or upgrading their wheels behind their back.  
- Anyone who wants a self-contained, predictable environment.  
- Anyone who needs ComfyUI fully accelerated with FlashAttention, SageAttention, and Triton.  

## Quick Overview
1. Use ComfyUI Portable 0.2.4 (requires Python 3.12).  
2. Place all wheels in a local directory.  
3. Install in the exact order shown in `WHEEL_ORDER.md`.  
4. Replace the broken template package with the working version.  
5. Install GitPython and gitdb so ComfyUI-Manager appears.  
6. Launch using one of the GPU launchers if you're running dual GPUs.  

Full step-by-step: see `INSTALL.md`.  
Troubleshooting: see `TROUBLESHOOTING.md`.  
Wheel order reference: see `WHEEL_ORDER.md`.

If you want to contribute corrections, refinements, or additional GPU benchmarks, open an issue or pull request. This project grew out of necessity, and I expect others will improve it over time.
