# Install with GLPK

## 1 Install LLVM/Clang from source

Official guide:
- LLVM: https://llvm.org/docs/GettingStarted.html#id5
- Clang: https://clang.llvm.org/get_started.html

```
git clone https://github.com/llvm/llvm-project.git
cd llvm-project
mkdir build
cd build
cmake -G 'Unix Makefiles' -DLLVM_ENABLE_PROJECTS=clang -DCMAKE_INSTALL_PREFIX=$HOME/opt/llvm ../llvm
make -j8
make install
```

In ~/.bashrc:
```
export PATH="$HOME/opt/llvm/bin:$PATH"
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
./configure --prefix=$HOME/opt/pluto --enable-glpk --with-glpk-prefix=$HOME/opt/glpk --with-clang-prefix=$HOME/opt/llvm
make -j32
```