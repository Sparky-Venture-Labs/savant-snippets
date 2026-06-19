# Common Savant Issues & Fixes

## Host Not Responding / Blueprint Can't Connect

**Symptoms:** Blueprint shows host offline, app shows spinning wheel

**Steps:**
1. SSH into host: `ssh admin@[HOST_IP]`
2. Check services: `sudo launchctl list | grep savant`
3. Restart Savant service:
   ```bash
   sudo launchctl stop com.savant.racepoint.host
   sudo launchctl start com.savant.racepoint.host
   ```
4. If still offline, full reboot: `sudo reboot`

---

## Service Not Controlling Device

**Symptoms:** Button press does nothing, no feedback in Blueprint logs

**Steps:**
1. Check IP address of device hasn't changed — assign static IPs to all controlled devices
2. Verify port is correct and not blocked by firewall
3. Check Blueprint logs: **Tools → Log Viewer → Component**
4. Test raw connection: `telnet [DEVICE_IP] [PORT]`
5. Re-sync component in Blueprint

---

## Slow App Response

**Symptoms:** App takes 5–10 seconds to reflect state changes

**Steps:**
1. Check host CPU/RAM: `top -l 1 | head -20`
2. Check for large media libraries slowing metadata service
3. Reduce polling frequency on high-frequency state variables
4. Check network — host should be wired, not WiFi

---

## App Shows Wrong State

**Symptoms:** Light shows on in app but is actually off

**Steps:**
1. Force state refresh in Blueprint
2. Check feedback path — device must send feedback, not just accept commands
3. For toggle services, switch to discrete on/off if device supports it
4. Add manual state variable reset on scene trigger

---

## Blueprint Deploy Takes Forever

**Symptoms:** Deploy hangs at "Sending configuration"

**Steps:**
1. Check host disk space: `df -h`
2. Clear old backups: `sudo rm -rf /var/savant/backups/*`
3. Deploy to specific zones rather than full deploy
4. If hung for 10+ min, kill deploy, restart host, redeploy
