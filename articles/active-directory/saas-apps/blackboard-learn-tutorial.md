---
title: "Didacticiel : Intégration d'Azure Active Directory à Blackboard Learn | Microsoft Docs"
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et Blackboard Learn.
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.assetid: 0b8ca505-61ea-487c-9a3e-fa50c936df0c
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/19/2017
ms.author: jeedes
ms.openlocfilehash: 9b7e7a84059f8393e8f900733602e32ca3ad833b
ms.sourcegitcommit: 1d850f6cae47261eacdb7604a9f17edc6626ae4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39423655"
---
# <a name="tutorial-azure-active-directory-integration-with-blackboard-learn"></a>Didacticiel : Intégration d'Azure Active Directory à Blackboard Learn

Dans ce didacticiel, vous allez apprendre à intégrer Blackboard Learn à Azure Active Directory (Azure AD).

L’intégration de Blackboard Learn dans Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à Blackboard Learn.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à Blackboard Learn (via l’authentification unique) avec leur compte Azure AD
- Vous pouvez gérer vos comptes à partir d’un emplacement central : le portail Azure.

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD à Blackboard Learn, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement avec authentification unique à Blackboard Learn

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez obtenir un essai d’un mois [ici](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de Blackboard Learn à partir de la galerie
1. Configuration et test de l’authentification unique Azure AD

## <a name="adding-blackboard-learn-from-the-gallery"></a>Ajout de Blackboard Learn à partir de la galerie
Pour configurer l’intégration de Blackboard Learn à Azure AD, vous devez ajouter Blackboard Learn de la galerie à votre liste d’applications SaaS gérées.

**Pour ajouter Blackboard Learn à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Active Directory][1]

1. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![APPLICATIONS][2]
    
1. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![APPLICATIONS][3]

1. Dans la zone de recherche, tapez **Blackboard Learn**.

    ![Création d’un utilisateur de test Azure AD](./media/blackboard-learn-tutorial/tutorial_blackboardlearn_search.png)

