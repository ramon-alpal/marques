# Marquès

Marks of files of all kinds and of actions of all kinds

![Marquès' Logo](./logo.png)

# Notice

This repository has two versions of the files: the original one in
Catalan and the derived one in English.

See the file `LLEGEIXME` if you speak Catalan instead of this file you
have now opened.

## Requirements

In order to use the program you need the following packages installed:
- The `fzf` program to be used as a menu interface, or others like
  `dmenu` or `vis-menu` with a couple of adaptations that you will find
  on the notes;
- The `xclip` program in order to be able to interact with the X11's
  clipboard;
- An interactive shell capable of supporting the POSIX standard and
  capable of creating keybindings, like for example `bash` and `zsh`;
- Any text editor, like for example `vim` or `vi`;
- And basic utilities like `cp`, `ls`, `find` and `sed`.

## Installation

After you have satisfied the requirements you can begin with the the
installation.

For installing the program execute the following list of commands in your
shell for downloading the repository, changing directory and producing
the installation:

    git clone 'https://github.com/ramon-alpal/marques'
    cd marques
    sudo sh produ en install

During the installation you will be asked a user for installing it the
local configuration's file.

You can optionally make a local installation modifying the heading's
variables of the script `produ` or changing the environment variable
`$PREF`.

## Configuration and Usage

After the installation you will have to configure a couple more things
in order to begin using the program.

You have to add, if you use `bash`, in your configuration's files
`.bashrc` the following line in order to create a keybinding to
`Control-O` for the program:

    bind -x '"\C-o":". /usr/local/bin/marques"'

If you use `zsh`, you have to add into your configuration's file `.zshrc`
the following lines:

    function _marques { . /usr/local/bin/marques
    zle reset-prompt; }; zle -N _marques
    bindkey '^o' _marques

You have to define the environment variable `$EDITOR` for your preferred
text editor that you want to use, or else you will use the text editor
`vi`. If you don't know how to do it you have to simply add the following
line into the respective configuration's file that we used previously:

    export EDITOR=vim

There is also some more other insular thing that you will find on
the notes.

Now the program is completely functional, the only thing that it's
missing is adding your own marks for beginning to give it use.

In the installation's process it has been created a local
configuration's file and a global one at `~/.config/marques.conf` and at
`/usr/local/share/marques.conf` respectively with all the instructions
of how the configuration is structured with comments and with multiple
of my own marks.

## Absent

The installation producer script named `produ` has a primitive and
anti-standard way of choosing the user.

I don't know a good way of how to make the `produ` script be able to
install locally and globally without having to put `sudo` in front of
every corresponding instance of the global installation.

This issue doesn't allow me to use appropriately the `$XDG_CONFIG_HOME`
environment variables during the installation, resulting in that I have
to use `~/.config`.

## Notes

### Menu Interface

By default the `fzf` program is used as the menu interface, but you can
change it by disabling from the program the function situated at the
heading named `Menu` from the `fzf` and enabling one of the tow others
from the `dmenu` and `vis-menu`.

You can also create your own functions if you use a program that isn't
one of the three, the only main thing that you have to do is inserting the
first argument of the function where it belongs at the prompt of the menu.

By the way, I recommend using the `vis-menu` over the `fzf`. Is like the
`dmenu` but in the terminal, the small issue is that it's part of the
text editor [`vis`](https://github.com/martanne/vis).

### Change the LS Command

You can change the `ls` command for whatever you want editing the
program for the function `cmd_ls`.

### Extend the Program

You can extend the program for doing a thousand different things adding
more types of actions, for that the program has in the end a case
statement for making whatever you want to make.

### The Name

The name of the `marquès` program means in English `marquess` but it
actually has no relation to that, it's just from the simple casualty
that it matches with the Catalan word `marques`, without accent, that
means marks.

You could pronounced in Catalan if you can, it would be `/mar'kɛs/`. But
I don't really care that much of these kind of games so you could
pronounces as the equivalent English wort `marquess`.

### Other Notes

- In order to be able to use the program it has to be executed in
  the current shell, for doing that you have to source the program with
  `. /route/program`, specially for the changing of a directory. This
  is what can cause to not be able to be use in shells that don't follow
  the POSIX standard, like for example `fish`.
- For opening files you could use `xdg-open` instead of the `$EDITOR`,
  as not all the files to be opened will be of text.
