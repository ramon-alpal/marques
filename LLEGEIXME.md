# Marquès

Marques de fitxers de tota mena i d'accions de tota mena

![Logo del Marquès](./logo.png)

## Avís

Aquest repositori té dos versions dels fitxers: la original en Català
i la derivada en Anglès.

Vegeu el fitxer [`README`](./README.md) si parleu Anglès en ves d'aquest
fitxer que teniu ara obert.

## Descripció

Aquest guió (script) et permet tindre un fitxer per a ficar rutes a
fitxers i directoris amb un nom i una acció.

Per exemple: Jo tinc una marca nomenada `crepo` que té com a ruta un
directori ple de fitxers plantilla per a crear un repositori, aquesta
marca al ser seleccionada li tinc una acció que em copia al directori
actual tots els fitxers plantilla. També en tinc una altra que té la
mateixa ruta però es nomenada `platrepo` i li tinc la acció de canviar
de directori.

Com a interfície s'utilitza programes com el `fzf` o `dmenu`.

## Requeriments

Per a poder utilitzar el guió necessites els següents paquets
instaŀlats:

- El programa `fzf` per a utilitzar-lo com a interfície de menú,
  o altres com el `dmenu` o `vis-menu` amb un parell d'adaptacions que
  trobaràs a les [notes](#Notes);
- El programa `xclip` per a poder interactuar amb el portapapers d'X11;
- Una closca (Shell) interactiva capaç de suportar l'estàndard POSIX
  i capaç de crear lligadures, com per exemple `bash` i `zsh`;
- Qualsevol editor de text, com per exemple `vim` o `vi`;
- I utilitats bàsiques com `cp`, `ls`, `find` i `sed`.

## Instaŀlació

Després d'haver satisfet els requeriments pots començar amb la
instaŀlació.

Per a instaŀlar el guió executa la següent llista de comandaments
a la teva closca per a baixar el repositori, canviar de directori i
produir la instaŀlació:

    git clone 'https://github.com/ramon-alpal/marques'
    cd marques
    sudo sh produ ca inst

Durant la instaŀlació se't preguntarà un usuari per a instaŀlar-li
el fitxer de configuració local.

Pots optativament fer una instaŀlació local modificant les variables de
la capçalera del guió `produ` o canviant la variable ambiental `$PREF`.

## Configuració i Utilització

Després de la instaŀlació hauràs de configurar un parell de coses
més per a poder començar a utilitzar el guió.

Has d'afegir, si utilitzes `bash`, al teu fitxer de configuració
`.bashrc` la següent línia per a poder crear una lligadura a `Control-O`
del guió:

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

També hi ha unes quantes coses més insulars que trobaràs a les
[notes](#Notes).

Ara el guió ja és completament funcional, l'únic que et queda és
afegir les teves pròpies marques per a començar-li a donar ús.

En el proces d'instaŀlació s'ha creat un fitxer de configuració local
i global a `~/.config/marques.conf` i a `/usr/local/share/marques.conf`
respectivament amb totes les instruccions de com la configuració és
estructurada en comentaris i amb múltiples de les meves pròpies marques.

## Absent

El guió productor de la instaŀlació titulat `produ` té una forma de
triar usuari que és primitiva i anti-estàndards.

No sé una bona manera de com fer que el `produ` pugui instaŀlar
localment i globalment sense haver de ficar `sudo` davant de cada
instància que correspongui a la instaŀlació global.

Aquest problema no em permet utilitzar apropiadament la variable ambiental
`$XDG_CONFIG_HOME` durant la instaŀlació, resultant en que he de fer
servir `~/.config`.

## Notes

### Interfície de Menú

De forma predeterminada s'utilitzarà el programa `fzf` com a la
interfície de menú, però pots canviar-ho desactivant del guió la
funció situada a la capçalera titulada `Menu` del `fzf` per activar
una de les dos altres del `demnu` i `vis-menu`.

També pots crear la teva pròpia funció si utilitzes un programa
que no sigui ningun dels tres, l'únic que has de fer principalment
és inserir el primer argument de la funció a on correspongui l'avís
(Prompt) del menú.

Per cert, Jo recomano utilitzar el `vis-menu` per sobre del `fzf`. És
com el `dmenu` però a la terminal, el petit problema és que és part
de l'editor de text [`vis`](https://github.com/martanne/vis).

### Canviar el Comandament d'LS

Pots editar el comandament `ls` per el que vulguis editant del guió la
funció `cmd_ls`.

### Extendre el Programa

Pots extendre el guió per a fer mil coses diferents afegint més tipus
d'accions, per a tal el guió té cap al final una instrucció de casos
per a ficar el que vulguis ficar.

### El Nom

El nom del guió de `marquès` és de la simple casualitat de que concorda
amb `marques`.

### Altres Notes

- Per a poder utilitzar el guió ha de ser executat a la closca actual,
  per a tal s'ha d'importar el guió amb `. /ruta/guio`, especialment
  per a canviar de directori. Això és el que pot causar que no es
  pugui utilitzar en closques que no segueixen l'estàndard POSIX,
  com per exemple `fish`.
- Per a obrir fitxer es podria utilitzar `xdg-open` en ves del `$EDITOR`,
  ja que no tots els fitxers a obrir seran fetes de text.
