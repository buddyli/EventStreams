---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Qu'est-ce que {{site.data.keyword.messagehub}} ?
{: #about}

{{site.data.keyword.messagehub_full}} est un bus de messages à haute capacité généré avec Apache Kafka. Il est optimisé pour l'ingestion d'événements dans {{site.data.keyword.Bluemix_notm}} et la distribution de flux d'événements dans des services et des applications. {{site.data.keyword.messagehub}} était auparavant connu sous le nom de Message Hub.
{: shortdesc}

Vous pouvez utiliser {{site.data.keyword.messagehub}} pour effectuer les tâches suivantes :

* Décharger des travaux vers des processus d'agent de back end.
* Connecter des données de flux à des fonctions d'analyse pour en tirer des informations importantes.
* Publier des données d'événement sur plusieurs applications pour qu'elles réagissent en temps réel.
* Transférer des données vers un autre service, par exemple, le stockage à long terme.

Etant généré avec Apache Kafka, il bénéficie directement de toutes les innovations qui voient le jour dans la communauté et prend en charge des API de client Kafka, Kafka Streams, Kafka Connect et également KSQL.
{:shortdesc}

En général, les outils Apache Kafka fonctionnent directement avec {{site.data.keyword.messagehub}}, mais vous devez cependant fournir une configuration supplémentaire car les connexions à {{site.data.keyword.messagehub}} sont toujours authentifiées à l'aide de données d'identification.

Dans {{site.data.keyword.messagehub}}, les applications envoient des données en créant un message et en l'envoyant à un sujet. Pour recevoir des messages, les applications s'abonnent à un sujet et choisissent de recevoir tous les messages du sujet ou de partager les messages entre elles. {{site.data.keyword.messagehub}} héberge et gère les messages dans un ordre précis. 




