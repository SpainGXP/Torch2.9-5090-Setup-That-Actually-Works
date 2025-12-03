# Additional Notes

This repo was built out of necessity.  
After about twenty failed installations, I realized the only way to avoid dependency hell was to go fully offline, lock every wheel version, and treat the portable Python environment as a sealed biosphere.

This method is not theoretical.  
It works repeatedly, and every step here is grounded in practical trial and error.

If updates to Torch, Triton, FlashAttention, or SageAttention change the stack, I will update the repo.  
Pull requests are welcome if you find improvements or additional GPU configs that work under Torch 2.9 and CUDA 12.8.
