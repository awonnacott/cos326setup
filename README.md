# Setup for COS 326

We will use two functional programming languages in this course: OCaml and F#. 

## Installing OCaml

_OPAM is the package manager for OCaml. It is the recommended way to install the OCaml compiler and OCaml packages._ -OCaml installation instructions

Once Opam is installed, the same instructions work on all platforms.
But the installation of Opam will work differently on different operating systems.

### Windows
Because Windows does not have a Unix shell built in, we have to install one.
There are several ways to do this.
I will give instructions for using Cygwin (a third-party tool for installing Linux programs natively on Windows) and the Windows Subsystem for Linux (also called "Bash on Ubuntu on Windows"). 

### Windows: Cygwin Method

* Download the 64-bit graphical installer from [OCaml for Windows](https://fdopen.github.io/opam-repository-mingw/installation/).
* Step through the installer.
* It will open Cygwin setup.
  * Step through this.
  * Select a mirror (a website which hosts packages to install).
  I used [mirrors.kernel.org](mirrors.kernel.org).
  * If you want to use `emacs`, then when you get to the 'Select Packages' screen, select the 'Full' view and search for 'emacs'. Click on the `emacs` line where it says 'Skip' so it changes to a version number. Repeatedly click it - this will rotate between all the possible versions. Leave it with the highest version selected. Then hit Next.
  * It will take a while to download and install Cygwin.
* Then you will be back in the OCaml setup.
* In the future, you can use setup-x64_64.exe from [Cygwin Installation](https://cygwin.com/install.html) to update or install the packages in the Cygwin system.
* Open the Cygwin64 Terminal (instead of the Windows Command Prompt) to continue below.

### Mac OS
* If you do not have Homebrew installed (run `brew` in Terminal to see), [install Homebrew](https://brew.sh/).
* `brew instal opam ocaml`
* If you want to use `emacs` as your text editor, also `brew install emacs` because Mac OS X comes with an out-of-date version of emacs. 

### Linux
* Use your system package manager to install the `ocaml` and `opam` packages.

## Setting Up Ocaml

* `opam init`
* Say `y` to `Do you want opam to modify C:/OCaml64/home/kathe/.bash_profile? [N/y/f]`
* Say `y` to `A hook can be added to opam's init scripts to ensure that the shell remains in sync with the opam environment when they are loaded. Set that up? [y/N]`
* `eval $(opam env)`
* Now run `opam switch`.
  This will tell you you are using the system compiler.
* `opam install tuareg merlin user-setup ocamlbuild ocamlfind ocp-indent`
* Run `which ocaml` to check that the `ocaml` compiler is installed.
* Run `which ocamlfind` to check that `ocamlfind` is installed.
* Run `which ocamlbuild` to check that `ocamlbuild` is installed.
* Run `opam user-setup install` to configure `merlin` in `emacs` and `vim`.

## Setting up text editors for Ocaml

### Emacs

### Vim

### Sublime Text

### Atom

### Visual Studio Code
