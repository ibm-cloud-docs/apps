---

copyright:
  years: 2015, 2017, 2018
lastupdated: "2018-05-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Vérification du statut d'une application
{: #manageapps}

Le tableau de bord de la console {{site.data.keyword.Bluemix}} fournit des informations récapitulatives sur les applications que vous avez créées. Ces informations récapitulatives incluent le nom, l'icône, l'URL, le contexte d'exécution, le statut d'exécution, ainsi que les instances de service liées à l'application.
{:shortdesc}

## Comprendre le statut d'une application
{: #status}

Depuis le tableau de bord, vous pouvez afficher le statut de chaque application. La colonne d'état de chaque application vous pouvez de voir si les instances de cette application sont en cours d'exécution.

<dl>
<dt>
<strong>
Arrêté ou Inconnu (gris)
</strong>
</dt>
<dd>
Votre application est arrêtée ou le statut est Inconnu. L'icône grise indique que l'application est arrêtée ou que le statut est inconnu.
</dd>
<dt>
<strong>
En cours d'exécution (vert)
</strong>
</dt>
<dd>
Votre application est en cours d'exécution. L'icône verte indique que l'application est démarrée et que toutes les instances sont en cours d'exécution.
</dd>
<dt>
<strong>
_Nombre_ en cours d'exécution (jaune)
</strong>
</dt>
<dd>
L'application est démarrée mais toutes les instances ne sont pas en cours d'exécution. L'icône jaune indique que moins de 100% des instances sont
en cours d'exécution. Le nombre d'instances en cours d'exécution et le nombre
d'instances ayant échoué sont affichés.
</dd>
<dt>
<strong>
Pas en cours d'exécution (rouge)
</strong>
</dt>
<dd>
Votre application n'est pas en cours d'exécution. L'icône rouge indique que l'application est démarrée mais qu'aucune instance n'est en cours d'exécution.
</dd>
</dl>

## Affichage du tableau de bord des détails d'application
{: #viewingapps}

Vous pouvez afficher des informations sur une application en cliquant sur son nom dans votre tableau de bord. Ensuite, vous pouvez afficher la page Vue d'ensemble de l'application.

Sur la page Vue d'ensemble de l'application, une fois l'application déployée, vous pouvez démarrer, arrêter, redémarrer ou, dans le cas d'applications Web, modifier le nombre d'instances et la quantité de mémoire utilisée par l'application. Pour les applications Web, {{site.data.keyword.Bluemix_notm}} n'ajuste pas automatiquement votre application en fonction de sa charge, et vous devez donc gérer cet aspect vous-même.

Si une mise à jour est effectuée, les applications peuvent être redéployées. Le mécanisme de mise à jour de l'application est identique au mécanisme utilisé pour déployer initialement l'application. {{site.data.keyword.Bluemix_notm}}
arrête toutes les instances en cours d'exécution et les remplace automatiquement par de nouvelles instances.
