Windows Configuration
=============================

Turn off real time protection permenantlly with group policy (the regedit method doesn't work) [ref](https://techloris.com/how-to-disable-windows-defender/)
---------------------------------------
1. Win+R: `gpedit.msc`
2. Navigate with "Computer Configuration --> Administrator Templates --> Windows Components --> Windows Defender"
3. Double-click **Turn off Windows Defender** and select **Enabled**
4. In Command Prompt run: `gpupdate /force`
5. Reboot
6. **Not working**
