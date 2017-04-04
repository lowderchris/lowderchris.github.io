---
title:  "Setting up macOS for a bit of science"
categories:
  - workflows
tags:
  - macOS
---
After having re-installed and moved computing machines so many times, I’ve almost got the hang of re-installing applications and bits of code. To make this a bit simpler, and to share this information for anyone else who might be interested, I’ve compiled this into a guide. This guide will end up changing and evolving with time, a sort of living document.

## LaTeX

[MacTeX](https://www.tug.org/mactex/) and [TeXShop](http://pages.uoregon.edu/koch/texshop/) are my absolutely favorites. Trust me. MacTeX also includes the wonderfully useful tool, LaTeXiT. By entering a snippet of LaTeX math code into the prompt, a drag-and-droppable PDF or image is created. This is especially useful with dropping equations into Keynote. Did I mention Keynote. You should give Keynote a run for presentations. Again, trust me.

## Xcode

Having the Xcode suite, while not fully required, is the easiest way to get started with these install pre-requisites. While the majority of software only requires the Xcode command line tools, having the full suite would ensure full compatibility down the road.

Xcode itself can be installed via the macOS app store, or alternatively from their [developer website](https://developer.apple.com/downloads). Afterwards, the command line tools can be installed via,

	xcode-select --install

This will install the required command line tools for the rest of this installation process… as well as fueling the dream of one day having time to try my hand at creating a simple iOS app…

## Homebrew

### Installation

[Homebrew](http://brew.sh) is a package manager for macOS, allowing the installation of some core software packages that aren’t bundled with macOS. Installation is a breeze,

	/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

So easy. *cough*MacPorts*cough*

### Usage

As a simple test of this installation, we can install the package `htop`. This is a straightforward terminal view of system resources.

	brew install htop

Down the road, packages can be upgraded to newer versions published by authors. This can be achieved by commanding homebrew to check for updates, find outdated packages, and then undergo the upgrading process,

	brew update
	brew outdated
	brew upgrade

### Install a few packages

`wget` is a great tool for grabbing content from a web URL. `curl` is an alternative pre-loaded on macOS, but I can never recall the syntax.

	brew install wget

I’m a fan of the VIM text editor, so I’ll install that as well,

	brew install macvim

## Python

### Core

[Python](https://www.python.org) is the language of choice for many researchers, and is actively developed and maintained. Best of all, the open-source community has adopted this for many open science analysis packages. Even better, there’s no license manager to deal with!

An earlier version of python comes bundled with macOS, but we can do a bit better. Depending on your needs as a researcher, there are two major versions to consider. 2.7.11 is the last stable version of the 2.x versions of python. Many older repositories of code rely on syntax and packages in this version. With the introduction of python 3.x, changes were made to clean-up and modernize the language. As you might imagine, this left a few older code packages broken.

You can choose either version for use, but I’d recommend starting with python 3.x for modernity. The older version of python installed with macOS will remain for use with legacy code.

Many folks will recommend installing a version of python bundled with other python packages geared at scientific analysis. I enjoy having a bit more control over which packages are installed, and how I go about updating these. I’ve also never met a software wizard I trust. How easy is it to install python with homebrew?

	brew install python3

Done. Almost like magic.

The next step will take a moment longer to install, depending on the system being installed to. GCC is a software compiler bundle, which we’ll need to install a few other packages down the road, notably some FORTRAN routines. So I’d recommend running the following command, and running out to grab a coffee. Your CPU will be engaged for a short while.

	brew install gcc

### Science packages

There are a number of additional packages that make scientific analysis and presentation much easier on the python platform. For that, we’ll need the `pip3` or `pip` tool, depending on which version of python was installed.

[NumPy](http://www.numpy.org) allows for more advanced array handling within python.

	pip3 install numpy

[SciPy](https://www.scipy.org) contains a variety of mathematics, science, and engineering packages for signal analysis, processing, etc.

	pip3 install scipy

[Matplotlib](http://matplotlib.org) provides a beautiful set of data visualization tools for use within python. Syntax and appearance mimics that in Matlab, which can make the transition a bit easier for some folks seeing the light. A [gallery](http://matplotlib.org/gallery.html) has more examples than you have time to explore.

	pip3 install matplotlib

[iPython](http://ipython.org) is an interactive command line interface for python, again making it more akin to a Matlab-like-environment.

	pip3 install ipython

A few other packages will enable some astronomy libraries, as well as tools for dealing with reading large databases. Many packages will eventually call for these as pre-requisites, so I’d go ahead and install these now.

	pip3 install astropy
	pip3 install pyfits
	pip3 install pandas
	pip3 install suds

Last, but certainly not least, we can install the [SunPy](http://sunpy.org) package, which aims to replace many of the standard solar software routines. In particular, providing a free and open replacement for the SolarSoft packages is of key interest. While SolarSoft itself is a great resource, the reliance on IDL licensing is less than ideal.

	pip3 install sunpy

And with that, you now have a fully functional solar physics battlestation.

## Other tools

[Pandoc](http://pandoc.org) is a fantastic tool for the automated conversion between a number of language types, from Markdown, LaTeX, HTML, ePub, etc. This is a great tool for writing notes up in one language, Markdown, for instance, and then enables the easy conversion into a number of other document types.

	brew install pandoc

[Jekyll](https://jekyllrb.com) is a great tool for building a responsive, static website from content files. In my case, I use this to generate blog files and serve these up to GitHub for rendering. This is easily installed with the already installed Homebrew.

	brew install ruby

Then, in a new terminal session (to allow paths to update),

	gem install jekyll