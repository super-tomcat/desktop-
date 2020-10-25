# desktop++
Put Emacs Desktop+ package on a menu for quicker access

I have got more to add to this, so bear with me :-)

This is a small enhancement to the emacs DESKTOP+ PACKAGE.. https://github.com/ffevotte/desktop-plus

Desktop+ is easier to use than the Builtin Desktop (which this still needs).

This code simply creates a new menu pane called "Desktop+" in the menu bar to the right of the "File" menu.

Important for when you first start using this package:

Once you have a desktop (any files/windows etc) that you want to have reloaded each time emacs starts then you need to issue the command: M-x desktop-save, or use the "Save the desktop to your own folder" menu option under the new Desktop+ menu, then pick the .emacs.d folder to save it into, this will then be saved and reloaded each time emacs starts, so long as you also put this next line in your emacs init file:
```
(desktop-save-mode 1)
```
NOTE: This command is not part of Desktop+ but the normal Desktop mode built into Emacs, if you switch this off then you will need to use Desktop+ above to reload a saved desktop each time you start Emacs.

You can also save (you should pick any other folder other than the .emacs.d folder to save it into) and reload any other desktop at any time by using the commands on the menu.

When you first use the save option (desktop+-create) it will ask you for a folder, note that after you pick your folder all future saves will automatically go in that folder.


Make sure you have already installed the Desktop+ package into emacs with something like this in your init file:

```
(use-package desktop+
    :ensure t)
```

Then add the following code also to your emacs init file then restart Emacs....

```
(define-key-after
  global-map
  [menu-bar desktopplusmenu]
  (cons "Desktop+" (make-sparse-keymap "hey there"))
  'file)
;; Creating a menu item to a desktop+ command, under the menu by the id "[menu-bar desktopplusmenu]"
(define-key
  global-map
  [menu-bar desktopplusmenu ploadauto]
  '("Load an auto named desktop - based on current directory" . desktop+-load-auto))
;;
(define-key
  global-map
  [menu-bar desktopplusmenu pcreateauto]
  '("Create an auto named desktop - based on current directory" . desktop+-create-auto))
;;
(define-key
  global-map
  [menu-bar desktopplusmenu pcreate]
  '("Create a named desktop" . desktop+-create))
;;
(define-key
  global-map
  [menu-bar desktopplusmenu pload]
  '("Load a named desktop" . desktop+-load))
;; 
(define-key
  global-map
  [menu-bar desktopplusmenu psave]
  '("Save the desktop to your own folder" . desktop-save))
 
 ```
 
 You should now see a new menu called Desktop+
