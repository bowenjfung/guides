# Setting up parallel port communication via PsychoPy
This setup is for PsychoPy version 1.90.2 running on Windows 10 (64 bit)

- Download the [inpout32 binaires](http://www.highrez.co.uk/scripts/download.asp?package=InpOutBinaries)
- Install using the .exe in the \Win32 folder (run as admin)[^not sure that this step is necessary]
- Move inpout32.dll to C:\Windows\SysWOW64

Moving the driver to the SysWOW64 folder should be sufficient for the parallel module to find it. Best practice is to keep a copy of inpout32.dll in your working directory (in case it disappears from the internet).

Below is minimal code to send a 0.5 sec pulse to pin 1 (check device manager for LPT port address)

```
from psychopy import core, parallel

parallel.setPortAddress(0xE050)
parallel.setData(1)
core.wait(0.5)
parallel.setData(0)
```

## Some notes from testing
Despite the apparent simplicity, I had quite a bit of difficulty getting this set up. I believe the problems related mainly to how the different versions (32 vs 64 bit) of each platform (Windows, Python, PsychoPy) read the parallel port drivers (e.g. inpout32). Ultimately, because the standalone version of PsychoPy operates under 32 bit python, the above method is the simplest, but will preclude testing on other (read 64 bit) platforms. 
