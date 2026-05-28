## Display Builder with DSFR Recipe

This recipe extend Display builder Base recipe to provide a ready to use [DSFR](https://www.systeme-de-design.gouv.fr)
with Drupal experience.

---

## Version Française

### Introduction

Ui Suite DSFR est la solution Drupal pour implémenter le DSFR, le Design System de l'État français 🇫🇷. Ce thème implémente les composants, styles et icônes du DSFR. Notre solution est [**recommandée par le Service d'Information du Gouvernement (SIG)**](https://www.systeme-de-design.gouv.fr/version-courante/fr/communaute/portages-du-dsfr#drupal) et assure la conformité de l'interface utilisateur avec les standards de la marque de l'État. Ui Suite DSFR est utilisée dans de nombreuses administrations et est populaire auprès des agences Drupal.

Documentation Drupal sur les 'recipes' (en) :

- https://www.drupal.org/docs/extending-drupal/drupal-recipes
- https://project.pages.drupalcode.org/distributions_recipes/getting_started.html

## Installation

- Démarrer avec un site Druapl 11.3+

```shell
composer create-project drupal/recommended-project drupal_dsfr
cd drupal_dsfr
```

### DSFR avec Drupal

Installation librairie DSFR, voir [Documentation](https://git.drupalcode.org/project/ui_suite_dsfr/-/blob/1.x/README.md).

Résumé d'installation :

```shell
composer config repo.asset-packagist composer https://asset-packagist.org
composer config --merge --json extra.installer-types '["npm-asset"]'
composer config --merge --json extra.installer-paths '{"web/libraries/{$name}":["type:drupal-library"]}'
composer config --merge --json extra.installer-paths '{"web/libraries/dsfr":["npm-asset/gouvfr--dsfr"]}'
composer require oomphinc/composer-installers-extender:^2
composer require npm-asset/gouvfr--dsfr:^1.14
```

_Temporaire_, certains modules sont en version dev, il faut autoriser composer :

```shell
composer config minimum-stability dev
```

### Drupal `recipe`

Voir documentation d'[installation](https://project.pages.drupalcode.org/distributions_recipes/getting_started.html).

Résumé d'installation pour la préparation des recettes :

```shell
composer config allow-plugins.drupal/core-recipe-unpack true
composer require drupal/core-recipe-unpack
composer config --merge --json extra.installer-paths '{"recipes/{$name}":["type:drupal-recipe"]}'
echo '/recipes' >> .gitignore
```

Installer les `recipe` :

```shell
composer config repo.display_builder_base vcs https://github.com/mogtofu33/display-builder-base.git
composer config repo.display_builder_dsfr vcs https://github.com/mogtofu33/display-builder-dsfr.git
composer require drupal/display_builder_base:dev-main drupal/display_builder_dsfr:dev-main
```

### Installation Drupal

- Installer le profile 'Minimal'

Par exemple avec [DDEV](https://ddev.com) :

```shell
ddev config
ddev start
ddev drush si -y minimal
```

- Appliquer cette 'recipe'

Commande à exécuter :

```shell
php core/scripts/drupal recipe recipes/display_builder_dsfr
```

Ou avec [DDEV](https://ddev.com) `ddev exec`

```shell
ddev exec -d /var/www/html/web php core/scripts/drupal recipe /var/www/html/recipes/display_builder_dsfr
```

Si tout se passe bien un message s'affiche :

```shell
[OK] Display Builder with DSFR applied successfully
```

Importer les traductions avec Drush :

```shell
drush local:update
```

Ou avec [DDEV](https://ddev.com) `ddev exec`

```shell
ddev drush local:update
```

**Important** : Effacer le cache Drupal après l'application de la recette.

```shell
ddev drush cache:rebuild
```