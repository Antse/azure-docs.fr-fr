---
title: 'Tutoriel : Intégration d’Azure Active Directory à Manabi Pocket | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et Manabi Pocket.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 8e521099-bf7d-43ab-a0e0-86aa1c9e577e
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/20/2018
ms.author: jeedes
ms.openlocfilehash: 0116cac7d0e44efee0112d57aedd4f5ee02833b3
ms.sourcegitcommit: 1d850f6cae47261eacdb7604a9f17edc6626ae4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39430713"
---
# <a name="tutorial-azure-active-directory-integration-with-manabi-pocket"></a>Tutoriel : Intégration d’Azure Active Directory à Manabi Pocket

Dans ce tutoriel, vous allez apprendre à intégrer Manabi Pocket à Azure Active Directory (Azure AD).

L’intégration de Manabi Pocket à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à Manabi Pocket.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à Manabi Pocket (par le biais de l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration de Manabi Pocket à Azure AD, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Abonnement à Manabi Pocket avec authentification unique activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de Manabi Pocket à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-manabi-pocket-from-the-gallery"></a>Ajout de Manabi Pocket à partir de la galerie
Pour configurer l’intégration de Manabi Pocket à Azure AD, vous devez ajouter Manabi Pocket, disponible dans la galerie, à votre liste d’applications SaaS gérées.

**Pour ajouter Manabi Pocket à partir de la galerie, effectuez les étapes suivantes :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

1. Dans la zone de recherche, tapez **Manabi Pocket**, sélectionnez **Manabi Pocket** dans le panneau de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![Manabi Pocket dans la liste des résultats](./media/manabipocket-tutorial/tutorial_manabipocket_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD auprès de Manabi Pocket avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur Manabi Pocket équivalent dans Azure AD. En d’autres termes, une relation de lien entre un utilisateur Azure AD et un utilisateur Manabi Pocket associé doit être établie.

Pour configurer et tester l’authentification unique Azure AD auprès de Manabi Pocket, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Créer un utilisateur de test Manabi Pocket](#create-a-manabi-pocket-test-user)** pour avoir un équivalent de Britta Simon dans Manabi Pocket lié à la représentation Azure AD de l’utilisateur.
1. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Tester l’authentification unique](#test-single-sign-on)** : pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application Manabi Pocket.

**Pour configurer l’authentification unique Azure AD auprès de Manabi Pocket, effectuez les étapes suivantes :**

1. Dans le portail Azure, dans la page d’intégration de l’application **Manabi Pocket**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.

    ![Boîte de dialogue Authentification unique](./media/manabipocket-tutorial/tutorial_manabipocket_samlbase.png)

1. Dans la section **Domaine et URL Manabi Pocket**, suivez les étapes ci-dessous :

    ![Informations d’authentification unique dans Domaine et URL Manabi Pocket](./media/manabipocket-tutorial/tutorial_manabipocket_url.png)

    a. Dans la zone de texte **URL de connexion**, tapez l’URL : `https://ed-cl.com/`

    b. Dans la zone de texte **Identificateur**, tapez une URL au format suivant : `https://<SERVER-NAME>.ed-cl.com/<TENANT-ID>/idp/provider`

    > [!NOTE]
    > La valeur de l'identificateur n'est pas réelle. Mettez-la à jour avec l’identificateur réel. Pour obtenir cette valeur, contactez l’[équipe de support technique Manabi Pocket](mailto:info-ed-cl@ntt.com).

1. Dans la section **Certificat de signature SAML**, cliquez sur **Métadonnées XML** puis enregistrez le fichier de métadonnées sur votre ordinateur.

    ![Lien Téléchargement de certificat](./media/manabipocket-tutorial/tutorial_manabipocket_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Bouton Enregistrer de la page Configurer l’authentification unique](./media/manabipocket-tutorial/tutorial_general_400.png)

1. Pour configurer l’authentification unique côté **Manabi Pocket**, vous devez envoyer le **XML de métadonnées** téléchargé à [l’équipe de support technique Manabi Pocket](mailto:info-ed-cl@ntt.com). Celles-ci configurent ensuite ce paramètre pour que la connexion SSO SAML soit définie correctement des deux côtés.

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/manabipocket-tutorial/create_aaduser_01.png)

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/manabipocket-tutorial/create_aaduser_02.png)

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/manabipocket-tutorial/create_aaduser_03.png)

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/manabipocket-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="create-a-manabi-pocket-test-user"></a>Créer un utilisateur de test Manabi Pocket

Dans cette section, vous allez créer un utilisateur appelé Britta Simon dans Manabi Pocket. Contactez l’[équipe de support technique Manabi Pocket](mailto:info-ed-cl@ntt.com) pour ajouter les utilisateurs à la plateforme Manabi Pocket. Les utilisateurs doivent être créés et activés avant que vous utilisiez l’authentification unique.

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à Manabi Pocket.

![Attribuer le rôle utilisateur][200] 

**Pour affecter Britta Simon à Manabi Pocket, effectuez les étapes suivantes :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **Manabi Pocket**.

    ![Lien Manabi Pocket dans la liste des applications](./media/manabipocket-tutorial/tutorial_manabipocket_app.png)  

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.

### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Quand vous cliquez sur la vignette Manabi Pocket dans le volet d’accès, vous devez être connecté automatiquement à votre application Manabi Pocket.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/manabipocket-tutorial/tutorial_general_01.png
[2]: ./media/manabipocket-tutorial/tutorial_general_02.png
[3]: ./media/manabipocket-tutorial/tutorial_general_03.png
[4]: ./media/manabipocket-tutorial/tutorial_general_04.png

[100]: ./media/manabipocket-tutorial/tutorial_general_100.png

[200]: ./media/manabipocket-tutorial/tutorial_general_200.png
[201]: ./media/manabipocket-tutorial/tutorial_general_201.png
[202]: ./media/manabipocket-tutorial/tutorial_general_202.png
[203]: ./media/manabipocket-tutorial/tutorial_general_203.png