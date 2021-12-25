---
title: Nick's Zettelkasten
dirtree:
  display: false
---
- [[b5c75538]]
- [[135fb390]]
- [[3c438a6a]]
- [[8e6e92d1]]
- [[93ed4657]]

## Significant Hotkeys & Notes
- "/" in fzf directories, C-a+SPC, C-a+S in tmux
-

## Projects

- [[6ad8cd43]]
- [[4de119a0]]

## References

* [[cli]]#
* [[lang]]#
* [[libs]]#

add providerInventory table, look at spadash_api.customer_credit_transactions table for example
https://bitbucket.org/spadash/send-customer-appointment-receipts/src/master/
send-customer-appointment-receipt
- only tarps for now


# /home/nicholas/.config/nvim
# /etc/xdg/xdg-i3/nvim
# /etc/xdg/nvim
# /home/nicholas/.local/share/nvim/site
# /home/nicholas/.local/share/nvim/site/pack/packer/opt/gitsigns.nvim
# /home/nicholas/.local/share/nvim/site/pack/*/start/*
# /home/nicholas/.local/share/nvim/site/pack/packer/opt/friendly-snippets
# /home/nicholas/.local/share/nvim/site/pack/packer/opt/vs-snippets
# /home/nicholas/.local/share/nvim/site/pack/packer/opt/cmp-vsnip
# /home/nicholas/.local/share/nvim/site/pack/packer/start/packer.nvim
# /usr/share/i3/nvim/site
# /home/nicholas/.local/share/flatpak/exports/share/nvim/site
# /var/lib/flatpak/exports/share/nvim/site
# /usr/local/share/nvim/site
# /usr/share/nvim/site
# /var/lib/snapd/desktop/nvim/site
# /home/nicholas/.local/share/nvenv/versions/0.6.0/share/nvim/runtime
# /home/nicholas/.local/share/nvenv/versions/0.6.0/share/nvim/runtime/pack/dist/opt/matchit
# /home/nicholas/.local/share/nvenv/versions/0.6.0/lib/nvim
# /home/nicholas/.local/share/nvim/site/pack/*/start/*/after
# /home/nicholas/.local/share/nvim/site/pack/packer/opt/cmp-vsnip/after
# /var/lib/snapd/desktop/nvim/site/after
# /usr/share/nvim/site/after
# /usr/local/share/nvim/site/after
# /var/lib/flatpak/exports/share/nvim/site/after
# /home/nicholas/.local/share/flatpak/exports/share/nvim/site/after
# /usr/share/i3/nvim/site/after
# /home/nicholas/.local/share/nvim/site/after
# /etc/xdg/nvim/after
# /etc/xdg/xdg-i3/nvim/after
# /home/nicholas/.config/nvim/after

## Paths in LUA

The question could be split in the following:
1) What I mean for "Scirpt file"
2) How get info about where it is
3) How extract the absolute path
4) Split name and directory


What is a script file:
a) The "Main script file", i.e. the one you pass to the lua standalone interpreter from the command line
b) Any other file loaded by the main one through `require`
c) A string passed to `load` with a third parameter that is a proper file reference

These are all the ways you have to actually execute lua code. Note that an embedding
application that calls lua, falls in the case c) as well as a lua C modules calling lua code.

The info 2) is in `arg[0]` just for the case a). However, for all the cases you can use:

```
path = debug.getinfo(1,"S").source:sub(2)
```

but remember that in c) what is returned is what you passed to `load` as third parameter
(is up to you to specify correctly where you took the information).

However the info returned can be a RELATIVE path, e.g.:
- in a) could return `./main.lua` if you launched the script with `lua ./main.lua`
- in b) `package.path='./module/?.lua' require 'mymodule' ` could return './module/mymodule.lua'

Sadly, if you really need the abolute path 3), you have to rely on os-dependent tricks.
For linux you can use popen and realpath:

```
absolute = io.popen("realpath '"..path.."'", 'r'):read('a')
absolute = absolute:gsub('[\n\r]*$','') -- needed to handle popen result
```

This give you the absolute path to the file, so for the step 4) you need a bit of
string parsing to split path and name, e.g. `absolute:match('^(.*/)([^/]-)$')`.

So putting all togheter:

```
local fullpath = debug.getinfo(1,"S").source:sub(2)
fullpath = io.popen("realpath '"..fullpath.."'", 'r'):read('a')
fullpath = fullpath:gsub('[\n\r]*$','')

local dirname, filename = fullpath:match('^(.*/)([^/]-)$')
dirname = dirname or ''
filename = filename or fullpath
```


```sh


# For a script that works in both bash and zsh, you need to use a more complicated syntax.
# Eg, to reference the first element in an array:
${array[@]:0:1}
# Here, array[@] is all the elements, 0 is the offset (which always is 0-based), and 1 is the number of elements desired.

# TODO: disable ctrl-r and ctrl-e if not relevant (nvim script check if file exists)
# ctrl-r: reload
# ctrl-e: edit
# ctrl-y: copy
# ctrl-o: xdg-open
# ctrl-^: toggle popup
# ctrl-shift-y: copy preview contents
# ctrl-shift-a: select all
# ctrl-shift-d: delete/remove
# ctrl-shift-i: install
# F1, F2 ... modes
# S-F1, S-F2 ... toggles



# $-p    -> M-p    : tmux attach _fz-repos
# $-n/N  -> M-n/N  : swap panes with back window
# $-]/[  -> M-]/[  : next/previous session
# $-z    -> M-z    : tmux fullscreen
# $-f    -> M-f    : tmux fullscreen + i3 fullscreen
# $-k    -> ...    : kill session list

# $-i    -> M-i    : attach to zettelkasten
# $-\    -> M-\    : attach to main

# pfx-bs -> ...    : reset session
# $-bs   -> free
# C-del  -> ...    : exit tmux pane
# $-del  -> pfx-d  : kill session no detach


```
