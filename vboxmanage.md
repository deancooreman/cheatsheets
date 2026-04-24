# VBoxManage Cheatsheet

## 1. General & Information

| Command | Description |
|---------|-------------|
| `VBoxManage list vms` | List all registered virtual machines |
| `VBoxManage list runningvms` | List only currently running VMs |
| `VBoxManage list hdds` | List available virtual hard disk images |
| `VBoxManage showvminfo "VM Name"` | Display detailed information about a specific VM |
| `VBoxManage list hostinfo` | Show hardware/OS information of the host system |

---

## 2. VM Lifecycle Management

| Command | Description | Mode/Type |
|---------|-------------|-----------|
| `VBoxManage createvm --name "Name" --register` | Create and register a new VM | `config` |
| `VBoxManage startvm "Name" --type headless` | Start VM without a GUI window | `run` |
| `VBoxManage startvm "Name" --type gui` | Start VM with a graphical interface | `run` |
| `VBoxManage controlvm "Name" poweroff` | Immediate hard power off (pulling the plug) | `control` |
| `VBoxManage controlvm "Name" acpipowerbutton` | Send soft shutdown signal to Guest OS | `control` |
| `VBoxManage controlvm "Name" pause` | Suspend the execution of the VM | `control` |
| `VBoxManage unregistervm "Name" --delete` | Remove VM and delete all associated files | `delete` |

---

## 3. Hardware Configuration

| Command | Description |
|---------|-------------|
| `VBoxManage modifyvm "Name" --memory 4096` | Set RAM size (in MB) |
| `VBoxManage modifyvm "Name" --cpus 4` | Set number of virtual CPUs |
| `VBoxManage modifyvm "Name" --vram 128` | Set Video RAM size |
| `VBoxManage modifyvm "Name" --boot1 dvd` | Set first boot device (dvd, disk, net) |

---

## 4. Storage & Media

| Command | Description |
|---------|-------------|
| `VBoxManage storagectl "Name" --name "SATA" --add sata` | Add a SATA controller |
| `VBoxManage storageattach "Name" --storagectl "SATA" --port 0 --type hdd --medium file.vdi` | Attach a virtual hard disk |
| `VBoxManage storageattach "Name" --storagectl "SATA" --port 1 --type dvddrive --medium file.iso` | Mount an ISO image |
| `VBoxManage modifymedium disk "path.vdi" --resize 40960` | Resize a virtual disk (in MB) |

---

## 5. Networking

| Command | Description |
|---------|-------------|
| `VBoxManage modifyvm "Name" --nic1 nat` | Set first adapter to NAT mode |
| `VBoxManage modifyvm "Name" --nic1 bridged --bridgeadapter1 eth0` | Set to Bridged mode on specific host adapter |
| `VBoxManage controlvm "Name" natpf1 "ssh,tcp,,2222,,22"` | Configure Port Forwarding (Host 2222 -> Guest 22) |
| `VBoxManage controlvm "Name" natpf1 delete "ssh"` | Remove a Port Forwarding rule |

---

## 6. Snapshots

| Command | Description |
|---------|-------------|
| `VBoxManage snapshot "Name" take "Snap1"` | Create a new snapshot |
| `VBoxManage snapshot "Name" restore "Snap1"` | Revert to a specific snapshot |
| `VBoxManage snapshot "Name" list` | List all snapshots for the VM |
| `VBoxManage snapshot "Name" delete "Snap1"` | Delete a snapshot (merging data if needed) |

---

## 7. Guest Control

| Command | Description |
|---------|-------------|
| `VBoxManage guestcontrol "Name" run --username "u" -- /bin/ls` | Run a command inside the Guest OS |
| `VBoxManage guestcontrol "Name" copyto "/src" "/dst"` | Copy a file from Host to Guest |
