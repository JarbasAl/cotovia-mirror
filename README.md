Mirror from sourceforge https://sourceforge.net/p/cotovia/code/ci/master/tree/

## Requirements
```
* Requirements (Debian package name given in brackets)
  - GCC               (gcc, g++)
  - GNU Bison         (bison)
  - GNU Flex          (flex)
  - Alsa audio        (libasound2, libasound2-dev)
  - Expat             (libexpat1, libexpat1-dev)
  - help2man          (help2man)
  - devscripts package and its dependencies in order to build Debian packages  (devscripts)
```


## Getting Cotovia from Git repository

```bash
~/compartido$ mkdir COTOVIA
~/compartido$ cd COTOVIA/
~/compartido/COTOVIA$ git clone ssh://gtmsf@git.code.sf.net/p/cotovia/code cotovia-code

Cloning into cotovia-code...
remote: Counting objects: 347, done.
remote: Compressing objects: 100% (277/277), done.
remote: Total 347 (delta 71), reused 324 (delta 61)
Receiving objects: 100% (347/347), 148.90 MiB | 1.74 MiB/s, done.
Resolving deltas: 100% (71/71), done.
```

## Building Cotovia

```bash
~/compartido/COTOVIA$ cd cotovia-code/
~/compartido/COTOVIA/cotovia-code$ ls

data  src

~/compartido/COTOVIA/cotovia-code$ cd src

~/compartido/COTOVIA/cotovia-code/src$ ls

AUTHORS.txt  COPYRIGHT_and_LICENSE.txt  cotovia  debian  Makefile  proyectos  README

~/compartido/COTOVIA/cotovia-code/src$ make

~/compartido/COTOVIA/cotovia-code/src$ ls ../bin64

cotovia  cotovia-ecess-m1
```


## Running Cotovia



The main binary is cotovia. At this time the input to Cotovia must be in ISO format, therefore format conversion is needed for reading UTF8 files. For instance:

```bash
~/compartido/COTOVIA/cotovia-code/src$ echo "Este é un exemplo." | iconv -c -f UTF-8 -t ISO-8859-1 | ../bin64/cotovia -s -V iago -l gl

~/compartido/COTOVIA/cotovia-code/src$ ../bin64/cotovia -i iso_file.txt -s -V iago -l gl
```

You should add cotovia to your PATH variable. 
When you run cotovia with no or wrong options, some help information appears on the screen with some simple examples at the end. 


## Building Cotovia Debian packages

```bash
~/compartido/COTOVIA/cotovia-code/src$ make debian-packages

~/compartido/COTOVIA/cotovia-code/src$ ls ../.

~/compartido/COTOVIA/cotovia-code/src$ ls  ../*.deb

../cotovia_0.5_amd64.deb  ../cotovia-ecess-m1_0.5_amd64.deb

~/compartido/COTOVIA/cotovia-code/src$ ~/compartido/COTOVIA/cotovia-code/src$ ls ../data/*.deb

../data/cotovia-lang-es_0.5_all.deb  ../data/cotovia-voice-iago_0.5_all.deb
../data/cotovia-lang-gl_0.5_all.deb
```

In order to run Cotovia, you will need to install the following packages:

```
../cotovia_0.5_amd64.deb   ---  Cotovia executable
../data/cotovia-lang-gl_0.5_all.deb --- Galician linguistic data
../data/cotovia-lang-es_0.5_all.deb --- Spanish linguistic data
../data/cotovia-voice-iago_0.5_all.deb --- Iago's voice files.
```



