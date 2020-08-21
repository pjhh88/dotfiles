Dotfiles
========

🏠 Personal dotfiles for \*NIX (Mac OS X and Linux) systems.

Installation
------------

### 👉 One-liner (if you trust me):

```bash
curl -fsSL https://dotfiles.sleepykitty.kr/etc/install | bash
```

<details><summary>
💡 (Tip) You only need to remember <code>curl dotfiles.sleepykitty.kr</code> (Click to expand)
</summary></p>

Every file is accessible through `dotfiles.sleepykitty.kr` (via `curl -L` or `wget`), e.g.,

* https://dotfiles.sleepykitty.kr/vimrc
* https://dotfiles.sleepykitty.kr/vimrc?raw=true
* https://dotfiles.sleepykitty.kr/bin/tb

<p></details>

<details><summary>
🤔 Want to manually clone and install? (Click to expand)
</summary><p>

```bash
$ git clone --recursive https://github.com/pjhh88/dotfiles.git ~/.dotfiles
$ cd ~/.dotfiles && python install.py
```

<!--
Note: The option `-j8` (`--jobs 8`) works with Git >= 2.8 (parallel submodule fetching).
For older versions of Git, try without `-j` option.
-->

</p></details>

<br>


The installation script will clone the repository into `~/.dotfiles` and create symbolic links (e.g., `~/.vimrc`) for you.
If target files already exist (e.g. `~/.vim`, `~/.vimrc`), you will need to manually resolve the conflict (delete the old one or just ignore). See Troubleshooting below for details.


`$ dotfiles`
------------

**To update dotfiles** (pull changes from upstream and run [`install.py`][install.py] again):

```bash
$ dotfiles update
$ dotfiles update --fast          # fast update mode: skip updating {vim,zsh} plugins
```

On Linux, you can [install some common softwares locally][linux-locals.sh] (into `$HOME/.local/bin`) *without sudo*:

```bash
$ dotfiles install neovim         # -> ~/.local/bin/nvim
$ dotfiles install ripgrep        # -> ~/.local/bin/rg
```


🆘 Troubleshooting
------------------

* If something goes wrong, run **[`$ dotfiles update`][dotfiles-update]** (or [install.py]) to have everything up-to-date.
    * *Read carefully warning messages during installation !!*
    * If you have your own `~/.zshrc`, `~/.vimrc`, `~/.vim`, etc., that are NOT symbolic links,
      they will not be overwritten by default.
      In such cases you should delete these files *manually*.

* If you are using [**neovim**][neovim] and seeing any startup errors (e.g. `no module named neovim`):
    * Try `:checkhealth`.
    * Use **`neovim >= 0.4.2`.**
      To install/upgrade neovim on your system, try `dotfiles install neovim`.
    * We require python3 version not less than 3.4.  **Python 3.6+** is recommended (semshi: 3.5+)
    * Make sure that the [`pynvim`](https://pypi.python.org/pypi/pynvim/) pypi package is installed on *local* python 3,
      i.e. the python3 on conda, virtualenv, etc.
      This should have been automatically installed.
      If it doesn't work, check `which python3`. Use the following vim command to tell which host python is used:
          [`:echo g:python3_host_prog`](https://github.com/wookayin/dotfiles/blob/master/nvim/init.vim).
      * If you are not sure, manually running `python3 -m pip install --user pynvim` might help.

* [Powerline symbols](https://github.com/powerline/powerline#screenshots) are not displayed properly?
  Install [Powerline fonts](https://github.com/powerline/fonts) or
  [Nerd fonts](https://github.com/ryanoasis/nerd-fonts).
* Does vim color look weird (e.g. only black-and-white)?
  * Check whether your terminal emulator supports [24-bit color](https://github.com/wookayin/dotfiles/pull/9). Use iTerm2 rather than built-in Terminal.
  * Try `:set notermguicolors` to disable 24-bit colors.
* Does tmux look weird? Make sure that tmux version is [2.3](etc/ubuntu-setup.sh) or higher.
    * Run `$ dotfiles install tmux` to install `tmux` into `$HOME/.local/bin`, if you do not have sudo.
* Ruby version is shown unwantedly? A simple workaround might be to install [rvm](https://rvm.io/).
* If you still have no idea or have found a bug, please feel free to contact me or raise an issue.


[neovim]: https://github.com/neovim/neovim
[dotfiles-update]: https://github.com/wookayin/dotfiles/blob/master/bin/dotfiles
[linux-locals.sh]: https://github.com/wookayin/dotfiles/blob/master/etc/linux-locals.sh
[install.py]: https://github.com/wookayin/dotfiles/blob/master/install.py


License
-------

The MIT License (MIT)

Copyright (c) 2012-2020 Jongwook Choi (@wookayin)
