---
author: rothja
ms.service: billing
ms.topic: include
ms.date: 11/09/2018
ms.author: jroth
ms.openlocfilehash: efa367157a8fd896cdc9680bf2ab6ba6a9e3dbb0
ms.sourcegitcommit: b254db346732b64678419db428fd9eb200f3c3c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53429959"
---
Transactions de clé (transactions maximales autorisées dans les 10 secondes, par coffre par région<sup>1</sup>) :

|Type de clé|Clé HSM<br>Clé CREATE|Clé HSM<br>Toutes les autres transactions|Clé logicielle<br>Clé CREATE|Clé logicielle<br>Toutes les autres transactions|
|:---|---:|---:|---:|---:|
|RSA 2 048 bits|5.|1 000|10|2000|
|RSA 3 072 bits|5.|250|10|500|
|RSA 4 096 bits|5.|125|10|250|
|ECC P-256|5.|1 000|10|2000|
|ECC P-384|5.|1 000|10|2000|
|ECC P-521|5.|1 000|10|2000|
|ECC SECP256K1|5.|1 000|10|2000|
|

> [!NOTE]
> En examinant le tableau ci-dessous, vous constatez que pour les clés logicielles nous autorisons 2000 transactions toutes les 10 secondes, et que pour les clés HSM nous autorisons 1000 transactions toutes les 10 secondes. Le rapport des transactions logicielles pour les clés 3072 à 2048 est de 500/2000 ou 0.4. Cela signifie que si un client effectue 500 transactions de clés 3072 en 10 secondes, il atteint la limite maximale et il ne peut plus effectuer d’autres opérations de clé. 
   
|Type de clé  | Clé logicielle |Clé HSM  |
|---------|---------|---------|
|RSA 2 048 bits     |    2000     |   1 000    |
|RSA 3 072 bits     |     500    |    250     |
|RSA 4 096 bits     |    125     |    250     |
|ECC P-256     |    2000     |  1 000     |
|ECC P-384     |    2000     |  1 000     |
|ECC P-521     |    2000     |  1 000     |
|ECC SECP256K1     |    2000     |  1 000     |


Secrets, clés de compte de stockage géré et transactions de coffre :
| Type de transaction | Transactions maximales autorisées dans les 10 secondes, par coffre par région<sup>1</sup> |
| --- | --- |
| Toutes les transactions |2000 |
|

Consultez la page [Aide sur la limitation de requêtes Azure Key Vault](../articles/key-vault/key-vault-ovw-throttling.md) pour plus d’informations sur la façon de gérer la limitation en cas de dépassement de ces limites.

<sup>1</sup> La limite d’abonnement pour tous les types de transaction est fixée à 5x par limite de coffre de clés. Par exemple, HSM - autres transactions par abonnement sont limitées à 5000 transactions en 10 secondes par abonnement.
