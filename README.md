### Introduction

If you follow this readme you will be able to create a Windows VM from scratch from simple command lines.

This repo began with joefitzgerald templates (https://github.com/joefitzgerald/packer-windows) and box-cutter (https://github.com/box-cutter/windows-vm)

### Requirements

[Packer](https://github.com/mitchellh/packer/blob/master/CHANGELOG.md) `0.5.1` or greater is required.

[VirtualBox](https://www.virtualbox.org/wiki/Downloads) `4.3.12` or greater is required

[Vagrant](http://www.vagrantup.com/downloads.html) `1.6.3` or greater is required

### Version Status

* Machines supported: Windows 7 Pro x64.
* Platform: VirtualBox

### Information about Microsoft installer

`win7x64-pro.json` will install a trial Windows 7 Pro version from Microsoft. Build time: depends on Microsoft download rate
`win7x64-pro-local-iso.json` will install my licensed Windows using my ISO's local path.

If you have you own ISO you can, instead changing win7x64-pro-local-iso.json, simply run:

```bash
packer build -var 'iso=<path_to_your_iso>' -var 'checksum=<checksum-value>' windows7_virtuabox.json
```

### Product Keys 

If you wanna add your own product keys to Windows:

* Uncomment the `<Key>...</Key>` element
* Insert your product key into the `Key` element


### Building a VM with packer

```bash
packer windows7_virtuabox.json
```

After you run this command it will create a .box file inside folder. If you want, later you can delete it but I suggest you keep it. It will be useful if you want to build a Windows for another project

Run Vagrant:

```bash
vagrant up
```

Now your machine is ready. Now to run sus converter scripts type:

```bash
vagrant ssh
```

And your are done!

PS: You can also RDP to this Windows by using `vagrant rdp`.
