+++
title = "Power User Setup for Unix-based Operating Systems"
date = 2020-02-17
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
- Email: [neomutt](https://neomutt.org/) (with [isync](http://isync.sourceforge.net/) for mailbox synchronization and [msmtp](https://marlam.de/msmtp/) for sending emails)
- File Format Handler: [pandoc](https://pandoc.org/)
- File Manager: [nnn](https://github.com/jarun/nnn)
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
- [goyo.vim](https://github.com/junegunn/goyo.vim)
- [lightline.vim](https://github.com/itchyny/lightline.vim)
- [vim-commentary](https://github.com/tpope/vim-commentary)
- [vim-fugitive](https://github.com/tpope/vim-fugitive)
- [vim-moonfly-colors](https://github.com/bluz71/vim-moonfly-colors)
- [vim-polyglot](https://github.com/sheerun/vim-polyglot)
- [vim-surround](https://github.com/tpope/vim-surround)

#### Current Stats

Plugins arranged according to their startup time.

| TOP | Time (ms) | Plugin             |
| --- | --------- | ------------------ |
| 1   | 27.572    | vim-polyglot       |
| 2   | 12.027    | vim-fugitive       |
| 3   | 11.635    | coc.nvim           |
| 4   | 7.789     | vim-moonfly-colors |
| 5   | 1.588     | lightline.vim      |
| 6   | 1.268     | fzf.vim            |
| 7   | 1.011     | fzf                |
| 8   | 0.640     | vim-surround       |
| 9   | 0.265     | vim-commentary     |
| 10  | 0.087     | goyo.vim           |

This results in the total average of approximately 63.882 ms delay for the
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
| `<Leader>z`        | Toggle Goyo                                | Zen      |
| `C-h`              | Switch to the left window                  |          |
| `C-j`              | Switch to the bottom window                |          |
| `C-k`              | Switch to the top window                   |          |
| `C-l`              | Switch to the right window                 |          |

### Automated Installation

In order to start the installation wizard, execute the commands below:

```console
$ git clone https://github.com/oniani/dots
$ ./setup.py --help
```

Also, please make sure that the system runs the latest macOS operating system.
Note that the setup script is idempotent: it can safely be run multiple times.

## License

[GNU General Public License v3.0](LICENSE)
