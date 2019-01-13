## Sources
 - https://npm.community/t/tink-state-of-the-unwinder-2019-01-15/4676
 - https://github.com/npm/tink
 - https://blog.npmjs.org/post/178027064160/next-generation-package-management
 - https://npm.community/t/tink-faq-a-package-unwinder-for-javascript/3191
 - https://medium.com/npm-inc/npm-weekly-163-introducing-tink-visit-npm-communitys-75ec64ddf05f
 - https://www.theregister.co.uk/2018/09/15/npm_yarn_project/
 - https://syndicode.com/2018/09/17/tink-is-a-next-generation-package-manager-for-javascript/

## Notes
### Comment sont rangés les fichiers
 - Exécuter tink plusieurs fois jusqu'à avoir un run qui fonctionne
 - Supprimer ~/.npm/
 - Relancer tink
    * Les nouvelles dépendances doivent se DL
 - dans ~/.npm/index-v.*/ il y a la descriptions des packages et de chacun des fichiers contenus dans ce package
 - dans ~/.npm/content-v.*/ il y a le contenu des fichiers de chaque package, qu'on peut retrouver via leurs hash

### Comportements chelous
 - Supprimer le package-lock.json sans supprimer le dossier `node_modules` fait tout planter
 - Lancer `tink sh` avec le tag --production plante si pas de package-lock.json, mais une fois lancer sans --production (ou via prepare sans --production), relancer avec --production ne plante pas si un module utilisé se trouve dans les devDependencies
