# Lisp/Emacs


Page-Up
Page-Down to reach minibuffer
`C-x C-r` ouvre les buffers ouverts


### Init

- `~/.emacs` ou `~/.emacs.el` ou `~/.emacs.d/init.el`
- `-q` pour lancer Emacs sans init.
- `-u` pour lancer Emacs avec l'init d'un autre utilisateur

### termes
- un **symbole** (gnu: symbol) est un nom de variable. Une variable pouvant être une valeur, une fonction , etc...

### fonctions/macros (commun)
- Une **fonction** ou un **macro** possèdent un code associé. Ce code associé s'appelle une **définition** (gnu: definition) et donc selon le cas la **définition de la fonction** (gnu: function definition) ou la **définition du macro** (gnu: macro definition).
- Dans cette définition, on retrouve le nom de la fonction/macro même, une liste de paramètres, une documentation, une expression optionelle pour rendre l'appelle **interactif** (gnu: interactive), et le **corps** de la fonction (gnu: body).

### fonctions

- On utilise `defun` pour créer une nouvelle 
**fonction**.

```lisp
(defun function-name (arguments...)
  "optional-documentation..."
  (interactive argument-passing-info)
  body...)

;; Par exemple

(defun multiply-by-seven (number)
  "Multiply NUMBER by seven."
  (* 7 number))
```
*`multiply-by-seven` est appelé `symbol`*

### macros

- On utilise `defmacro` pour créer un nouveau **macro**.

```lisp
(defmacro macro-name (arguments...)
  "optional-documentation..."
  body...)

;; Par exemple

(defmacro inc (var)
  (list 'seq var (list '1+ var)))
```

Un **macro** c'est comme une **fonction** sauf que les arguments ne sont pas évalués au moment où ils sont passés au **corps**. On récupère plutôt leur référence. Aussi la valeur retournée d'un **macro** est une expression alternative Lisp appelée **expansion du macro** (gnu: the expansion of the macro). L'interpréteur Lisp évalue ensuite cette expansion lorsqu'elle est retournée depuis le macro.
- `macroexpand` permet de voir l'expansion pré-évaluée d'un macro, utilisée par Emacs pour expandre à l'avance des macros et charger plus rapidement des fichiers `.el` non compilés. Cette procédure s'appelle **eager macro expansion**.

```lisp
(defmacro inc (var)
  (list 'setq var (list '1+ var)))

(macroexpand '(inc r))
  ⇒ (setq r (1+ r))
```

### &rest
- semblables au variadic dans les listes d'arguments

## Emacs

### Interface

- le minibuffer c'est la bar I/O tout en bas.


### Les briques `.el` d'Emacs

- Emacs peut être représenté comme une organisation d'un grand nombre de fichiers `.el` qui lui donne de l'intelligence.
- Chaque fichier `.el` contient des variables, fonctions, etc... et a une fonction bien spécifique (ex. `package.el` qui gère toute la partie système logique des paquets).
- `.el` pour les fichiers Lisp classiques et `.elc` pour les fichiers Lisp compilés en byte-code (plus rapide à charger).
- `M-x load file` pour charger un fichier Lisp dans l'espace d'expression d'Emacs. Ou `M-x load-library` si le fichier est dans le load path.
- `(add-to-list 'load-path "~/.emacs/mydir")` pour ajouter un chemin dans le load path.
- Certaines fonctions sont autoloadées (pas besoin de `M-x load-file` avant de les utiliser).


- `C-h f` : pour décrire une fonction.

### Paquets / Packages

- Un paquet = 1 fichier `.el` ou plusieurs fichiers `.el` dans un tar.
- `C-h v package-archives RET` pour voir les arhives de paquets installés (par défaut seulement **elpa**).
- Installés par défaut dans `~/.emacs.d/elpa` depuis le serveur d'archive des paquets elpa.
- Les paquets installés dans `~/.emacs.d/elpa` sont appelés "name-version subdirectory".
- `list-packages` pour installer un paquet depuis une interface ou `M-x install-package`.