# packer-esxi

A set of example [Packer][] templates for building Debian and Ubuntu boxes on
[VMware ESXi][]. These are built on the remote ESXi host, then shutdown and
left registered. A lot of this work comes out of [boxes][], which provides the
basic template formation.

They assume that it's possible to fetch an IP through DHCP on the primary (`VM
Network`) network. If this isn't the case, you can adjust the [boot command to
set a static IP][].

This example repo comes out of [this post I wrote on how to use Packer with
VMware ESXi][post].

## Usage

```sh
packer build -var-file variables.json ubuntu-1604-base.json
```

Ensure that `variables.json` contains valid values.

## Testing Boxes

A Vagrantfile was borrowed from https://github.com/geerlingguy/packer-debian-9 and a the `.json` and `preseed` stuff for enabling debian 9.  To boot into a box and dig around on the local machine, just run:

```
$ vagrant up
$ vagrant ssh
# (NOTE:  I'm still making this work...)
```

## Original Author

Copyright (c) 2016 Nick Charlton. MIT Licensed.

[Packer]: https://packer.io
[VMware ESXi]: http://www.vmware.com/products/vsphere-hypervisor.html
[boxes]: https://github.com/nickcharlton/boxes
[boot command to set a static IP]: https://help.ubuntu.com/lts/installation-guide/armhf/apbs02.html
[post]: https://nickcharlton.net/posts/using-packer-esxi-6.html
