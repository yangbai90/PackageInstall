# Installation of vim

## Step-1 Download
The download of vim can be done via:
```
git clone https://github.com/vim/vim.git
```
or go to the release page of [vim](https://github.com/vim/vim/tags)

## Step-2 Configure
The configuration for vim can be done via:
```
./configure --with-features=huge \
--enable-multibyte \
--enable-rubyinterp=yes \
--enable-python3interp=yes \
--with-python3-config-dir=$(python3-config --configdir) \
--enable-perlinterp=yes \
--enable-luainterp=yes \
--enable-gui=gtk2 \
--enable-cscope \
--prefix=/home/by/Programs/vim
```
then you can do:
```
make -j4 && make install
```

## Step-3 install plugin manager
You can choose whatever(vundle, bundle,etc.) you like, here I'll use [vim-plug](https://github.com/junegunn/vim-plug)

### Download vim-plug
```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
then you can open you vim by running:
```
vim
```
from your terminal.

### Install plugins
Since now, the `vim-plug` is ready, you can do:
```
PlugInstall
```
to install all the plugins you required in your ~/.vimrc file.

## Step-4 configure coc.nvim

### Generate the config file for coc
```
:CocConfig
```
in your `coc-settings.json`, write down the following lines:
```
{
  "languageserver": {
    "fortran": {
    "command": "fortls",
    "filetypes": ["fortran"],
    "rootPatterns": [".fortls", ".git/"]
  }
  }
}
```

For other plugins in coc(if they offer the support for the languages you are using), you can do the install via:
```
CocInstall coc-plugin
```

In my case, I plan to use c++/cmake/python/julia, then I will do:
```
:CocInstall coc-json coc-css
:CocInstall coc-sh
:CocInstall coc-clangd
:CocInstall coc-cmake
:CocInstall coc-julia
:CocInstall coc-pyright
```

Afterwards, enjoy your vim coding :)
