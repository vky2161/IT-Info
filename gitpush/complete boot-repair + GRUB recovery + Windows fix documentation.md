
# UEFI Boot Recovery & GRUB Fix Guide (Ubuntu + Windows)

## 1. GRUB Command Line (When System Boots to GRUB)

If you see `grub>` prompt, use these steps:

### List disks and partitions

```
ls
```

Example output:

```
(hd0) (hd0,gpt1) (hd0,gpt2) ...
```

---

### Check partition contents

```
ls (hd0,gpt1)/
```

Look for:

- /boot
- /EFI
- /Windows
- /vmlinuz

Try other partitions if needed:

```
ls (hd0,gpt2)/ls (hd0,gpt3)/
```

---

### Load chainloader (Windows boot)

If Windows EFI is found:

```
insmod chain
```

Then:

```
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
```

---

### Set root partition (if needed)

```
set root=(hd0,gpt1)
```

---

### Start Windows boot

```
boot
```

---

## 2. After Booting into Windows (Fix Boot Permanently)

### Check firmware boot entries

```
bcdedit /enum firmware
```

### Detailed view

```
bcdedit /enum firmware /v
```

---

### Set Windows Boot Manager first

```
bcdedit /set {fwbootmgr} displayorder {bootmgr} /addfirst
```

---

### Optional: Remove Ubuntu entry

```
bcdedit /delete {GUID}
```

(Replace `{GUID}` with Ubuntu entry ID)

---

## 3. EFI Partition Cleanup (Optional)

### Mount EFI partition

```
mountvol S: /S
```

---

### View EFI contents

```
dir S:\EFI
```

Typical folders:

- Microsoft
- Boot
- ubuntu
- OEM (Dell/HP etc.)

---

### Remove Ubuntu boot files (if not needed)

```
rmdir /S /Q S:\EFI\ubuntu
```

---

### Unmount EFI partition

```
mountvol S: /D
```

⚠️ This does NOT delete data, only removes access.

---

## 4. Final Verification

- Restart system
- Ensure Windows boots directly
- No GRUB screen appears
- Ubuntu entry removed (if deleted)

---

## Summary Flow

### GRUB Fix (temporary boot)

- `ls`
- `ls (hd0,gptX)/`
- `insmod chain`
- `chainloader /EFI/Microsoft/Boot/bootmgfw.efi`
- `boot`

### Windows Fix (permanent)

- `bcdedit /enum firmware`
- `bcdedit /set {fwbootmgr} displayorder {bootmgr} /addfirst`
- Optional cleanup in EFI
