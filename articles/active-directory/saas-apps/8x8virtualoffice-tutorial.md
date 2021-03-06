---
title: 'Didacticiel : Intégration d’Azure Active Directory à 8x8 Virtual Office | Microsoft Docs'
description: Découvrez comment configurer l’authentification unique entre Azure Active Directory et 8x8 Virtual Office.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: b34a6edf-e745-4aec-b0b2-7337473d64c5
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 10/30/2018
ms.author: jeedes
ms.openlocfilehash: 53db637bf7ad47896747b491fcbe31123fdb104e
ms.sourcegitcommit: ae45eacd213bc008e144b2df1b1d73b1acbbaa4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50741808"
---
# <a name="tutorial-azure-active-directory-integration-with-8x8-virtual-office"></a>Didacticiel : Intégration d’Azure Active Directory à 8x8 Virtual Office

Dans ce didacticiel, vous allez apprendre à intégrer 8x8 Virtual Office à Azure Active Directory (Azure AD).

L’intégration de 8x8 Virtual Office dans Azure AD vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à 8x8 Virtual Office.
- Vous pouvez autoriser les utilisateurs à se connecter automatiquement à 8x8 Virtual Office (via l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure

Pour en savoir plus sur l’intégration des applications SaaS à Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique auprès d’Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)

## <a name="prerequisites"></a>Prérequis

Pour configurer l’intégration d’Azure AD à 8x8 Virtual Office, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement 8x8 Virtual Office pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario

Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de 8x8 Virtual Office à partir de la galerie
2. Configuration et test de l’authentification unique Azure AD

## <a name="adding-8x8-virtual-office-from-the-gallery"></a>Ajout de 8x8 Virtual Office à partir de la galerie

Pour configurer l’intégration de 8x8 Virtual Office avec Azure AD, vous devez ajouter 8x8 Virtual Office, disponible dans la galerie, à votre liste d’applications SaaS gérées.

**Pour ajouter 8x8 Virtual Office à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

2. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
3. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

