Required Wheel Install Order
This is the exact sequence that prevents DLL failures, fallback mode, SDPA issues, and kernel mismatches.
Install in this order:
1.	Torch
2.	TorchVision
3.	TorchAudio
4.	Triton
5.	Xformers (placeholder only)
6.	FlashAttention
7.	SageAttention
Failure to follow this order results in:
⦁	Triton not binding correctly
⦁	FlashAttention DLL errors
⦁	SageAttention missing kernels
⦁	SDPA fallback
⦁	Slow performance
⦁	Random crashes
⦁	Or ComfyUI not launching at all
This is the only sequence I have found that is repeatable.
