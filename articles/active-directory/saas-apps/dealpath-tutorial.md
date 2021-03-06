---
title: 'Didacticiel : Intégration d’Azure Active Directory avec Dealpath | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et Dealpath.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 51ace608-5a4f-48c0-9446-d9f86ad2e890
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 12/11/2017
ms.author: jeedes
ms.openlocfilehash: 8fa9014ec066e888e9c5cc9330d76c2487786530
ms.sourcegitcommit: 1d850f6cae47261eacdb7604a9f17edc6626ae4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39427698"
---
# <a name="tutorial-azure-active-directory-integration-with-dealpath"></a>Didacticiel : Intégration d’Azure AD avec Dealpath

Dans ce didacticiel, vous allez apprendre à intégrer Dealpath à Azure Active Directory (Azure AD).

L’intégration de Dealpath à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à Dealpath.
- Vous pouvez autoriser vos utilisateurs à se connecter automatiquement à Dealpath (via l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD avec Dealpath, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement Dealpath pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de Dealpath à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-dealpath-from-the-gallery"></a>Ajout de Dealpath à partir de la galerie
Pour configurer l’intégration de Dealpath à Azure AD, vous devez ajouter Dealpath à partir de la galerie à votre liste d’applications SaaS gérées.

**Pour ajouter Dealpath à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

1. Dans la zone de recherche, tapez **Dealpath**, sélectionnez **Dealpath** dans le volet de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![Dealpath dans la liste des résultats](./media/dealpath-tutorial/tutorial_dealpath_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec Dealpath, avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur Dealpath équivalent dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur Dealpath associé doit être établie.

Dans Dealpath, assignez la valeur de **nom d’utilisateur** dans Azure AD comme valeur de **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec Dealpath, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Créer utilisateur de test Dealpath](#create-a-dealpath-test-user)** pour avoir un équivalent de Britta Simon dans Dealpath lié à la représentation Azure AD associée.
1. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Tester l’authentification unique](#test-single-sign-on)** : pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application Dealpath.

**Pour configurer l'authentification unique Azure AD avec Dealpath, procédez comme suit :**

1. Dans le portail Azure, sur la page d’intégration de l’application **Dealpath**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Boîte de dialogue Authentification unique](./media/dealpath-tutorial/tutorial_dealpath_samlbase.png)

1. Dans la section **Domaine et URL Dealpath**, procédez comme suit :

    ![Informations d’authentification unique dans Domaine et URL Dealpath](./media/dealpath-tutorial/tutorial_dealpath_url.png)

    a. Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://app.dealpath.com/account/login`

    b. Dans la zone de texte **Identificateur**, tapez une URL au format suivant : `https://api.dealpath.com/saml/metadata/<ID>`

    > [!NOTE] 
    > L'identificateur n'est pas réel. Mettez à jour cette valeur avec l’identificateur réel. Pour obtenir cette valeur, contactez [l’équipe du support technique Dealpath](mailto:kenter@dealpath.com). 
 
1. Dans la section **Certificat de signature SAML**, cliquez sur **Téléchargez le certificat (Base64)**, puis enregistrez le fichier du certificat sur votre ordinateur.

    ![Lien Téléchargement de certificat](./media/dealpath-tutorial/tutorial_dealpath_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Bouton Enregistrer de la page Configurer l’authentification unique](./media/dealpath-tutorial/tutorial_general_400.png)

1. Dans la section **Configuration de Dealpath**, cliquez sur **Configurer Dealpath** pour ouvrir la fenêtre **Configurer l’authentification**. Copiez l’**ID d’entité SAML et l’URL du service d’authentification unique SAML** à partir de la **section Référence rapide.**

    ![Configuration de Dealpath](./media/dealpath-tutorial/tutorial_dealpath_configure.png) 

1. Dans une autre fenêtre de navigateur web, connectez-vous à Dealpath en tant qu’administrateur.

1. Dans l’angle supérieur droit, cliquez sur **Outils d’administration** et sélectionnez **Intégrations**, puis dans la section **SAML 2.0 Authentication**, cliquez sur **Mettre à jour les paramètres** :

    ![Configuration de Dealpath](./media/dealpath-tutorial/tutorial_dealpath_admin.png)

1. Dans la page **SAML 2.0 Authentication**, procédez comme suit :

    ![Configuration de Dealpath](./media/dealpath-tutorial/tutorial_dealpath_saml.png) 

    a. Dans la zone de texte **URL SAML SSO**, collez la valeur de **l’URL du service d’authentification unique SAML** que vous avez copiée sur le portail Azure.

    b. Dans la zone de texte **Émetteur du fournisseur d’identité**, collez la valeur de l’**ID d’entité SAML** copié à partir du portail Azure.

    c. Copiez le contenu du certificat téléchargé dans le fichier **certificate(Base64)**, puis collez-le dans la zone de texte **Certificat public**.

    d. Cliquez sur **Mettre à jour les paramètres**.


> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Vous pouvez en savoir plus sur la fonctionnalité de documentation incorporée ici : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/dealpath-tutorial/create_aaduser_01.png)

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/dealpath-tutorial/create_aaduser_02.png)

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/dealpath-tutorial/create_aaduser_03.png)

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/dealpath-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="create-a-dealpath-test-user"></a>Créer un utilisateur de test Dealpath

Dans cette section, vous allez créer un utilisateur appelé Britta Simon dans Dealpath. Collaborez avec l’[équipe du support technique Dealpath](mailto:kenter@dealpath.com) pour ajouter des utilisateurs sur la plateforme Dealpath. Les utilisateurs doivent être créés et activés avant que vous utilisiez l’authentification unique.

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à Dealpath.

![Attribuer le rôle utilisateur][200] 

**Pour affecter Britta Simon à Dealpath, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **Dealpath**.

    ![Lien Dealpath dans la liste des applications](./media/dealpath-tutorial/tutorial_dealpath_app.png)  

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la mosaïque Dealpath dans le volet d’accès, vous devez être connecté automatiquement à votre application Dealpath.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/dealpath-tutorial/tutorial_general_01.png
[2]: ./media/dealpath-tutorial/tutorial_general_02.png
[3]: ./media/dealpath-tutorial/tutorial_general_03.png
[4]: ./media/dealpath-tutorial/tutorial_general_04.png

[100]: ./media/dealpath-tutorial/tutorial_general_100.png

[200]: ./media/dealpath-tutorial/tutorial_general_200.png
[201]: ./media/dealpath-tutorial/tutorial_general_201.png
[202]: ./media/dealpath-tutorial/tutorial_general_202.png
[203]: ./media/dealpath-tutorial/tutorial_general_203.png

