+++
title = "Power User Setup for Unix-based Operating Systems"
date = 2020-02-17
+++

A lot of people have asked me about my setup.

Here it is (taken from my [dots](https://github.com/oniani/dots) repo):


## Setup

- Addressbook: [Abook](http://abook.sourceforge.net/)
- Colorscheme Generator: [pywal](https://github.com/dylanaraps/pywal)
- Default Colorscheme: [Gruvbox Dark Hard](https://github.com/morhetz/gruvbox)
- Document Viewer: [Preview](<https://en.wikipedia.org/wiki/Preview_(macOS)>) / [Zathura](https://github.com/zegervdv/homebrew-zathura)
- Editor: [Neovim](https://neovim.io/)
- Email: [neomutt](https://neomutt.org/) (with [isync](http://isync.sourceforge.net/) for mailbox synchronization and [msmtp](https://marlam.de/msmtp/) for sending emails)
- File Format Handler: [pandoc](https://pandoc.org/)
- File Manager: [Vifm](https://vifm.info/)
- Font: [Hack Regular Nerd Font Complete](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/Hack/Regular/complete/Hack%20Regular%20Nerd%20Font%20Complete.ttf)
- Fuzzy Finder: [fzf](https://github.com/junegunn/fzf)
- Image Viewer: [Preview](<https://en.wikipedia.org/wiki/Preview_(macOS)>) / [sxiv](https://github.com/muennich/sxiv)
- Music Player: [ncmpcpp](https://rybczak.net/ncmpcpp/) (with [mpd](https://www.musicpd.org/) as a backend)
- Package Manager: [Homebrew](https://brew.sh/)
- Password Manager: [Pass](https://www.passwordstore.org/)
- RSS Reader: [Newsboat](https://newsboat.org/)
- Shell: [Z Shell](http://zsh.sourceforge.net/)
- Terminal Emulator: [kitty](https://sw.kovidgoyal.net/kitty/)
- Version Control: [Git](https://git-scm.com/downloads)
- Video Player: [mpv](https://mpv.io/)
- Wallpaper: [wallpaper47.jpg](https://github.com/oniani/wallpapers/blob/master/wallpapers/wallpaper47.jpg)
- Web Browser: [Firefox](https://www.mozilla.org/en-US/firefox/)
- Window Manager: [Amethyst](https://github.com/ianyh/Amethyst) / [bspwm](https://github.com/baskerville/bspwm)

Code Formatting

- CSS/HTML/JavaScript/Markdown: [Prettier](https://prettier.io/)
- Python: [Black](https://black.readthedocs.io/en/stable/)
- R: [styler](https://github.com/r-lib/styler)
- Rust: [rustfmt](https://github.com/rust-lang/rustfmt)

Code Linting

- Haskell: [hlint](http://hackage.haskell.org/package/hlint)
- JavaScript: [eslint](https://eslint.org/)
- Markdown: [mdl](https://github.com/DavidAnson/markdownlint)
- Python: [pylint](https://www.pylint.org/) and [mypy](http://mypy-lang.org/)
- R: [lintr](https://github.com/jimhester/lintr)
- Rust: [Clippy](https://rust-lang.github.io/rust-clippy/)
- Shell: [ShellCheck](https://www.shellcheck.net/)

### Z Shell

#### Plugins

No plugin manager is used. Plugins are sourced at the end of `.zshrc`.

- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

### Neovim

#### Plugins

Plugins are installed and managed using a minimalist plugin manager
[vim-plug](https://github.com/junegunn/vim-plug).

- [Base16 Vim](https://github.com/chriskempson/base16-vim/)
- [fzf.vim](https://github.com/junegunn/fzf.vim)
- [fzf](https://github.com/junegunn/fzf)
- [vim-commentary](https://github.com/tpope/vim-commentary)
- [completion-nvim](https://github.com/haorenW1025/completion-nvim)
- [diagnostic-nvim](https://github.com/haorenW1025/diagnostic-nvim)
- [nvim-lsp](https://github.com/neovim/nvim-lsp)
- [goyo.vim](https://github.com/junegunn/goyo.vim)
