# How to install
## How to install for Emacs24

    M-x list-packages
    lookup to logalimacs
    もっとちゃんとかく....

## How to install for otherwise


    % git clone https://yuutayamada@github.com/logaling/logalimacs.git

## Sets config to your as .emacs
1. Put logalimacs where to pass load-path.
2. Sets as below to your .emacs for setting.
3. let's type M-x loga-intarective-command or your set key.
4. if you like type "f" after the intarective-command, allow to executable "loga lookup" at on the fly.  
(word to point of current cursor where execute the lookup)
5. retype like same "4.~" section, you can avoid above used loga-fly-mode.

---

    ;;the second section example
    (when (require 'logalimacs nil t)
      (global-set-key (kbd "M-g M-i") 'loga-interactive-command)
      (global-set-key (kbd "M-g M-l") 'loga-lookup-in-hand-or-region)
      (global-set-key (kbd "M-g M-a") 'loga-add-word))

    ;;or, use only interactive-command
    (autoload 'loga-interactive-command "logalimacs"
      "front-end for logaling-command")
    (global-set-key (kbd "M-g M-i") 'loga-interactive-command)

---


## convenient configuration for popwin.el


this is requirement [_popwin.el_](http://www.emacswiki.org/emacs/PopWin).

    (require 'popwin)
    (setq display-buffer-function 'popwin:display-buffer)
    (setq popwin:special-display-config
          (append '(
                ("*logalimacs*" :position bottom :height 10 :noselect t :stick t)
                ;;if need to other configuration, add for like below:
                ;("*Backtrace*")
                )
              popwin:special-display-config))

    (setq popwin:popup-window-height 15   ;default 15. if left or right, ignored
          popwin:popup-window-width 30    ;default 30. if top or bottom, ignored
          )