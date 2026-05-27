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
- Installer le profile 'Minimal'
- Appliquer cette 'recipe'

Commande à exécuter :

```shell
php core/scripts/drupal recipe recipes/contrib/display_builder_dsfr
```

Ou avec [DDEV](https://ddev.com) `ddev exec`

```shell
ddev exec -d /var/www/html/docroot php core/scripts/drupal recipe recipes/contrib/display_builder_dsfr
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
