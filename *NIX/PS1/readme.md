# PS1 (Escape Sequences (ES))

An ES has a one or more `<modifier>`
Here's the syntax :

```
\033[<modifier; ...>m
       ou
\e[<modifier; ...>m
```

It will modify all the text on the right.
To stop the modification, use the ES `\e[0m`


## Possible \<modifier\>

- **38;5;\<color\> :** change the text to \<color\><sup>1</sup>
```bash
# example
\e[38;5;48m I'm very green
```

- **48;5;\<color\> :** change the background to \<color\><sup>1</sup>
```bash
# example
\e[48;5;48m I have a green background
```

- **1 :** change the text to bold
```bash
# example
\e[1m I am so bold
```

- **4 :** underline the text
```bash
\e[4m I am underlined
```

- **0 :** no text transform



<sup>1</sup> All possible colors can be checked using this function :
```bash
show255colors() {
    for C in {16..255}; do
	echo -en "\e[48;5;${C}m$C ";
    done
    echo -en "\e[0m";
}
```

## Combinaison

You can also combine the modifiers, for instance :

```bash
\e[38;5;48;1m I am green and bold
\e[38;5;124;48;5;211;4m I am underline, burgundy on pink background
# (the order doesn't matter)
```

## Placeholders


- **\u** : username
- **\h** : host
- **\w** : pwd
- **\W** : basedir(pwd)
- **\d** : date
- **\n** : newline

When you define a PS1, you can use those, for instance :
```bash
 PS1='\[\e[38;5;48m\]\w \[\e[1;38;5;211m\]\u $'
```

This will define prompt a green path and a pink username


## Functions

We can use function and stamp them inside the PS1, for instance :
```bash
showBranch() {
    git branch 2>/dev/null | sed -n "s/* \(.*\)/\1 /p";
}
PS1="\u \$(showBranch) \n$"
PS1='\u $(showBranch) \n$'
```
