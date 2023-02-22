# Marquès

Marques de fitxers de tota mena i d'accions de tota mena

![Logo del Marquès](./logo.png)

## Avís

Aquest repositori té dos versions dels fitxers: la original en Català
i la derivada en Anglès.

Mireu el fitxer `README` si parleu Anglès en ves d'aquest fitxer que
teniu ara obert.

## Requeriments

Per a poder utilitzar el programa necessites els següents paquets
instal·lats:
- El programa `fzf` per a utilitzar-lo com a interfície de menú,
  o altres com el `dmenu` o `vis-menu` amb un parell d'adaptacions que
  trobaràs a les notes;
- El programa `xclip` per a poder interactuar amb el portapapers d'X11;
- Una closca (shell) interactiva capaç de suportar l'estàndard POSIX
  i capaç de crear lligadures, com per exemple `bash` i `zsh`;
- Qualsevol editor de text, com per exemple `vim` o `vi`;
- I utilitats bàsiques com `cp`, `ls`, `find` i `sed`.

## Instal·lació

Després d'haver satisfet els requeriments pots començar amb la
instal·lació.

Per a instal·lar el programa executa la següent llista de comandaments
a la teva closca (shell) per a baixar el repositori, canviar de directori
i produir la instal·lació:

    git clone 'https://github.com/ramon-alpal/marques'
    cd marques
    sudo sh produ ca inst

Durant la instal·lació se't preguntarà un usuari per a instal·lar-li
el fitxer de configuració local.

Pots optativament fer una instal·lació local modificant les variables de
la capçalera del guió (script) `produ` o canviant la variable ambiental
`$PREF`.

## Configuració i Utilització

Després de la instal·lació hauràs de configurar un parell de coses
més per a poder començar a utilitzar el programa.

Has d'afegir, si utilitzes `bash`, al teu fitxer de configuració
`.bashrc` la següent línia per a poder crear una lligadura a `Control-O`
del programa:

    bind -x '"\C-o":". /usr/local/bin/marques"'

Si utilitzes `zsh`, has d'afegir al teu fitxer de configuració `.zshrc`
les següents línies:

    function _marques { . /usr/local/bin/marques
    zle reset-prompt; }; zle -N _marques
    bindkey '^o' _marques

Has de definir la variable ambiental `$EDITOR` per a l'editor de text
que vulguis utilitzar, sinó s'utilitzarà l'editor `vi`. Si no saps
com fer-ho has de simplement afegir la següent línia al teu respectiu
fitxer de configuració que em utilitzat anteriorment:

    export EDITOR=vim

També hi ha unes quantes coses més insulars que trobaràs a les notes.

Ara el programa ja és completament funcional, l'únic que et queda és
afegir les teves pròpies marques per a començar-li a donar ús.

En el proces d'instal·lació s'ha creat un fitxer de configuració local
i global a `~/.config/marques.conf` i a `/usr/local/share/marques.conf`
respectivament amb totes les instruccions de com la configuració és
estructurada en comentaris i amb múltiples de les meves pròpies marques.

## Absent

El guió (script) productor de la instal·lació titulat `produ` té
una forma de triar usuari que és primitiva i anti-estàndards.

No sé una bona manera de com fer que el `produ` pugui instal·lar
localment i globalment sense haver de ficar `sudo` davant de cada
instància que correspongui a la instal·lació global.

Aquest problema no em permet utilitzar apropiadament la variable ambiental
`$XDG_CONFIG_HOME` durant la instal·lació, resultant en que he de fer
servir `~/.config`.

## Notes

### Interfície de Menú

De forma predeterminada s'utilitzarà el programa `fzf` com a la
interfície de menú, però pots canviar-ho desactivant del programa la
funció situada a la capçalera titulada `Menu` del `fzf` per activar
una de les dos altres del `demnu` i `vis-menu`.

També pots crear la teva pròpia funció si utilitzes un programa
que no sigui ningun dels tres, l'únic que has de fer principalment
és inserir el primer argument de la funció a on correspongui l'avís
(prompt) del menú.

Per cert, Jo recomano utilitzar el `vis-menu` per sobre del `fzf`. És
com el `dmenu` però a la terminal, el petit problema és que és part
de l'editor de text [`vis`](https://github.com/martanne/vis).

### Canviar el Comandament d'LS

Pots editar el comandament `ls` per el que vulguis editant del programa
la funció `cmd_ls`.

### Extendre el Programa

Pots extendre el programa per a fer mil coses diferents afegint més
tipus d'accions, per a tal el programa té cap al final una instrucció
de casos per a ficar el que vulguis ficar.

### El Nom

El nom del programa de `marquès` és de la simple casualitat de que
concorda amb `marques`.

### Altres Notes

- Per a poder utilitzar el programa ha de ser executat a la closca (shell)
  actual, per a tal s'ha d'importar el programa amb `. /ruta/programa`,
  especialment per a canviar de directori. Això és el que pot causar que
  no es pugui utilitzar en closques (shells) que no segueixen l'estàndard
  POSIX, com per exemple `fish`.
- Per a obrir fitxer es podria utilitzar `xdg-open` en ves del `$EDITOR`,
  ja que no tots els fitxers a obrir seràn de text.
