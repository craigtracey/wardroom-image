# wardroom-image
A tool for creating Kubernetes-ready images.

## Requirements
- [ansible](https://ansile.com)
- [packer](https://www.packer.io)
- [vagrant](https://vagrantup.com)

## Usage
First prepare your environment with ansible:
```
virtualenv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

To test image generation with Vagrant:
```
vagrant up $distro
```

Where `$distro` is one of:
- bionic
