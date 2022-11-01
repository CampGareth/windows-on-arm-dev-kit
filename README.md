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
 - MiniDP only if you want to see the UEFI but the only interesting bit there was boot order and secure boot disable
 - USB Boot and PXE Boot supported, shenanigans?
 - Where do I even go for support on e.g. GPU drivers?

### Memory testing and USB booting
So my system crashes under GPU load and I wondered whether this could be memory related since the GPU shares system RAM. I tried the windows memory diagnostic utility but `mdsched` was missing from my system. I tried booting memtest86 which supports ARM, seems anything with a BOOTAA64.efi probably works. Memtest86 booted but then wanted me to press a button to start while not accepting any keyboard input. Not sure what was going on there. I tried Ubuntu Server 22.10 ARM from a USB drive and that didn't seem to be recognised as bootable. 

### Graphics related crashing
My list of working games is shrinking, Halo MCC started crashing on me. It seems 'new' graphics trigger this more quickly than old? Still I get no BSOD or event logs to debug so I don't know where to begin.

### Performance
I ran https://browserbench.org/Speedometer2.1/ across a few machines to give an idea of performance.
- Volterra, edge, windows, arm64 - 148rpm
- Volterra, vivaldi, windows, x86 - 33.2rpm
- Volterra, vivaldi, linux (wsl2), arm64 - 128rpm
- M1 MBP, firefox, macos, arm64 - 262rpm
- Surface go 2 (intel pentium 4425Y), vivaldi, linux, x86 - 44.9rpm
- i5 3570k desktop, chrome, windows, x86 - 122rpm
- MBP 16" 2019 (2.6Ghz 6 core i7), chrome, macos, x86 - 167rpm
- Pinebook pro (RK3399), vivaldi, linux, arm64 - 21.6rpm
- Steam deck, chrome, linux, x86 - 91.3rpm
