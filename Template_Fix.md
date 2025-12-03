Template Fix for ComfyUI Portable 0.2.4
This folder contains the working template package for ComfyUI Portable 0.2.4.
ComfyUI Portable cannot use the newer template package (0.7.x).  
It will fail silently or simply show no templates.
Replace the broken version in:
ComfyUI/python_embeded/Lib/site-packages
with the version in this folder.
After replacement, templates should appear normally.
