---
title: Prévention des attaques par force brute avec le verrouillage intelligent Azure AD
description: Le verrouillage intelligent d’Azure Active Directory permet de protéger votre organisation contre les attaques par force brute visant à deviner vos mots de passe.
services: active-directory
ms.service: active-directory
ms.component: authentication
ms.topic: conceptual
ms.date: 12/14/2018
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.reviewer: rogoya
ms.openlocfilehash: 9f701f0f6d00d2913eaf5b237435fd375b2030e0
ms.sourcegitcommit: c2e61b62f218830dd9076d9abc1bbcb42180b3a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53435274"
---
# <a name="azure-active-directory-smart-lockout"></a>Verrouillage intelligent Azure Active Directory

Le verrouillage intelligent empêche les personnes malveillantes de deviner vos mots de passe ou d’utiliser des méthodes de force brute pour rentrer dans vos systèmes. Il peut reconnaître les connexions provenant d’utilisateurs validés et les traiter différemment de celles des attaquants et autres sources inconnues. Le verrouillage intelligent empêche les attaquants de pénétrer dans le système, tout en permettant à vos utilisateurs d’accéder à leurs comptes et de travailler.

Par défaut, le verrouillage intelligent empêche les tentatives de connexion au compte pendant une minute après 10 tentatives infructueuses. Le compte se verrouille à nouveau après chaque échec de connexion consécutif. Le premier verrouillage dure une minute, les suivants durent plus longtemps.

Le verrouillage intelligent effectue le suivi des trois derniers hachages de mots de passe incorrects pour éviter de réincrémenter le compteur de verrouillages. Si un utilisateur entre plusieurs fois le même mot de passe incorrect, le compte n'est pas verrouillé.

 > [!NOTE]
 > La fonctionnalité de suivi du hachage n’est pas disponible pour les clients sur lesquels l’authentification directe est activée dans la mesure où l’authentification est effectuée localement et pas dans le cloud.

Le verrouillage intelligent est activé en permanence pour les clients Azure AD disposant des paramètres par défaut qui offrent la combinaison idéale de sécurité et de facilité d’utilisation. Pour personnaliser les paramètres de verrouillage intelligent en vue de répondre aux besoins de votre organisation, vos utilisateurs doivent disposer d’une licence Azure AD Basic ou plus élevée.

L'utilisation du verrouillage intelligent ne garantit pas qu'un véritable utilisateur ne sera jamais verrouillé. Lorsque le verrouillage intelligent verrouille un compte d'utilisateur, nous mettons tout en œuvre pour ne pas verrouiller le véritable utilisateur. Le service de verrouillage veille à ce que des personnes mal intentionnées n’aient pas accès au compte d’un véritable utilisateur.  

* Chaque centre de données Azure Active Directory assure indépendamment le suivi des verrouillages. Un utilisateur disposera d'un nombre de tentatives de (seuil_limite x nombre_de_centres_de_données) s'il atteint chaque centre de données.
* Le verrouillage intelligent utilise un emplacement familier par opposition à un emplacement inconnu pour faire la différence entre une personne mal intentionnée et un véritable utilisateur. Les emplacements familiers et inconnus disposent tous deux de compteurs de verrouillages distincts.

Le verrouillage intelligent peut être intégré aux déploiements hybrides à l’aide de la synchronisation du hachage de mot de passe ou de l’authentification directe, en vue d’empêcher les comptes Active Directory locaux d’être verrouillés par les attaquants. En définissant les stratégies de verrouillage intelligent nécessaires dans Azure AD, vous pouvez bloquer les attaques avant même qu’elles atteignent l’instance locale d’Active Directory.

Lorsque vous utilisez [l’authentification directe](../hybrid/how-to-connect-pta.md), vous devez vérifier que :

   * Le seuil de verrouillage d’Azure AD est **inférieur** au seuil de verrouillage de compte Active Directory. Définissez les valeurs de sorte que le seuil de verrouillage de compte Active Directory soit au moins deux ou trois fois supérieur au seuil de verrouillage d’Azure AD. 
   * La durée de verrouillage d’Azure AD, **exprimée en secondes**, est **plus longue** que la durée après laquelle réinitialiser le compteur de verrouillage de compte Active Directory, **exprimée en minutes**.

> [!IMPORTANT]
> Actuellement, un administrateur ne peut pas déverrouiller les comptes cloud des utilisateurs si ceux-ci ont été verrouillés à l’aide de la fonctionnalité Verrouillage intelligent. L’administrateur doit attendre que la durée de verrouillage expire.

## <a name="verify-on-premises-account-lockout-policy"></a>Vérifier la stratégie de verrouillage d’un compte local

Utilisez les instructions suivantes pour vérifier les stratégies de verrouillage de votre compte local Active Directory :

1. Ouvrez l’outil de gestion de stratégie de groupe.
2. Modifiez la stratégie de groupe qui comprend la stratégie de verrouillage de compte de votre organisation, par exemple, la **stratégie de domaine par défaut**.
3. Accédez à **Configuration de l’ordinateur** > **Stratégies** > **Paramètres Windows** > **Paramètres de sécurité** > **Stratégies de compte** > **Stratégie de verrouillage de compte**.
4. Vérifiez vos valeurs de **Seuil de verrouillage de compte** et **Réinitialiser le compteur de verrouillage de compte après**.

![Modifier la stratégie de verrouillage des comptes locaux Active Directory à l’aide d’un objet de stratégie de groupe](./media/howto-password-smart-lockout/active-directory-on-premises-account-lockout-policy.png)

## <a name="manage-azure-ad-smart-lockout-values"></a>Gérer les valeurs du verrouillage intelligent Azure AD

En fonction des besoins de votre organisation, les valeurs de verrouillage intelligent peuvent nécessiter une personnalisation. Pour personnaliser les paramètres de verrouillage intelligent en vue de répondre aux besoins de votre organisation, vos utilisateurs doivent disposer d’une licence Azure AD Basic ou plus élevée.

Pour vérifier ou modifier les valeurs de verrouillage intelligent de votre organisation, procédez aux étapes suivantes :

1. Connectez-vous au [portail Azure](https://portal.azure.com), et cliquez sur **Azure Active Directory**, puis sur **Méthodes d’authentification**.
1. Définissez le **Seuil de verrouillage**, c’est-à-dire le nombre d’échecs de connexions autorisé avant qu’un compte ne soit verrouillé. La valeur par défaut est de 10.
1. Définissez la **Durée du verrouillage en secondes** sur la durée en secondes souhaitée de chaque verrouillage. La valeur par défaut est 60 secondes (une minute).

> [!NOTE]
> Si la première connexion après verrouillage échoue également, le compte est de nouveau verrouillé. Si un compte est verrouillé à plusieurs reprises, la durée de verrouillage augmente.

![Personnaliser la stratégie de verrouillage intelligent Azure AD dans le portail Azure](./media/howto-password-smart-lockout/azure-active-directory-custom-smart-lockout-policy.png)
## <a name="next-steps"></a>Étapes suivantes

[Découvrez comment interdire les mots de passe incorrects dans votre organisation à l’aide d’Azure AD](howto-password-ban-bad.md)

[Configurez la réinitialisation de mot de passe libre-service pour permettre aux utilisateurs de déverrouiller leur compte.](quickstart-sspr.md)