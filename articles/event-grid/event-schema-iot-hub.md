---
title: Schéma Azure Event Grid pour IoT Hub | Microsoft Docs
description: Page de référence pour le format de schéma des événements et les propriétés d’IoT Hub
services: iot-hub
documentationcenter: ''
author: kgremban
manager: timlt
editor: ''
ms.service: event-grid
ms.topic: reference
ms.date: 08/17/2018
ms.author: kgremban
ms.openlocfilehash: a86b22b3327b2353dd37a9f9863337d12a009434
ms.sourcegitcommit: a1140e6b839ad79e454186ee95b01376233a1d1f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43143571"
---
# <a name="azure-event-grid-event-schema-for-iot-hub"></a>Schéma des événements Azure Event Grid pour IoT Hub

Cet article fournit les propriétés et les schémas des événements IoT Hub. Pour une présentation des schémas d’événements, consultez [Schéma d’événements Azure Event Grid](event-schema.md). 

Pour obtenir la liste des exemples de scripts et des didacticiels, consultez [Source d’événement IoT Hub](event-sources.md#iot-hub).

## <a name="available-event-types"></a>Types d’événement disponibles

IoT Hub émet les types d’événements suivants :

| Type d'événement | Description |
| ---------- | ----------- |
| Microsoft.Devices.DeviceCreated | Publié quand un appareil est inscrit auprès d’un hub IoT. |
| Microsoft.Devices.DeviceDeleted | Publié quand un appareil est supprimé d’un hub IoT. | 
| Microsoft.Devices.DeviceConnected | Publié quand un appareil est connecté à un hub IoT. |
| Microsoft.Devices.DeviceDisconnected | Publié quand un appareil est déconnecté d’un hub IoT. | 

## <a name="example-event"></a>Exemple d’événement

Les schémas pour les événements DeviceConnected et DeviceDisconnected ont la même structure. Cet exemple d’événement montre le schéma d’un événement déclenché quand un appareil est connecté à un hub IoT :

```json
[{
  "id": "f6bbf8f4-d365-520d-a878-17bf7238abd8", 
  "topic": "/SUBSCRIPTIONS/<subscription ID>/RESOURCEGROUPS/<resource group name>/PROVIDERS/MICROSOFT.DEVICES/IOTHUBS/<hub name>", 
  "subject": "devices/LogicAppTestDevice", 
  "eventType": "Microsoft.Devices.DeviceConnected", 
  "eventTime": "2018-06-02T19:17:44.4383997Z", 
  "data": {
    "deviceConnectionStateEventInfo": {
      "sequenceNumber":
        "000000000000000001D4132452F67CE200000002000000000000000000000001"
    },
    "hubName": "egtesthub1",
    "deviceId": "LogicAppTestDevice",
    "moduleId" : "DeviceModuleID"
  }, 
  "dataVersion": "1", 
  "metadataVersion": "1" 
}]
```

Les schémas pour les événements DeviceCreated et DeviceDeleted ont la même structure. Cet exemple d’événement montre le schéma d’un événement déclenché quand un appareil est inscrit auprès d’un hub IoT :

```json
[{
  "id": "56afc886-767b-d359-d59e-0da7877166b2",
  "topic": "/SUBSCRIPTIONS/<subscription ID>/RESOURCEGROUPS/<resource group name>/PROVIDERS/MICROSOFT.DEVICES/IOTHUBS/<hub name>",
  "subject": "devices/LogicAppTestDevice",
  "eventType": "Microsoft.Devices.DeviceCreated",
  "eventTime": "2018-01-02T19:17:44.4383997Z",
  "data": {
    "twin": {
      "deviceId": "LogicAppTestDevice",
      "etag": "AAAAAAAAAAE=",
      "deviceEtag": "null",
      "status": "enabled",
      "statusUpdateTime": "0001-01-01T00:00:00",
      "connectionState": "Disconnected",
      "lastActivityTime": "0001-01-01T00:00:00",
      "cloudToDeviceMessageCount": 0,
      "authenticationType": "sas",
      "x509Thumbprint": {
        "primaryThumbprint": null,
        "secondaryThumbprint": null
      },
      "version": 2,
      "properties": {
        "desired": {
          "$metadata": {
            "$lastUpdated": "2018-01-02T19:17:44.4383997Z"
          },
          "$version": 1
        },
        "reported": {
          "$metadata": {
            "$lastUpdated": "2018-01-02T19:17:44.4383997Z"
          },
          "$version": 1
        }
      }
    },
    "hubName": "egtesthub1",
    "deviceId": "LogicAppTestDevice"
  },
  "dataVersion": "1",
  "metadataVersion": "1"
}]
```

### <a name="event-properties"></a>Propriétés d’événement

Tous les événements contiennent les mêmes données de niveau supérieur : 

| Propriété | type | Description |
| -------- | ---- | ----------- |
| id | chaîne | Identificateur unique de l’événement. |
| rubrique | chaîne | Chemin d’accès complet à la source de l’événement. Ce champ n’est pas modifiable. Event Grid fournit cette valeur. |
| subject | chaîne | Chemin de l’objet de l’événement, défini par le serveur de publication. |
| eventType | chaîne | Un des types d’événements inscrits pour cette source d’événement. |
| eventTime | chaîne | L’heure à quelle l’événement est généré selon l’heure UTC du fournisseur. |
| données | objet | Données d’événement IoT Hub.  |
| dataVersion | chaîne | Version du schéma de l’objet de données. Le serveur de publication définit la version du schéma. |
| metadataVersion | chaîne | Version du schéma des métadonnées d’événement. Event Grid définit le schéma des propriétés de niveau supérieur. Event Grid fournit cette valeur. |

Pour tous les événements IoT Hub, l’objet de données contient les propriétés suivantes :

| Propriété | type | Description |
| -------- | ---- | ----------- |
| hubName | chaîne | Nom du hub IoT où l’appareil a été créé ou supprimé. |
| deviceId | chaîne | Identificateur unique de l’appareil. Cette chaîne qui respecte la casse peut contenir jusqu’à 128 caractères et prend en charge les caractères alphanumériques 7 bits ASCII, ainsi que les caractères spéciaux suivants :`- : . + % _ # * ? ! ( ) , = @ ; $ '`. |

Le contenu de l’objet de données est différent pour chaque serveur de publication d’événements. Pour les événements IoT Hub **DeviceConnected** et **DeviceDisconnected**, l’objet de données contient les propriétés suivantes :

| Propriété | type | Description |
| -------- | ---- | ----------- |
| moduleId | chaîne | Identificateur unique du module. Ce champ est sorti uniquement pour les appareils de module. Cette chaîne qui respecte la casse peut contenir jusqu’à 128 caractères et prend en charge les caractères alphanumériques 7 bits ASCII, ainsi que les caractères spéciaux suivants :`- : . + % _ # * ? ! ( ) , = @ ; $ '`. |
| deviceConnectionStateEventInfo | objet | Informations d’événement sur l’état de connexion d’appareil
| sequenceNumber | chaîne | Un numéro qui vous aide à indiquer l’ordre des événements de connexion et de déconnexion d’appareils. Le dernier événement aura un numéro de séquence plus élevé que l’événement précédent. Ce numéro peut changer de plus d’une unité, mais il ne peut qu’augmenter. Consultez [comment utiliser le numéro de séquence](../iot-hub/iot-hub-how-to-order-connection-state-events.md). |

Le contenu de l’objet de données est différent pour chaque serveur de publication d’événements. Pour les événements IoT Hub **DeviceCreated** et **DeviDeleted**, l’objet de données contient les propriétés suivantes :

| Propriété | type | Description |
| -------- | ---- | ----------- |
| twin | objet | Informations sur le jumeau d’appareil, qui est la représentation cloud des métadonnées d’appareil de l’application. | 
| deviceID | chaîne | Identificateur unique du jumeau d’appareil. | 
| etag | chaîne | Un validateur pour garantir la cohérence des mises à jour à un jumeau d'appareil. Chaque etag est unique pour chaque jumeau d’appareil. |  
| deviceEtag| chaîne | Un validateur pour garantir la cohérence des mises à jour à un registre d'appareil. Chaque deviceEtag est unique pour chaque registre d’appareil. |
| status | chaîne | Indique si le jumeau d’appareil est activé ou désactivé. | 
| statusUpdateTime | chaîne | Horodatage ISO8601 de la dernière mise à jour de l’état du jumeau d’appareil. |
| connectionState | chaîne | Indique si l’appareil est connecté ou déconnecté. | 
| lastActivityTime | chaîne | Horodatage ISO8601 de la dernière activité. | 
| cloudToDeviceMessageCount | integer | Nombre de messages cloud-à-appareil envoyés à cet appareil. | 
| authenticationType | chaîne | Type d’authentification utilisé pour cet appareil : `SAS`, `SelfSigned` ou `CertificateAuthority`. |
| x509Thumbprint | chaîne | L’empreinte numérique est une valeur unique pour le certificat x509, et sert généralement à rechercher un certificat particulier dans un magasin de certificats. L’empreinte numérique, générée dynamiquement à l’aide de l’algorithme SHA-1, n’existe pas physiquement dans le certificat. | 
| primaryThumbprint | chaîne | Empreinte numérique principale pour le certificat x509. |
| secondaryThumbprint | chaîne | Empreinte numérique secondaire pour le certificat x509. | 
| version | integer | Entier qui est incrémenté chaque fois que le jumeau d’appareil est mis à jour. |
| desired | objet | Une partie des propriétés qui peuvent être écrites uniquement par le backend d’application et lues par l’appareil. | 
| reported | objet | Une partie des propriétés qui peuvent être écrites uniquement par l’appareil et lues par le backend d’application. |
| lastUpdated | chaîne | Horodatage ISO8601 de la dernière mise à jour de la propriété du jumeau d’appareil. | 

## <a name="next-steps"></a>Étapes suivantes

* Pour une présentation d’Azure Event Grid, consultez [Présentation d’Event Grid](overview.md).
* Pour en savoir plus sur le fonctionnement conjoint d’IoT Hub et d’Event Grid, consultez [Réagir aux événements IoT Hub en utilisant Event Grid pour déclencher des actions](../iot-hub/iot-hub-event-grid.md).