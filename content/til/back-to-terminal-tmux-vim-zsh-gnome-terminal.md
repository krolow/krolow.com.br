+++
categories = ["tmux", "vim", "zsh"]
date = "2016-03-08T14:23:02-03:00"
title = "Back to terminal: Tmux + Vim + ZSH + Gnome Terminal"

+++
I was willing to get back to vim (i have used it about 8-9 years ago), In the last couple of years I have switch around between code editors, **I have tried**: Eclipse, Sublime 2 and lately I have been using atom.

I get motivated to get back to vim, after [have watched this talk about Vim](http://krolow.com.br/learningpath/vim/why-use-vim/talk-mastering-vim-language/), and by my [co-worker](http://nunes.io), whom is using vim as well... and it sounds exicted get back for use **only terminal**, to avoid as much as possible mouse.

So well to get back to terminal, I would need to leave the guake that I have been using for the past few years, because, I would need a new terminal to keep in full screen, but It would be nice to have support to split it into panels/windows... I have remember to have heard about **tmux**.

Given a look in [tmux](https://tmux.github.io/)

**Install (ubuntu):**

{{< highlight bash >}}
sudo apt-get install tmux
{{< /highlight >}}
It by defaults uses <kbd>Ctrl</kbd> + <kbd>B</kbd>, as the shortcut to trigger commands, **but** it is quite uncomfortable to type, so I was needing to change the trigger, after some research of how to change it I have found this repository: http://tony.github.io/tmux-config/

It is an example of tmux configuration, it changes the shortcut/trigger to <kbd>Ctrl</kbd> + <kbd>a</kbd> and it brings some cool configurations like:

- [tmux-mem-cpu-load](https://github.com/thewtex/tmux-mem-cpu-load)


**Backing to Tmux itself...**

So basically the commands are simple, they MUST be executed after the trigger/predix, so as I have used *tmux-config* now it is: <kbd>Ctrl</kbd> + <kbd>a</kbd>

**Some that I already get used to:**

**Pane**

* **Create vertical**: <kbd>Ctrl</kbd> + <kbd>a</kbd> <kbd>%</kbd>
* **Create horizontal**: <kbd>Ctrl</kbd> + <kbd>a</kbd> <kbd>"</kbd>
* **Rotate**: <kbd>Ctrl</kbd> + <kbd>a</kbd> <kbd>o</kbd>

**Window**

* **Create new**: <kbd>Ctrl</kbd> + <kbd>a</kbd>  <kbd>c</kbd>
* **Move to next window**:<kbd>Ctrl</kbd> + <kbd>a</kbd> <kbd>n</kbd>
* **Move to prev window**: <kbd>Ctrl</kbd> + <kbd>a</kbd> <kbd>p</kbd>
* **Move to specific window**: <kbd>Ctrl</kbd> + <kbd>a</kbd> <kbd>[0-9]</kbd>

**Scroll in specific panel** <kbd>Ctrl</kbd> + <kbd> a </kbd> <kbd>[</kbd> to active and <kbd>up</kbd> or <kbd>down</kbd> to scroll

I have deciced to start always tmux when **zsh**, to achieve I have added in the end of my ```vim ~/.zshrc```


{{< highlight bash >}}
if [[ ! $TERM =~ screen ]]; then
  exec tmux
fi
{{< /highlight >}}


as I have started to used tmux, I decided to give a better look for my terminal, by changing the **oh-my-zsh theme** and **terminal theme**, and **vim theme**. I have choosed to use dark theme similiar to atom.

* **Oh my zsh Theme:** [Spaceship](https://github.com/denysdovhan/spaceship-zsh-theme)
* **Gnome Terminal:** [One Gnome](https://github.com/denysdovhan/one-gnome-terminal)
* **Vim:** [atom Dark](https://github.com/gosukiwi/vim-atom-dark)

I need to give a look on [Powerline](https://github.com/powerline/powerline), after watch the below video it seems amazing:

<iframe width="854" height="480" src="https://www.youtube.com/embed/DgLIPYP8nnI" frameborder="0" allowfullscreen></iframe>

<br /><br />
A part of that I still needing to configure my **vim**, I have tried to use this [vimrc](https://github.com/amix/vimrc) it looks good, **BUT** I think to begin it would be better if I configure my vim by my self, so that I can learn while configure it.
