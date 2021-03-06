---
title: 'Didacticiel : Intégration d’Azure Active Directory avec eDigitalResearch | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et eDigitalResearch.
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.reviewer: joflore
ms.assetid: c6b66ea0-16ba-45b4-b550-e81c56262b1f
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/20/2017
ms.author: jeedes
ms.openlocfilehash: d5c86186cd6ee02d83800c6483a2e35d8f1fb3c7
ms.sourcegitcommit: 11d8ce8cd720a1ec6ca130e118489c6459e04114
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2018
ms.locfileid: "52848712"
---
# <a name="tutorial-azure-active-directory-integration-with-edigitalresearch"></a>Didacticiel : Intégration d’Azure Active Directory avec eDigitalResearch

Dans ce didacticiel, vous allez apprendre à intégrer eDigitalResearch dans Azure Active Directory (Azure AD).

L’intégration d’eDigitalResearch à Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à eDigitalResearch.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à eDigitalResearch (via l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD avec eDigitalResearch, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement eDigitalResearch pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout d’eDigitalResearch à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-edigitalresearch-from-the-gallery"></a>Ajout d’eDigitalResearch à partir de la galerie
Pour configurer l’intégration d’eDigitalResearch avec Azure AD, vous devez ajouter eDigitalResearch, disponible dans la galerie, à votre liste d’applications SaaS gérées.

**Pour ajouter eDigitalResearch à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

1. Dans la zone de recherche, tapez **eDigitalResearch**, sélectionnez **eDigitalResearch** dans le volet de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![eDigitalResearch dans la liste des résultats](./media/edigitalresearch-tutorial/tutorial_edigitalresearch_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec eDigitalResearch avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur eDigitalResearch équivalent dans Azure AD. En d’autres termes, une relation entre l’utilisateur Azure AD et l’utilisateur eDigitalResearch associé doit être établie.

Dans eDigitalResearch, assignez la valeur du **nom d’utilisateur** d’Azure AD comme valeur de **Username** (Nom d’utilisateur) pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec eDigitalResearch, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Crééer un utilisateur de test eDigitalResearch](#create-a-edigitalresearch-test-user)** pour avoir dans eDigitalResearch un équivalent de Britta Simon lié à la représentation Azure AD associée.
1. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Tester l’authentification unique](#test-single-sign-on)** pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application eDigitalResearch.

**Pour configurer l’authentification unique Azure AD avec eDigitalResearch, procédez comme suit :**

1. Dans le portail Azure, dans la page d’intégration de l’application **eDigitalResearch**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Boîte de dialogue Authentification unique](./media/edigitalresearch-tutorial/tutorial_edigitalresearch_samlbase.png)

1. Dans la section **eDigitalResearch Domain and URLs** (Domaine et URL eDigitalResearch), procédez comme suit :

    ![Informations d’authentification unique dans eDigitalResearch Domain and URLs (Domaine et URL eDigitalResearch)](./media/edigitalresearch-tutorial/tutorial_edigitalresearch_url.png)

    a. Dans la zone de texte **Identificateur**, tapez une URL au format suivant : `https://<company-name>.edigitalresearch.com`

    b. Dans la zone de texte **URL de réponse** , tapez une URL au format suivant : `https://<company-name>.edigitalresearch.com/login/consume`

    > [!NOTE] 
    > Il ne s’agit pas de valeurs réelles. Mettez à jour ces valeurs avec l’identificateur et l’URL de réponse réels. Pour obtenir ces valeurs, contactez l’[équipe de support eDigitalResearch](https://www.maruedr.com/contact).
 


1. Dans la section **Certificat de signature SAML**, cliquez sur **Certificat (en base64)**, puis enregistrez le fichier du certificat sur votre ordinateur.

    !![Lien Téléchargement de certificat](./media/edigitalresearch-tutorial/tutorial_edigitalresearch_certificate.png) 

1. Cliquez sur le bouton **Enregistrer** .

    ![Bouton Enregistrer de la page Configurer l’authentification unique](./media/edigitalresearch-tutorial/tutorial_general_400.png)

1. Dans la section **eDigitalResearch Configuration** (Configuration d’eDigitalResearch), cliquez sur **Configure eDigitalResearch** (Configurer eDigitalResearch) pour ouvrir la fenêtre **Configurer l’authentification**. Copiez **l’URL de déconnexion et l’ID d’entité SAML** à partir de la section **Référence rapide**.

    ![Configuration d’eDigitalResearch](./media/edigitalresearch-tutorial/tutorial_edigitalresearch_configure.png) 

1. Pour configurer l’authentification unique côté **eDigitalResearch**, vous devez envoyer le **fichier de certificat (en base64)** téléchargé, l’**ID d’entité SAML** et l’**URL de déconnexion** à l’[équipe de support eDigitalResearch](https://www.maruedr.com/contact). Celles-ci configurent ensuite ce paramètre pour que la connexion SSO SAML soit définie correctement des deux côtés.

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Pour en savoir plus sur la fonctionnalité de documentation incorporée, accédez à : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/edigitalresearch-tutorial/create_aaduser_01.png)

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/edigitalresearch-tutorial/create_aaduser_02.png)

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/edigitalresearch-tutorial/create_aaduser_03.png)

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/edigitalresearch-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
  
### <a name="create-a-edigitalresearch-test-user"></a>Créer un utilisateur de test eDigitalResearch

L’objectif de cette section est de créer un utilisateur appelé Britta Simon dans eDigitalResearch. 

Pour créer des utilisateurs, contactez l’[équipe de support eDigitalResearch](https://www.maruedr.com/contact).        
    
 > [!NOTE]
 > Le titulaire du compte Azure Active Directory reçoit un e-mail contenant un lien à suivre pour confirmer son compte et l’activer.

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à eDigitalResearch.

![Attribuer le rôle utilisateur][200] 

**Pour affecter Britta Simon à eDigitalResearch, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **eDigitalResearch**.

    ![Lien eDigitalResearch dans la liste des applications](./media/edigitalresearch-tutorial/tutorial_edigitalresearch_app.png)  

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la vignette eDigitalResearch dans le volet d’accès, vous devez être connecté automatiquement à votre application eDigitalResearch.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/edigitalresearch-tutorial/tutorial_general_01.png
[2]: ./media/edigitalresearch-tutorial/tutorial_general_02.png
[3]: ./media/edigitalresearch-tutorial/tutorial_general_03.png
[4]: ./media/edigitalresearch-tutorial/tutorial_general_04.png

[100]: ./media/edigitalresearch-tutorial/tutorial_general_100.png

[200]: ./media/edigitalresearch-tutorial/tutorial_general_200.png
[201]: ./media/edigitalresearch-tutorial/tutorial_general_201.png
[202]: ./media/edigitalresearch-tutorial/tutorial_general_202.png
[203]: ./media/edigitalresearch-tutorial/tutorial_general_203.png

