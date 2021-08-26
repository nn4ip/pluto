# Install with GLPK


## 0 Dependencies

On Ubuntu 18.04:

```
sudo apt install llvm-dev llvm-6.0-tools libclang-dev
sudo apt install texinfo texlive-full
sudo apt install cmake autoconf automake libtool libgmp3-dev bison flex
```


## 1 Link FileCheck

In fact, the FileCheck executable is "FileCheck-6.0" in /usr/bin.

```
mkdir -p ~/opt/FileCheck/bin
ln -s /usr/lib/llvm-6.0/bin/FileCheck ~/opt/FileCheck/bin/FileCheck
```

In ~/.bashrc:
```
export PATH="$HOME/opt/FileCheck/bin:$PATH"
```


## 2 Install GLPK

Official guide: https://www.gnu.org/software/glpk/

```
wget http://ftp.gnu.org/gnu/glpk/glpk-5.0.tar.gz
tar -xzf glpk-5.0.tar.gz
cd glpk-5.0
./configure --prefix=$HOME/opt/glpk
make -j32
make install
```

In ~/.bashrc:
```
export PATH="$HOME/opt/glpk/bin:$PATH"
```

## 3 Install Pluto

Official page: http://pluto-compiler.sourceforge.net/

Github doc: https://github.com/bondhugula/pluto/blob/master/doc/DOC.txt

`./configure` options: `./configure --help`

```
git clone https://github.com/nn4ip/pluto.git
cd pluto
git submodule init
git submodule update
./autogen.sh
./configure --prefix=$HOME/opt/pluto --enable-glpk --with-glpk-prefix=$HOME/opt/glpk
make -j32
make install
```

In ~/.bashrc:
```
export PATH="$HOME/opt/pluto/bin:$PATH"
```