### Introduction

If you follow this readme you will be able to create a Windows VM from scratch from simple command lines.

This repo began with joefitzgerald templates (https://github.com/joefitzgerald/packer-windows) and box-cutter (https://github.com/box-cutter/windows-vm)

### Requirements

[Packer](https://github.com/mitchellh/packer/blob/master/CHANGELOG.md) `0.5.1` or greater is required.

[VirtualBox](https://www.virtualbox.org/wiki/Downloads) `4.3.12` or greater is required

[Vagrant](http://www.vagrantup.com/downloads.html) `1.6.3` or greater is required

For vagrant you need a plugin. To install it run':

```bash
vagrant plugin install winrm
```

### Building Windows trial machine from Microsoft

Clone the repository and run:

```bash
packer build win7x64-pro.json
```

After you run this command it will create a .box file inside folder.

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


### Building Windows from ISO


Clone the repository and run

```bash
packer build -var 'iso=<path_to_your_iso>' -var 'checksum=<checksum-value>' win7x64-pro-local-iso.json
```

After you run this command it will create a .box file inside folder.

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


### Version Status

* Machines supported: Windows 7 Pro x64.
* Platform: VirtualBox

### Information about Microsoft installer

`win7x64-pro.json` will install a trial Windows 7 Pro version from Microsoft. Build time: depends on Microsoft download rate

`win7x64-pro-local-iso.json` will install my your Windows using an ISO.

If you have you own ISO you can, instead changing win7x64-pro-local-iso.json, simply run:



### Product Keys 

In `Autounattend.xml`, if you wanna add your own product keys to Windows:

* Uncomment the `<Key>...</Key>` element
* Insert your product key into the `Key` element
