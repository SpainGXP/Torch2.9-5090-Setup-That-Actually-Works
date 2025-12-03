# Troubleshooting Guide (Offline ComfyUI + Torch 2.9 + RTX 5090)

This list is built from actual problems I hit during testing, not screenshots of someone else’s install.  
If something breaks, it is almost always one of these.

---

## 1. ComfyUI launches with an xformers error
Expected under Torch 2.9.  
Xformers does not have a working wheel for this setup.  
FlashAttention and Triton replace it.

---

## 2. FlashAttention crashes or fails to load
You installed it before Triton.  
Uninstall FlashAttention and SageAttention.  
Reinstall in the correct order.

---

## 3. SageAttention missing kernels
Sage must be installed after FlashAttention and Triton.

---

## 4. ComfyUI-Manager missing
Install:
- gitdb  
- GitPython  

---

## 5. Templates not showing up
Portable 0.2.4 cannot use 0.7.x templates.  
Use the 0.2.4 template folder included in this repo.

---

## 6. TorchAudio fails to install
TorchAudio requires Torch and TorchVision to be installed first.

---

## 7. Wrong GPU is being used
Use the provided launcher scripts to force GPU visibility.

---

## 8. SDPA fallback warnings
Usually means Triton or FlashAttention is missing or mismatched.

---

## 9. Silent crashes on startup
This is almost always a mismatched wheel:
- Wrong CUDA  
- Wrong ABI  
- Wrong Python version  

---

## 10. Meta tensor / device mismatch errors
Something in your stack is built for Torch 2.8 or CUDA 12.1 instead of CUDA 12.8.

---

## 11. Extremely slow load times
ComfyUI is falling back to CPU.  
Verify GPU selection and wheel versions.

---

## 12. Everything installed but Comfy still broken
Re-check every wheel to make sure it is:
- cp312  
- cu128  
- built for Torch 2.9  
- installed in the correct sequence  
