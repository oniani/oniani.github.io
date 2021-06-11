+++
title = "Power User Setup for Unix-based Operating Systems"
date = 2020-02-17

[extra]
toc = true
+++

A lot of people have asked me about my setup.

Here it is (taken from my [dots](https://github.com/oniani/dots) repo):

## Organization

The setup is compliant with the [XDG Base Directory
Specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html).

## Setup

- Addressbook: [Abook](http://abook.sourceforge.net/)
- Colorscheme Generator: [pywal](https://github.com/dylanaraps/pywal)
- Default Colorscheme: [moonfly](https://github.com/bluz71/vim-moonfly-colors)
- Document Viewer: [Preview](https://support.apple.com/guide/preview/welcome/mac) / [Zathura](https://github.com/zegervdv/homebrew-zathura)
- Editor: [Neovim](https://neovim.io/)
- File Format Handler: [pandoc](https://pandoc.org/)
- File Manager: [nnn](https://github.com/jarun/nnn)
- Font: [Iosevka Term Nerd Font Complete Mono](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Iosevka)
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
- Web Browser: [Brave](https://brave.com/)
- Window Manager: [Amethyst](https://github.com/ianyh/Amethyst) / [bspwm](https://github.com/baskerville/bspwm)

Code Formatting

- CSS/HTML/JavaScript/Markdown: [Prettier](https://prettier.io/)
- Python: [Black](https://black.readthedocs.io/en/stable/)

Code Linting

- Haskell: [hlint](http://hackage.haskell.org/package/hlint)
- JavaScript: [eslint](https://eslint.org/)
- Markdown: [mdl](https://github.com/DavidAnson/markdownlint)
- Python: [pyright](https://github.com/Microsoft/pyright)
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

- [coc.nvim](https://github.com/neoclide/coc.nvim)
- [fzf](https://github.com/junegunn/fzf)
- [fzf.vim](https://github.com/junegunn/fzf.vim)
- [lightline.vim](https://github.com/itchyny/lightline.vim)
- [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
- [vim-commentary](https://github.com/tpope/vim-commentary)
- [vim-fugitive](https://github.com/tpope/vim-fugitive)
- [vim-gruvbox8](https://github.com/lifepillar/vim-gruvbox8)

#### Current Stats

Plugins arranged according to their startup time.

| TOP | Time (ms) | Plugin            |
| --- | --------- | ----------------- |
| 1   | 9.349     | coc.nvim          |
| 2   | 4.959     | vim-gruvbox8      |
| 3   | 3.270     | nvim-treesitter   |
| 4   | 2.615     | vim-fugitive      |
| 5   | 2.034     | fzf.vim           |
| 6   | 1.629     | fzf               |
| 7   | 0.280     | vim-commentary    |
| 8   | 0.067     | nvim-web-devicons |

This results in the total average of approximately 24.203 ms delay for the
startup time.

The chart was generated using
[vim-plugins-profile](https://github.com/hyiltiz/vim-plugins-profile).

#### Key Mappings

| Key Mapping        | Functionality                              | Mnemonic |
| ------------------ | ------------------------------------------ | -------- |
| `<Space>`          | Space is the Leader key                    |          |
| `<Leader><Leader>` | Toggle between buffers                     |          |
| `<Leader>c`        | Generic compiler and runner                | Compile  |
| `<Leader>f`        | Use fzf for file searching                 | Find     |
| `<Leader>l`        | Search for a line with a pattern in a file | Line     |
| `<Leader>r`        | Use fzf and rg for the string search       | Rg       |
| `<Leader>s`        | Toggle spell checking                      | Spell    |
| `<Leader>w`        | Toggle line-wrapping                       | Wrap     |
| `C-h`              | Switch to the left window                  |          |
| `C-j`              | Switch to the bottom window                |          |
| `C-k`              | Switch to the top window                   |          |
| `C-l`              | Switch to the right window                 |          |

### Automated Installation

Check out the installation wizard!

```console
$ git clone https://github.com/oniani/dots
$ ./setup.py --help
```

Also, please make sure that the system runs the latest macOS operating system.
Note that the setup script is idempotent: it can safely be run multiple times.

## License

[MIT License](LICENSE)
