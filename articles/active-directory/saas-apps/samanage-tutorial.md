---
title: 'Didacticiel : Intégration d’Azure Active Directory avec Samanage | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et Samanage.
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.assetid: f0db4fb0-7eec-48c2-9c7a-beab1ab49bc2
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/05/2017
ms.author: jeedes
ms.openlocfilehash: 118ab72c9afc13c5792f229f9c7bc61d226553d5
ms.sourcegitcommit: 1d850f6cae47261eacdb7604a9f17edc6626ae4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39420572"
---
# <a name="tutorial-azure-active-directory-integration-with-samanage"></a>Didacticiel : Intégration d’Azure Active Directory à Samanage

Dans ce didacticiel, vous allez apprendre à intégrer Samanage avec Azure Active Directory (Azure AD).

L’intégration de Samanage à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à Samanage.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à Samanage (par le biais de l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes à partir d’un emplacement central : le portail Azure.

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD à Samanage, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement Samanage pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez obtenir un essai d’un mois [ici](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de Samanage à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-samanage-from-the-gallery"></a>Ajout de Samanage à partir de la galerie
Pour configurer l’intégration de Samanage à Azure AD, vous devez ajouter Samanage à partir de la galerie à votre liste d’applications SaaS gérées.

**Pour ajouter Samanage à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![APPLICATIONS][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![APPLICATIONS][3]

1. Dans la zone de recherche, tapez **Samanage**.

    ![Création d’un utilisateur de test Azure AD](./media/samanage-tutorial/tutorial_samanage_search.png)

1. Dans le volet de résultats, sélectionnez **Samanage**, puis cliquez sur **Ajouter** pour ajouter l’application.

    ![Création d’un utilisateur de test Azure AD](./media/samanage-tutorial/tutorial_samanage_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configuration et test de l’authentification unique Azure AD
Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec Samanage sur un utilisateur de test nommé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur Samanage équivalent à l’utilisateur dans Azure AD. En d’autres termes, une relation entre l’utilisateur Azure AD et l’utilisateur Samanage associé doit être établie.

Dans Samanage, assignez la valeur de **nom d’utilisateur** dans Azure AD comme valeur de **nom d’utilisateur** pour établir la relation de lien.

Pour configurer et tester l’authentification unique Azure AD avec Samanage, vous devez suivre les indications des sections suivantes :

1. **[Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Création d’un utilisateur de test Azure AD](#creating-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Création d’un utilisateur de test Samanage](#creating-a-samanage-test-user)** pour avoir un équivalent de Britta Simon dans Samanage qui soit lié à la représentation Azure AD associée.
1. **[Affectation de l’utilisateur de test Azure AD](#assigning-the-azure-ad-test-user)** : permet à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Testing Single Sign-On](#testing-single-sign-on)** pour vérifier si la configuration fonctionne.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuration de l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application Samanage.

**Pour configurer l’authentification unique Azure AD avec Samanage, procédez comme suit :**

1. Dans le portail Azure, sur la page d’intégration de l’application **Samanage**, cliquez sur **Authentification unique**.

    ![Configurer l'authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Configurer l'authentification unique](./media/samanage-tutorial/tutorial_samanage_samlbase.png)

1. Dans la section **Domaine et URL Samanage**, procédez comme suit :

    ![Configurer l'authentification unique](./media/samanage-tutorial/tutorial_samanage_url.png)

    a. Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://<Company Name>.samanage.com/saml_login/<Company Name>`

    b. Dans la zone de texte **Identificateur**, tapez une URL au format suivant : `https://<Company Name>.samanage.com`

    > [!NOTE] 
    > Il ne s’agit pas de valeurs réelles. Mettez à jour ces valeur avec l’URL de connexion et l’identificateur réels. La procédure est expliquée plus loin dans le didacticiel. Pour plus de détails, contactez l’[équipe de support technique Samanage](https://www.samanage.com/support).    
 
1. Dans la section **Certificat de signature SAML**, cliquez sur **Téléchargez le certificat (Base64)** puis enregistrez le fichier du certificat sur votre ordinateur.

    ![Configure Single Sign-On](./media/samanage-tutorial/tutorial_samanage_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Configurer l'authentification unique](./media/samanage-tutorial/tutorial_general_400.png)

1. Dans la section **Configuration de Samanage**, cliquez sur **Configurer Samanage** pour ouvrir la fenêtre **Configurer l’authentification**. Copiez **l’URL de déconnexion et l’ID d’entité SAML** à partir de la **section Référence rapide**.

    ![Configurer l'authentification unique](./media/samanage-tutorial/tutorial_samanage_configure.png) 

1. Dans une autre fenêtre de navigateur web, connectez-vous à votre site d’entreprise Samanage en tant qu’administrateur.

1. Cliquez sur **Dashboard** et sélectionnez **Setup** dans le volet de navigation de gauche.
   
    ![Tableau de bord](./media/samanage-tutorial/tutorial_samanage_001.png "Tableau de bord")

1. Cliquez sur **Single Sign-On**.
   
    ![Authentification unique](./media/samanage-tutorial/tutorial_samanage_002.png "Authentification unique")

1. Accédez à la section **Login using SAML** (Connexion avec SAML), puis procédez comme suit :
   
    ![Connexion avec SAML](./media/samanage-tutorial/tutorial_samanage_003.png "Connexion avec SAML")
 
    a. Cliquez sur **Enable Single Sign-On with SAML**(Activer l’authentification unique avec SAML).  
 
    b. Dans la zone de texte **URL du fournisseur d'identité**, collez la valeur de l’**ID d’entité SAML** copiée à partir du portail Azure.    
 
    c. Vérifiez que l’URL de connexion (**Login URL**) correspond à l’**URL de connexion** de la section **Domaine et URL Samanage** dans le portail Azure.
 
    d. Dans la zone de texte **Logout URL** (URL de déconnexion), collez la valeur d’**URL de déconnexion** que vous avez copiée à partir du portail Azure.
 
    e. Dans la zone de texte **SAML Issuer** (Émetteur SAML), saisissez l’URI d’ID d’application défini dans votre fournisseur d’identité.
 
    f. Ouvrez votre certificat codé en base 64 téléchargé à partir du portail Azure dans Bloc-notes, copiez son contenu dans le Presse-papiers, puis collez-le dans la zone de texte **Paste your Identity Provider x.509 Certificate below** (Collez le certificat X.509 de votre fournisseur d’identité ci-dessous).
 
    g. Cliquez sur **Create users if they do not exist in Samanage**(Créer des utilisateurs s’ils n’existent pas dans Samanage).
 
    h. Cliquez sur **Update**.

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Vous pouvez en savoir plus sur la fonctionnalité de documentation incorporée ici : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)
 
### <a name="creating-an-azure-ad-test-user"></a>Création d’un utilisateur de test Azure AD
L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

![Créer un utilisateur Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le panneau de navigation gauche du **portail Azure**, cliquez sur l’icône **Azure Active Directory**.

    ![Création d’un utilisateur de test Azure AD](./media/samanage-tutorial/create_aaduser_01.png) 

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.
    
    ![Création d’un utilisateur de test Azure AD](./media/samanage-tutorial/create_aaduser_02.png) 

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue.
 
    ![Création d’un utilisateur de test Azure AD](./media/samanage-tutorial/create_aaduser_03.png) 

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :
 
    ![Création d’un utilisateur de test Azure AD](./media/samanage-tutorial/create_aaduser_04.png) 

    a. Dans la zone de texte **Nom**, entrez **BrittaSimon**.

    b. Dans la zone de texte **Nom d’utilisateur**, tapez **l’adresse e-mail** de Britta Simon.

    c. Sélectionnez **Afficher le mot de passe** et notez la valeur du **mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="creating-a-samanage-test-user"></a>Création d’un utilisateur de test Samanage

Pour permettre aux utilisateurs Azure AD de se connecter à Samanage, vous devez les approvisionner dans Samanage.  
Dans le cas de Samanage, l’approvisionnement est une tâche manuelle.

**Pour approvisionner un compte d’utilisateur, procédez comme suit :**

1. Connectez-vous à votre site d’entreprise Samanage en tant qu’administrateur.

1. Cliquez sur **Dashboard** et sélectionnez **Setup** dans le volet de navigation gauche.
   
    ![Configuration](./media/samanage-tutorial/tutorial_samanage_001.png "Configuration")

1. Cliquez sur l’onglet **Users** .
   
    ![Utilisateurs](./media/samanage-tutorial/tutorial_samanage_006.png "Utilisateurs")

1. Cliquez sur **New User**.
   
    ![Nouvel utilisateur](./media/samanage-tutorial/tutorial_samanage_007.png "Nouvel utilisateur")

1. Entrez le **Nom** et l’**Adresse e-mail** du compte Azure Active Directory que vous souhaitez approvisionner, puis cliquez sur **Create user** (Créer un utilisateur).
   
    ![Créer un utilisateur](./media/samanage-tutorial/tutorial_samanage_008.png "Créer un utilisateur")
   
   >[!NOTE]
   >Le titulaire du compte Azure Active Directory reçoit un message électronique contenant un lien à suivre pour confirmer son compte et l’activer. Vous pouvez utiliser tout autre outil ou n’importe quelle API de création de compte d’utilisateur fournis par Samanage pour approvisionner des comptes d’utilisateur Azure Active Directory.

### <a name="assigning-the-azure-ad-test-user"></a>Affectation de l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à Samanage.

![Affecter des utilisateurs][200] 

**Pour attribuer Britta Simon à Samanage, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **Samanage**.

    ![Configurer l'authentification unique](./media/samanage-tutorial/tutorial_samanage_app.png) 

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Affecter des utilisateurs][202] 

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Affecter des utilisateurs][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="testing-single-sign-on"></a>Test de l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Quand vous cliquez sur la mosaïque Samanage dans le volet d’accès, vous devez être connecté automatiquement à votre application Samanage.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md).

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/samanage-tutorial/tutorial_general_01.png
[2]: ./media/samanage-tutorial/tutorial_general_02.png
[3]: ./media/samanage-tutorial/tutorial_general_03.png
[4]: ./media/samanage-tutorial/tutorial_general_04.png

[100]: ./media/samanage-tutorial/tutorial_general_100.png

[200]: ./media/samanage-tutorial/tutorial_general_200.png
[201]: ./media/samanage-tutorial/tutorial_general_201.png
[202]: ./media/samanage-tutorial/tutorial_general_202.png
[203]: ./media/samanage-tutorial/tutorial_general_203.png

