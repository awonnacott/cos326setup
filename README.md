# Setup for COS 326

We will use two functional programming languages in this course: OCaml and F#. 

## Installing OCaml

_OPAM is the package manager for OCaml. It is the recommended way to install the OCaml compiler and OCaml packages._ -OCaml installation instructions

Once Opam is installed, the same instructions work on all platforms.
But the installation of Opam will work differently on different operating systems.

### Mac OS
* If you do not have Homebrew installed (run `brew` in Terminal to see), [install Homebrew](https://brew.sh/).
* `brew install opam ocaml`
* If you want to use `emacs` as your text editor, also `brew install emacs` because Mac OS X comes with an out-of-date version of emacs. 

### Linux
* Use your system package manager to install the `ocaml` and `opam` packages.

### Windows
Because Windows does not have a Unix shell built in, we have to install one.
There are several methods for doing this, including:

* with Microsoft's Windows Subsystem for Linux (also called "Bash on Ubuntu on Windows")
* with Cygwin (a third-party tool for installing Linux programs natively on Windows)
* with a remote SSH connection to the `cycles.cs.princeton.edu` Linux computers, which already have OCaml installed
* with OCPWin (a self-contained OCaml installer using the native Windows command prompt)
* with a virtual machine installation of Linux, using [VirtualBox](https://www.virtualbox.org/)
* with a physical installation of Linux as a second operating system, so you chose which operating system to load when you start up your computer

I recommend you try these methods in the order presented above. I will provide instructions for the first three.

### Windows: WSL Method (recommended)
The Windows Subsystem for Linux (also called "Bash on Ubuntu on Windows") is Microsoft's compatibility layer to run Linux programs within Windows.

* Open PowerShell as an administrator (right click; Run as Administrator) and run `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`
* Restart when requested
* Install the Ubuntu app from the [Get Ubuntu](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6) page on the Microsoft Store.
* Open the Ubuntu app and set your username and password. Note the username cannot have spaces, and the password won't show while you're typing it.
* Once you have opened the Ubuntu app once, we will remove the Windows Subsystem for Linux from the Windows Defender Real-time Protection, which is necessary or else all programs in the Ubuntu shell will run very slowly:
  * Download `excludeWSL.ps1` [this GitHub link](https://gist.github.com/noelbundick/9c804a710eb76e1d6a234b14abf42a52) using the 'Download Zip' button and then copy `excludeWSL.ps1` out of the zip into your Downloads folder.
  * Then open PowerShell as an administrator again and run the following commands:
  * `cd C:\Users`
  * `ls` to see what your username is (the subfolder not named 'Public' will be your username)
  * `cd .\username\Downloads`
  * `.\excludeWSL.ps1`
  * Type `r` for `Run once` and the script will add a bunch of exclusions to the Windows Defender paths.
  * Close PowerShell and reopen the Ubuntu app.
* Install [Xming](https://sourceforge.net/projects/xming/) if you want graphics support for `emacs`.
  * If you do, add `export DISPLAY=:0` to your `~/.bashrc` (open `~/.bashrc` from the Ubuntu terminal with your preferred text editor) so that Linux programs can connect to the Xming display server while it is running.
* Run the following commands in the Ubuntu app:
  * `sudo apt update`
  * `sudo apt dist-upgrade -y` (This takes a while.)
  * `sudo apt install -y opam ocaml emacs vim m4` (This takes a while too.)
* Using the Ubuntu app (not the Windows Command Prompt) go to Setting Up OCaml below.

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
* Open the Cygwin64 Terminal (instead of the Windows Command Prompt) and go to Setting Up OCaml below.

### Windows: SSH Method
This is essentially the approach you would have used in COS 217, except that you will connect to `cycles.cs.princeton.edu` instead of `courselab.cs.princeton.edu`.
I am assuming you had issues setting up both WSL and Cygwin, and so these instructions will not use either of those programs.

* Set up your [CS department account](https://csguide.cs.princeton.edu/accounts/new), if you have not done this.
* Install [MobaXterm](https://mobaxterm.mobatek.net/) Home Edition (free edition)
* Select Session -> SSH
* Connect to `cycles.cs.princeton.edu`

## Setting Up Ocaml
Run the following commands in the Unix terminal (Terminal.app on Mac OS, Ubuntu app or Cygwin Terminal on Windows):

* `opam --version`. Note whether you are on `opam < 2.0` or `opam >= 2.0`.
* `opam init`
* Say `y` to `Do you want opam to modify C:/OCaml64/home/kathe/.bash_profile? [N/y/f]`
* Say `y` to `A hook can be added to opam's init scripts to ensure that the shell remains in sync with the opam environment when they are loaded. Set that up? [y/N]`
* `eval $(opam env)` (if you have `opam < 2.0`, such as `1.2.2`, then run `eval $(opam config env)` instead).
* Now run `opam switch`.
  This will tell you you are using the system compiler.
* `opam install tuareg merlin user-setup ocamlbuild ocamlfind ocp-indent`
* Run `which ocaml` to check that the `ocaml` compiler is installed.
* Run `which ocamlfind` to check that `ocamlfind` is installed.
* Run `which ocamlbuild` to check that `ocamlbuild` is installed.
* Run `opam user-setup install` to configure `merlin` in `emacs` and `vim`.

## Setting up F#

### Mac OS
Follow Option 1 or Option 2 from [Use F# on Mac OSX](https://fsharp.org/use/mac/).

### Linux
Follow the instructions for your distribution at [Use F# on Linux](https://fsharp.org/use/linux/).

### Windows
Follow Option 1 or Option 2 at [Use F# on Windows](https://fsharp.org/use/windows/).

## Setting up text editors for Ocaml and F#

### Emacs
For OCaml, the copy of `emacs` you run from the same terminal as `opam` is available should have Merlin set up automatically by `opam user-setup install` above.

For F#, install `fsharp-mode` from MELPA.

Mac OS users: we recommend you use `brew` to update `emacs` as described above.

### Vim
For OCaml, the copy of `vim` you run from the same terminal as `opam` is available should have Merlin set up automatically by `opam user-setup install` above. You can also install [`rgrinberg/vim-ocaml`](https://github.com/rgrinberg/vim-ocaml) for some additional features.

For F#, use [`fsharp/vim-fsharp`](https://github.com/fsharp/vim-fsharp).

### Sublime Text

### Atom

### Visual Studio Code
