# Vim Dev Config

Este repositorio contiene una configuración de **Vim orientada a desarrollo**, con un enfoque minimalista y sin alterar los colores del terminal.  
Incluye autocompletado, LSP, navegación rápida, herramientas de productividad y mejoras ergonómicas.

---

## 📦 Plugins utilizados (vim-plug)

La configuración utiliza **vim-plug** como gestor de plugins.  
Para instalarlo:

```sh
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

# Plugins incluidos

## Navegación y búsqueda

junegunn/fzf

junegunn/fzf.vim

preservim/nerdtree

---

## LSP, autocompletado e inteligencia

neoclide/coc.nvim (branch release)

---

## Linting y formato

dense-analysis/ale

editorconfig/editorconfig-vim

---

## Productividad

tpope/vim-commentary

tpope/vim-surround

tpope/vim-repeat

jiangmiao/auto-pairs

mattn/emmet-vim

---

## Estructura del código

preservim/tagbar

---

## Git

tpope/vim-fugitive

airblade/vim-gitgutter

---

## Sintaxis y soporte de lenguajes

sheerun/vim-polyglot
