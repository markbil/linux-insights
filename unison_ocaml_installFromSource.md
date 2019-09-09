# Install Unison version 2.51.2 (ocaml 4.08.1) on Ubuntu/Debian

## Background
For Unison to work properly, both client and server must not only have the same Unison version installed, but that version also needs to be compiled with the same version of OCaml on both ends. The Ubuntu package manager currently only delivers _Unison 2.48.4_, and _OCaml 4.05.0_. This can be a problem when synchronising between two different distros, as one distro is likely to run a different version of Unison than the other, or Unison is compiled with a different versions of OCaml. Arch Linux' packet manager pacman for example delivers already the newest _unison version 2.51.2 (ocaml 4.08.1)_.

The following commands install Unison 2.51.2 on Ubuntu/Debian using the latest OCaml version 4.08.1.


## Remove any existing OCaml version


    $ sudo apt purge ocaml
    $ sudo rm -r /usr/bin/ocaml*

## Remove any existing Unison version

    $ sudo apt purge unison
    $ sudo rm -r /usr/bin/unison
    $ sudo rm -r /usr/bin/unison-*

## Install OCaml from source

    $ sudo mkdir -p /usr/src/ocaml
    $ cd /usr/src/ocaml
    $ sudo wget https://caml.inria.fr/pub/distrib/ocaml-4.08/ocaml-4.08.1.tar.gz
    $ sudo tar xzvf ocaml-4.08.1.tar.gz --strip-components 1
    $ sudo ./configure
    $ sudo make world.opt
    $ sudo make install
    $ sudo make clean

check if new OCaml version was installed

    $ ocaml -version

 should return ```The OCaml toplevel, version 4.08.1```

## Install Unison from source

    $ cd /usr/src/
    $ sudo git clone https://github.com/bcpierce00/unison.git
    $ cd /usr/src/unison
    $ sudo make UISTYLE=text

check if new Unison version was installed

    $ unison -version

should return ```unison version 2.51.2 (ocaml 4.08.1)```


## Links
- select link to source code of latest OCaml version: https://ocaml.org/releases/
- git repository for unison: https://github.com/bcpierce00/unison/

## References:
- https://github.com/ocaml/ocaml/blob/trunk/INSTALL.adoc
- https://gist.github.com/dasginganinja/1e958f8db5606974b6b8f65562343770
- https://wiki.archlinux.org/index.php/Unison

