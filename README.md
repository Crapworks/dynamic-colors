# dynamic-colors-256

This is a fork of [sos4nt](https://github.com/sos4nt) [dynamic-colors](https://github.com/sos4nt/dynamic-colors).
This will not patch the first 16 colors in the color palette (ANSI) but will use the 256 color capability of newer terminal an patch the colors 100-116.
This will preserve the use of bold/bright ANSI colors

This is a small tool for changing your terminal colors on the fly.

I use it to switch my entire [tmux](http://tmux.sourceforge.net/) session between [Solarized](http://ethanschoonover.com/solarized) dark and light modes.


## Pre-requisites

Your terminal must support the appropriate OSC escape sequences. xterm and urxvt (rxvt-unicode) work fine, whereas Terminal.app and iTerm won't recognize these sequences.

Make sure `dynamicColors` is enabled in `.Xdefaults`/`.Xresources`

    xterm*dynamicColors: true
    urxvt*dynamicColors: on

### Compatibility Check

This changes your terminal background color to red if your terminal supports OCS:

    echo -e "\033]11;#ff0000\007"


## Setup

1. Clone the repository into `~/.dynamic-colors`:

        git clone https://github.com/sos4nt/dynamic-colors ~/.dynamic-colors

2. To add the tool to your `PATH` put the following line in your profile (`.bashrc`/`.zshrc`/`.profile`).

        export PATH="$HOME/.dynamic-colors/bin:$PATH"

3. For Zsh autocompletion add this to your `.zshrc`/`.zshenv`:

        source $HOME/.dynamic-colors/completions/dynamic-colors.zsh

## Usage

List available color schemes:

    dynamic-colors list

Switch to a color scheme:

    dynamic-colors switch solarized-dark

Reload last color scheme:

    dynamic-colors init

Add this line to your profile to always set the last color scheme.

### Integration

I'm using the provided color schemes in conjunction with [dircolors-solarized](https://github.com/seebi/dircolors-solarized) and [vim-colors-solarized](https://github.com/altercation/vim-colors-solarized) for best results. Always use the dark mode and switch schemes with `dynamic-colors switch <colorscheme>`


## Developing color schemes

Create a new color scheme (will be opened in your default editor):

    dynamic-colors create my-color-scheme

Edit an exising color scheme:

    dynamic-colors edit my-color-scheme

Check if all colors are defined:

    dynamic-colors audit my-color-scheme

