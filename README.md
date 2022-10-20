# map.tahiti.dev

Pour rajouter votre contact (vous n'y êtes pas obligé·e bien sûr), vous devez :

* Cloner ce repository
* Créer un fichier au format PRENOM-NOM.md dans le dossier `_members`
* Créer une PR

## Variables disponibles

| Variable                 | Format | Exemple                                           |
| ------------------------ | ------ | ------------------------------------------------- |
| `slack_account`          | String | leo                                               |
| `slack_account_url`      | String | https://tahitidevops.slack.com/team/U4R4LU6DC     |
| `stack_overflow_account` | String | https://stackoverflow.com/users/700317/teriiehina |
| `linkedin_account`       | String | teriiehina                                        |
| `contact_url`            | String | teriiehina                                        |
| `github_account`         | String | sitle                                             |
| `gitlab_account`         | String | sitle                                             |
| `twitter_account`        | String | leonardtavae                                      |

## Afficher le site sur votre machine

Vous avez peut-être envie de vérifier que vos modifications sont bien telles que vous l'espérez avant de soumettre une PR ?  Le site est généré avec [Jekyll](https://jekyllrb.com/), voici comment vous lancer :

Prérequis :

* [bundler](https://bundler.io/) (Généralement packagé dans votre distribution)

Note: Vous pouvez utiliser [rbenv](https://github.com/rbenv/rbenv) ou [RVM](https://rvm.io/rvm/install) si vous n'avez pas déjà un environnement Ruby fonctionnel ou si vous n'êtes pas administrateur·rice de votre machine.

```
$ git clone https://github.com/tahitidevops/map.tahiti.dev.git
$ cd map.tahiti.dev
$ bundle install
$ bundle exec jekyll serve
```

Voilà.