4. Dans la zone de recherche, tapez **8x8 Virtual Office**, sélectionnez **8x8 Virtual Office** dans le panneau de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![8 x 8 Virtual Office dans la liste des résultats](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec 8x8 Virtual Office, avec un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit connaître l’utilisateur 8x8 Virtual Office correspondant à l’utilisateur Azure AD. En d’autres termes, une relation entre l’utilisateur Azure AD et l’utilisateur 8x8 Virtual Office associé doit être établie.

Pour configurer et tester l’authentification unique Azure AD avec 8x8 Virtual Office, vous devez suivre les indications des sections suivantes :

1. **[Configuration de l’authentification unique Azure AD](#configuring-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
2. **[Création d’un utilisateur de test Azure AD](#creating-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
3. **[Création d’un utilisateur de test 8x8 Virtual Office](#creating-a-8x8-virtual-office-test-user)** pour avoir un équivalent de Britta Simon dans 8x8 Virtual Office lié à la représentation Azure AD de l’utilisateur.
4. **[Affectation de l’utilisateur de test Azure AD](#assigning-the-azure-ad-test-user)** : permet à Britta Simon d’utiliser l’authentification unique Azure AD.
5. **[Test de l’authentification unique](#testing-single-sign-on)** pour vérifier si la configuration fonctionne.

### <a name="configuring-azure-ad-single-sign-on"></a>Configuration de l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application 8x8 Virtual Office.

**Pour configurer l’authentification unique Azure AD avec 8x8 Virtual Office, effectuez les étapes suivantes :**

1. Dans le portail Azure, dans la page d’intégration de l’application **8x8 Virtual Office**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

2. Dans la boîte de dialogue **Sélectionner une méthode d’authentification unique**, cliquez sur **Sélectionner** pour le mode **SAML** afin d’activer l’authentification unique.

    ![Configurer l'authentification unique](common/tutorial_general_301.png)

3. Dans la page **Configurer l’authentification unique avec SAML**, cliquez sur l’icône **Modifier** pour ouvrir la boîte de dialogue **Configuration SAML de base**.

    ![Configurer l'authentification unique](common/editconfigure.png)

4. Dans la section **Configuration SAML de base**, effectuez les étapes suivantes :

    ![Informations d’authentification unique dans le domaine et les URL 8x8 Virtual Office](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_url.png)

    a. Dans la zone de texte **Identificateur**, tapez une URL : `https://sso.8x8.com/saml2`

    b. Dans la zone de texte **URL de réponse**, tapez l’URL au format suivant : `https://sso.8x8.com/saml2`

5. Dans la page **Certificat de signature SAML**, dans la section **Certificat de signature SAML**, cliquez sur **Télécharger** pour télécharger le **Certificat (brut)**, puis enregistrez le fichier de certificat sur votre ordinateur.

    ![Lien Téléchargement de certificat](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_certificate.png) 

6. Dans la section **Configurer 8x8 Virtual Office**, copiez l’URL appropriée en fonction de vos besoins.

    a. URL de connexion

    b. Identificateur Azure AD

    c. URL de déconnexion

    ![Configuration de 8x8 Virtual Office](common/configuresection.png)

7. Connectez-vous à votre client 8x8 Virtual Office en tant qu’administrateur.

8. Sélectionnez **Virtual Office Account Mgr** (Gestionnaire de compte Virtual Office) dans le volet Applications.

    ![Configurer l’authentification côté application](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_001.png)

9. Sélectionnez le compte **Entreprise** à gérer, puis cliquez sur le bouton **Se connecter**.

    ![Configurer l’authentification côté application](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_002.png)

10. Cliquez sur l’onglet **COMPTES** dans la liste de menu.

    ![Configurer l’authentification côté application](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_003.png)

11. Cliquez sur **Authentification unique** dans la liste des comptes.
  
    ![Configurer l’authentification côté application](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_004.png)

12. Sélectionnez **Authentification unique** sous la section Méthodes d’authentification, puis cliquez sur **SAML**.

    ![Configurer l’authentification côté application](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_005.png)

13. Dans la section **Authentification unique SAML**, procédez comme suit :

    ![Configurer l’authentification côté application](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_006.png)

    a. Dans la zone de texte **URL de connexion**, collez l’**URL de connexion** que vous avez copiée sur le portail Azure.

    b. Dans la zone de texte **URL de déconnexion**, collez l’**URL de déconnexion** que vous avez copiée sur le portail Azure.

    c. Dans la zone de texte **URL de l’émetteur**, collez l’**Identificateur Azure AD** que vous avez copié sur le portail Azure.

    d. Cliquez sur le bouton **Parcourir** pour charger le certificat que vous avez téléchargé à partir du portail Azure.

    e. Cliquez sur le bouton **Enregistrer** .

### <a name="creating-an-azure-ad-test-user"></a>Création d’un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

1. Dans le volet gauche du portail Azure, sélectionnez **Azure Active Directory**, sélectionnez **Utilisateurs**, puis sélectionnez **Tous les utilisateurs**.

    ![Créer un utilisateur Azure AD][100]

2. Sélectionnez **Nouvel utilisateur** dans la partie supérieure de l’écran.

    ![Création d’un utilisateur de test Azure AD](common/create_aaduser_01.png) 

3. Dans les propriétés de l’utilisateur, effectuez les étapes suivantes.

    ![Création d’un utilisateur de test Azure AD](common/create_aaduser_02.png)

    a. Dans le champ **Nom**, entrez **BrittaSimon**.
  
    b. Dans le champ **Nom d’utilisateur**, tapez **brittasimon@yourcompanydomain.extension**  
    Par exemple, BrittaSimon@contoso.com

    c. Sélectionnez **Propriétés**, cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ Mot de passe.

    d. Sélectionnez **Créer**.
  
### <a name="creating-a-8x8-virtual-office-test-user"></a>Création d’un utilisateur de test 8x8 Virtual Office

L’objectif de cette section est de créer un utilisateur appelé Britta Simon dans 8x8 Virtual Office. 8x8 Virtual Office prend en charge l’approvisionnement juste-à-temps, option activée par défaut.

Vous n’avez aucune opération à effectuer dans cette section. Un utilisateur est créé lors d’une tentative d’accès à 8x8 Virtual Office s’il n’existe pas déjà.

> [!NOTE]
> Si vous devez créer un utilisateur manuellement, contactez [l’équipe du support technique 8x8 Virtual Office](https://www.8x8.com/about-us/contact-us).

### <a name="assigning-the-azure-ad-test-user"></a>Affectation de l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à 8x8 Virtual Office.

1. Dans le portail Azure, sélectionnez **Applications d’entreprise**, puis **Toutes les applications**.

    ![Affecter des utilisateurs][201]

2. Dans la liste des applications, sélectionnez **8x8 Virtual Office**.

    ![Configurer l'authentification unique](./media/8x8virtualoffice-tutorial/tutorial_8x8virtualoffice_app.png) 

3. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Affecter des utilisateurs][202]

4. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Affecter des utilisateurs][203]

5. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste Utilisateurs, puis cliquez sur le bouton **Sélectionner** en bas de l’écran.

6. Dans la boîte de dialogue **Ajouter une attribution**, sélectionnez le bouton **Attribuer**.

### <a name="testing-single-sign-on"></a>Test de l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la vignette 8x8 Virtual Office dans le volet d’accès, vous devez être connecté automatiquement à votre application 8x8 Virtual Office.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](../user-help/active-directory-saas-access-panel-introduction.md).

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](../manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: common/tutorial_general_01.png
[2]: common/tutorial_general_02.png
[3]: common/tutorial_general_03.png
[4]: common/tutorial_general_04.png

[100]: common/tutorial_general_100.png

[201]: common/tutorial_general_201.png
[202]: common/tutorial_general_202.png
[203]: common/tutorial_general_203.png
