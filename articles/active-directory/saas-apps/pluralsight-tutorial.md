---
title: 'Didacticiel : Intégration de Pluralsight à Azure Active Directory | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et Pluralsight.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 4c3f07d2-4e1f-4ea3-9025-c663f1f2b7b4
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 12/18/2017
ms.author: jeedes
ms.openlocfilehash: 81f7e6f7610eb855bd4df1eaf45c6d016befc133
ms.sourcegitcommit: 1d850f6cae47261eacdb7604a9f17edc6626ae4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39443612"
---
# <a name="tutorial-azure-active-directory-integration-with-pluralsight"></a>Didacticiel : Intégration de Pluralsight à Azure Active Directory

Dans ce didacticiel, vous allez apprendre à intégrer Pluralsight à Azure AD (Azure Active Directory).

L’intégration de Pluralsight à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à Pluralsight.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à Pluralsight (via l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration de Pluralsight à Azure AD, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement Pluralsight pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de Pluralsight à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-pluralsight-from-the-gallery"></a>Ajout de Pluralsight à partir de la galerie
Pour configurer l’intégration de Pluralsight à Azure AD, vous devez ajouter Pluralsight depuis la galerie à votre liste d’applications SaaS gérées.

**Pour ajouter Pluralsight à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

1. Dans la zone de recherche, tapez **Pluralsight**, sélectionnez **Pluralsight** dans le volet de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![Pluralsight dans la liste des résultats](./media/pluralsight-tutorial/tutorial_pluralsight_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec Pluralsight avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur Pluralsight équivalent dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur Pluralsight associé doit être établie.

Dans Pluralsight, assignez la valeur de **nom d’utilisateur** dans Azure AD comme valeur de **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec Pluralsight, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Créer un utilisateur de test Pluralsight](#create-a-pluralsight-test-user)** pour obtenir un équivalent de Britta Simon dans Pluralsight lié à la représentation Azure AD associée.
1. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Tester l’authentification unique](#test-single-sign-on)** : pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application Pluralsight.

**Pour configurer l’authentification unique Azure AD avec Pluralsight, procédez comme suit :**

1. Dans le Portail Azure, sur la page d’intégration de l’application **Pluralsight**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Boîte de dialogue Authentification unique](./media/pluralsight-tutorial/tutorial_pluralsight_samlbase.png)

1. Dans la section **Domaine et URL Pluralsight**, suivez les étapes ci-dessous :

    ![Informations d’authentification unique dans Domaine et URL Pluralsight](./media/pluralsight-tutorial/tutorial_pluralsight_url.png)

    a. Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://<instancename>.pluralsight.com/sso/<companyname>`

    b. Dans la zone de texte **Identificateur**, tapez l’URL : `www.pluralsight.com`

    c. Dans la zone de texte **URL de réponse** , tapez une URL au format suivant : `https://<instancename>.pluralsight.com/sp/ACS.saml2`
     
    > [!NOTE] 
    > Il ne s’agit pas de valeurs réelles. Mettez à jour ces valeurs avec l’URL de réponse et l’URL de connexion réelles. Contactez [l’équipe de support client Pluralsight](mailto:support@pluralsight.com) pour obtenir ces valeurs. 

1. Dans la section **Certificat de signature SAML**, cliquez sur **Métadonnées XML** puis enregistrez le fichier de métadonnées sur votre ordinateur.

    ![Lien Téléchargement de certificat](./media/pluralsight-tutorial/tutorial_pluralsight_certificate.png) 

1. L’objectif de cette section est d’activer l’authentification unique Azure AD dans le portail Azure et de la configurer dans l’application Pluralsight.

    L’application Pluralsight s’attend à recevoir les assertions SAML dans un format spécifique, ce qui vous oblige à ajouter des mappages d’attributs personnalisés à votre configuration d’attributs de jeton SAML. La capture d’écran suivante montre un exemple :

    ![Configurer l'authentification unique](./media/pluralsight-tutorial/tutorial_pluralsight_attribute.png)

    >[!NOTE]
    >Vous pouvez également ajouter l’attribut **« Unique ID »** avec la valeur appropriée, comme EmployeeID ou autre valeur convenant à votre entreprise. Notez qu’il ne s’agit pas de l’attribut nécessaire, mais qu’il peut être ajouté pour l’identification de l’utilisateur unique. 

1. Pour ajouter les **Attributs du jeton SAML**requis, pour chaque ligne indiquée dans le tableau ci-dessous, procédez comme suit :
   
   | Nom de l'attribut | Valeur de l’attribut |
   | ---| --- |
   | Prénom |user.givenname |
   | Nom |user.surname |
   | Email |user.mail |
   
   a. Cliquez sur **add user attribute** to open the **Ajouter un attribut utilisateur** .
    
     ![Configurer l'authentification unique](./media/pluralsight-tutorial/tutorial_pluralsight_addattribute.png)
  
   b. Dans la zone de texte **Nom de l’attribut** , indiquez le nom d’attribut pour cette ligne.
  
   c. Dans la liste **Valeur de l’attribut** , sélectionnez la valeur d’attribut pour cette ligne.
  
   d. Cliquez sur **OK**.    

1. Cliquez sur le bouton **Enregistrer** .

    ![Configurer l'authentification unique](./media/pluralsight-tutorial/tutorial_general_400.png)

1. Pour obtenir la configuration de l’authentification unique pour votre application, contactez l’équipe [Services professionnels de Pluralsight](mailTo:professionalservices@pluralsight.com) et envoyez-lui le fichier de métadonnées téléchargé.

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Vous pouvez en savoir plus sur la fonctionnalité de documentation incorporée ici : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/pluralsight-tutorial/create_aaduser_01.png)

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/pluralsight-tutorial/create_aaduser_02.png)

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/pluralsight-tutorial/create_aaduser_03.png)

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/pluralsight-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="create-a-pluralsight-test-user"></a>Créer un utilisateur de test Pluralsight

L’objectif de cette section est de créer un utilisateur appelé Britta Simon dans Pluralsight. Contactez l’équipe du [support technique Pluralsight](mailto:support@pluralsight.com) pour ajouter des utilisateurs au compte Pluralsight.

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à Pluralsight.

![Attribuer le rôle utilisateur][200] 

**Pour affecter Britta Simon à Pluralsight, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **Pluralsight**.

    ![Lien Pluralsight dans la liste Applications](./media/pluralsight-tutorial/tutorial_pluralsight_app.png)  

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Quand vous cliquez sur la vignette Pluralsight dans le volet d’accès, vous êtes connecté automatiquement à votre application Pluralsight.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/pluralsight-tutorial/tutorial_general_01.png
[2]: ./media/pluralsight-tutorial/tutorial_general_02.png
[3]: ./media/pluralsight-tutorial/tutorial_general_03.png
[4]: ./media/pluralsight-tutorial/tutorial_general_04.png

[100]: ./media/pluralsight-tutorial/tutorial_general_100.png

[200]: ./media/pluralsight-tutorial/tutorial_general_200.png
[201]: ./media/pluralsight-tutorial/tutorial_general_201.png
[202]: ./media/pluralsight-tutorial/tutorial_general_202.png
[203]: ./media/pluralsight-tutorial/tutorial_general_203.png

