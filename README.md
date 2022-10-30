# windows-on-arm-dev-kit
Notes from testing the Windows on ARM 2023 dev kit (aka Project Volterra)

Cliff notes before I forget:
 - It's cool!
 - Wait it's actually quite hot, TDP seems cranked all the way up (probably for the best)
 - 'Efficiency mode' does exactly what you'd expect, chucks a process to the efficiency cores
 - x86/x64 apps seem fine broadly, though definitely a bit sluggish e.g. lag on opening
 - I'd be miffed if I paid £1600 for an SQ3 Surface Pro 9 then ran x86 stuff all day, for a mac mini style £580 device who cares
 - First time using WSL2 instead of dual booting, it's neat!
 - No audio in WSL2
 - No (working) Arch for ARM WSL2 that I can find, hamstrung a little by Ubuntu 22.04's old/missing packages 
 - ARM native stuff in WSL2 runs waaaaay faster than x86 in windows, 3.3x speedup in one browser benchmark
 - Vivaldi, Discord, Steam, VSCode all run fine
 - Steam can't max out a gigabit connection, too much CPU load :D
 - Some games work fine, definitely slower than my steam deck.
 - e.g. Borderlands 3 works, slowly. CSGO, HL2, Astroneer, Halo MCC all fine except... 
 - GPU driver seems to be a bag of bolts, 2D fine but 3D can crash the whole system. No BSOD so hard to start debugging
 - No Vulkan or (I think) recent OpenGL. DirectX 9-12 only.
 - Easy anticheat (and I imagine lots of anticheat) has an architecture check and says no on ARM
 - MiniDP only if you want to see the UEFI but the only interesting bit there was boot order
 - USB Boot and PXE Boot supported, shenanigans?
 - Where do I even go for support on e.g. GPU drivers?
