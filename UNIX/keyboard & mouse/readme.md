# Keyboard & Mouse

## Mouse

- Si les cliques milieux du touchpad ne fonctionnent pas après installation, il faut créer ce fichier dans `/etc/X11/xorg.conf.d/99-synaptics-overrides.conf` (testé sous Fedora 26) :

```conf
Section  "InputClass"
    Identifier  "touchpad overrides"
    # This makes this snippet apply to any device with the "synaptics" driver
    # assigned
    MatchDriver  "synaptics"

    ####################################
    ## The lines that you need to add ##
    # Enable left mouse button by tapping
    Option  "TapButton1"  "1"
    # Enable vertical scrolling
    Option  "VertEdgeScroll"  "1"
    # Enable right mouse button by tapping lower right corner
    Option "RBCornerButton" "3"
    ####################################

EndSection
```