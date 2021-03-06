# Speed Ricer

Vanilla packages for ricing.

## What is this?

This repo provides scripts and metadata to build Linux packages for some open source programs that are not available in the defacto package repositories.  This allows for easy installation of packages. 

## What distros or package managers does it support?

At this time Ubuntu but if anyone cares to provide packages for other systems I'm happy to take pull requests.

## What packages are available?

Have a look at [this PPA](https://launchpad.net/~kgilmer/+archive/ubuntu/speed-ricer) to see the packages and distro versions available.

### What's a PPA?

It's short for Personal Package Archive and it's a facility provided by Canonical for anyone to host packages for Ubuntu.

## How can I get these packages?

The Ubuntu PPA must be added to your system, and then you can install a package.

Add PPA:
```
sudo add-apt-repository -y ppa:kgilmer/speed-ricer
```

Install a package:
```
sudo apt install polybar
```

### Examples

#### `i3-gaps`

```
sudo apt install i3-gaps
```

## A package I'd like isn't available, can it be added?

[File an issue](https://github.com/regolith-linux/speed-ricer/issues) describing the package and version you're looking for and we'll see what can be done.

## Contributions and Feedback

Yes please.

## Goals

* Support people that want to create their own desktop environments.
* Enable others to use this repo to publish to their own PPA or other repositories.
* Provide binary packages as close to vanilla upstream as possible. 

## How to Build and Publish a Package

Here's an example of how to build polybar and push it to your own PPA.

### Setup

See [this concise guide](https://wiki.debian.org/BuildingTutorial) to install the tools and get a familiar with the Debian packaging workflow.

### Get to Business

```
$ git clone https://github.com/regolith-linux/speed-ricer.git
...
$ cd speed-ricer
$ wget https://github.com/polybar/polybar/archive/3.1.0.tar.gz # Found in https://github.com/polybar/polybar/releases
$ mv 3.1.0.tar.gz polybar_3.1.0.orig.tar.gz
$ debuild -S
...
$ ls ..
LICENSE                                   polybar_3.1.0-1ubuntu1ppa1_source.buildinfo
polybar                                   polybar_3.1.0-1ubuntu1ppa1_source.changes
polybar_3.1.0-1ubuntu1ppa1.debian.tar.xz  polybar_3.1.0.orig.tar.gz
polybar_3.1.0-1ubuntu1ppa1.dsc            README.md
polybar_3.1.0-1ubuntu1ppa1_source.build
$ dput -f <YOUR PPA URI> ../polybar_3.1.0-1ubuntu1ppa1_source.changes
```