1. Dans le volet de résultats, sélectionnez **Blackboard Learn**, puis cliquez sur **Ajouter** pour ajouter l’application.

    ![Création d’un utilisateur de test Azure AD](./media/blackboard-learn-tutorial/tutorial_blackboardlearn_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Configuration et test de l’authentification unique Azure AD
Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec Blackboard Learn avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur Blackboard Learn équivalent dans Azure AD. En d’autres termes, une relation entre l’utilisateur Azure AD et l’utilisateur Blackboard Learn associé doit être établie.

Pour cela, affectez la valeur de **nom d’utilisateur** dans Azure AD comme valeur de **nom d’utilisateur** dans Blackboard Learn.

Pour configurer et tester l’authentification unique Azure AD avec Blackboard Learn, vous devez suivre les indications des sections suivantes :

1. **[Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
1. **[Création d’un utilisateur de test Azure AD](#creating-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
1. **[Création d’un utilisateur de test Blackboard Learn](#creating-a-blackboard-learn-test-user)** pour avoir un équivalent de Britta Simon dans Blackboard Learn lié à la représentation Azure AD associée.
1. **[Affectation de l’utilisateur de test Azure AD](#assigning-the-azure-ad-test-user)** : permet à Britta Simon d’utiliser l’authentification unique Azure AD.
1. **[Testing Single Sign-On](#testing-single-sign-on)** pour vérifier si la configuration fonctionne.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuration de l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application Blackboard Learn.

**Pour configurer l’authentification unique Azure AD avec Blackboard Learn, procédez comme suit :**

1. Dans le portail Azure, dans la page d’intégration de l’application **Blackboard Learn**, cliquez sur **Authentification unique**.

    ![Configurer l'authentification unique][4]

1. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Configurer l'authentification unique](./media/blackboard-learn-tutorial/tutorial_blackboardlearn_samlbase.png)

1. Dans la section **Domaine et URL Blackboard Learn**, effectuez les étapes suivantes :

    ![Configurer l'authentification unique](./media/blackboard-learn-tutorial/tutorial_blackboardlearn_url.png)

    a. Dans la zone de texte **URL de connexion**, tapez une URL au format suivant : `https://<subdomain>.blackboard.com/`

    b. Dans la zone de texte **Identificateur**, tapez une URL au format suivant : `https://<subdomain>.blackboard.com/auth-saml/saml/SSO/entity-id/SAML_AD`
    
    > [!NOTE] 
    > Il ne s’agit pas de valeurs réelles. Mettez à jour ces valeurs avec l’URL de connexion et l’identificateur réels. Pour obtenir ces valeurs, contactez [l’équipe du support Blackboard Learn](https://www.blackboard.com/support/index.aspx). 

1. L’application Blackboard Learn attend les assertions SAML dans un format spécifique. Configurez les revendications suivantes pour cette application. Vous pouvez gérer les valeurs de ces attributs à partir de la section **Attributs utilisateur** sur la page d’intégration des applications.
 La capture d’écran suivante en présente un exemple.

    ![Configurer l'authentification unique](./media/blackboard-learn-tutorial/tutorial_attribute.png)

1. Dans la section **Attributs utilisateur** de la boîte de dialogue **Authentification unique**, configurez les attributs du jeton SAML comme indiqué dans l’image, puis effectuez les étapes suivantes : Nous avons mappé Userprincipalname comme seul attribut utilisateur ici, mais vous pouvez le mapper à la valeur appropriée qui identifie de façon unique l’utilisateur dans l’organisation et se mappe avec le champ de nom d’utilisateur Blackboard Learn.
           
    | Nom de l'attribut | Valeur de l’attribut |   
    | ---------------| ----------------|
    | urn:oid:1.3.6.1.4.1.5923.1.1.1.6 |user.userprincipalname |

    a. Cliquez sur **Ajouter un attribut** pour ouvrir la boîte de dialogue **Ajouter un attribut**.

    ![Configure Single Sign-On](./media/blackboard-learn-tutorial/tutorial_attribute_04.png)
    
    ![Configure Single Sign-On](./media/blackboard-learn-tutorial/tutorial_attribute_05.png)

    b. Dans la zone de texte **Attribut**, indiquez le nom d’attribut pour cette ligne.

    c. Dans la liste **Valeur** , saisissez la valeur d’attribut affichée pour cette ligne.
    
    d. Cliquez sur **OK**.

1. Dans la section **Certificat de signature SAML**, cliquez sur **Métadonnées XML** puis enregistrez le fichier XML sur votre ordinateur.

    ![Configure Single Sign-On](./media/blackboard-learn-tutorial/tutorial_blackboardlearn_certificate.png)

1. Cliquez sur le bouton **Enregistrer** .

    ![Configurer l'authentification unique](./media/blackboard-learn-tutorial/tutorial_general_400.png)

1. Dans la section **Configuration de Blackboard Learn**, cliquez sur **Configurer Blackboard Learn** pour ouvrir la fenêtre **Configurer l’authentification**. Copiez **l’ID d’entité SAML** à partir de la **section Référence rapide**.

    ![Configurer l'authentification unique](./media/blackboard-learn-tutorial/tutorial_blackboardlearn_configure.png) 

1. Pour configurer l’authentification unique côté **Blackboard Learn**, vous devez envoyer le fichier **XML de métadonnées** téléchargé et **l’ID d’entité SAML** à [l’équipe du support Blackboard Learn](https://www.blackboard.com/support/index.aspx).

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Vous pouvez en savoir plus sur la fonctionnalité de documentation incorporée ici : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)

### <a name="creating-an-azure-ad-test-user"></a>Création d’un utilisateur de test Azure AD
L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

![Créer un utilisateur Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le panneau de navigation gauche du **portail Azure**, cliquez sur l’icône **Azure Active Directory**.

    ![Création d’un utilisateur de test Azure AD](./media/blackboard-learn-tutorial/create_aaduser_01.png) 

1. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.
    
    ![Création d’un utilisateur de test Azure AD](./media/blackboard-learn-tutorial/create_aaduser_02.png) 

1. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue.
 
    ![Création d’un utilisateur de test Azure AD](./media/blackboard-learn-tutorial/create_aaduser_03.png) 

1. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :
 
    ![Création d’un utilisateur de test Azure AD](./media/blackboard-learn-tutorial/create_aaduser_04.png) 

    a. Dans la zone de texte **Nom**, entrez **BrittaSimon**.

    b. Dans la zone de texte **Nom d’utilisateur** , tapez l’**adresse de messagerie** de Britta Simon.

    c. Sélectionnez **Afficher le mot de passe** et notez la valeur du **mot de passe**.

    d. Cliquez sur **Créer**.
 
### <a name="creating-a-blackboard-learn-test-user"></a>Création d’un utilisateur de test Blackboard Learn
Dans cette section, vous allez créer un utilisateur appelé Britta Simon dans Blackboard Learn. 

L'application Blackboard Learn prend en charge la configuration de l'utilisateur au moment opportun. Vérifiez que vous avez configuré les revendications comme décrit dans la section **[Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-sign-on)**.
### <a name="assigning-the-azure-ad-test-user"></a>Affectation de l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à Blackboard Learn.

![Affecter des utilisateurs][200] 

**Pour affecter Britta Simon à Blackboard Learn, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

1. Dans la liste des applications, sélectionnez **Blackboard Learn**.

    ![Configurer l'authentification unique](./media/blackboard-learn-tutorial/tutorial_blackboardlearn_app.png) 

1. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Affecter des utilisateurs][202] 

1. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Affecter des utilisateurs][203]

1. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

1. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

1. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="testing-single-sign-on"></a>Test de l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la vignette Blackboard Learn dans le volet d’accès, vous devez être connecté automatiquement à votre application Blackboard Learn. Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/blackboard-learn-tutorial/tutorial_general_01.png
[2]: ./media/blackboard-learn-tutorial/tutorial_general_02.png
[3]: ./media/blackboard-learn-tutorial/tutorial_general_03.png
[4]: ./media/blackboard-learn-tutorial/tutorial_general_04.png

[100]: ./media/blackboard-learn-tutorial/tutorial_general_100.png

[200]: ./media/blackboard-learn-tutorial/tutorial_general_200.png
[201]: ./media/blackboard-learn-tutorial/tutorial_general_201.png
[202]: ./media/blackboard-learn-tutorial/tutorial_general_202.png
[203]: ./media/blackboard-learn-tutorial/tutorial_general_203.png

