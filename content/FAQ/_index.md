+++
title = 'FAQ'
date = 2023-11-15T19:38:39-07:00
draft = false
weight = 5
+++

## Frequently Asked Questions

**Can Tinkerbell be used to install OSes without Internet access (where both the Stack and Worker are in an isolated network)?**
: Yes, OS images, action Images, and all container Images in the stack can served inside air-gapped environments. See here for air-gapped considerations.

**What operating systems is Tinkerbell able to install?**
: Any! Out of the box, we are working to provide installation workflows for deb and rpm-based systems, but it can be used for anything (as it includes a generic workflow engine).

**Which hardware makes and models are supported in Tinkerbell?"**
: Tinkerbell currently works on many different vendors. Dell, HP, Supermicro, Lenovo, and many more. If you find a vendor that is not supported or want us to add additional vendors to our list, let us know!

**Is Tinkerbell able to operate remote server power settings (power on; power off)? How about resetting?**
: Yes, via the [PBnJ](/docs/services/Pbnj) or [Rufio](/docs/services/Rufio).

**Does Tinkerbell use each operating system's native network installer program, or does it install using a different method?**
: It depends on the operating system, the installation environment supports non-NM and NM for rpm-based systems, and the standard deb-based network interfaces.
