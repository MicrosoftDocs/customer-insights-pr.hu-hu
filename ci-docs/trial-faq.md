---
title: Próbaverzió GYIK – Dynamics 365 Customer Insights
description: Megoldások a Customer Insights próbaverzió beállításával és kezelésével kapcsolatos gyakori kérdésekre. Tájékoztatás a platform- és alkalmazásspecifikus problémák megoldásához.
author: m-hartmann
ms.author: mhart
ms.date: 09/30/2021
ms.topic: get-started
ms.service: customer-insights
ms.custom: template-trial-faq
ms.reviewer: jeffhar
manager: shellyha
ms.openlocfilehash: 2837ae13b4150310193a2d09d59aed66b4a69c69
ms.sourcegitcommit: e6020c178a61beb0ee31a031c11ded914d10d995
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/13/2021
ms.locfileid: "7642878"
---
# <a name="dynamics-365-customer-insights-trial-faq"></a>Dynamics 365 Customer Insights próbaverzió GYIK

## <a name="sign-up"></a>Regisztráció

### <a name="what-are-the-system-requirements-for-the-trial"></a>Milyen rendszerkövetelményei vannak a próbaverziónak?

Ez az alkalmazás egy felhőalapú szolgáltatás, amelyhez egy naprakész webböngészőn kívül nincs szükség speciális szoftverre, azonban érvényesek bizonyos korlátozások. A legjobb próbaidőszak érdekében ne használja inkgnito módban a próbawebhelyet, és válassza ki a önhöz legközelebbi próbahelyet. [További információ a webes alkalmazással kapcsolatos követelményekről.](/power-platform/admin/web-application-requirements)

### <a name="how-do-i-sign-up-for-the-trial-without-a-microsoft-365-tenant"></a>Hogyan regisztrálhatok a próbaverziót Microsoft 365-bérlő nélkül?

Megadhat egy nem munkahelyi e-mail címet, és létrehozunk önnek egy fiókot és bérlőt.

### <a name="can-i-sign-up-for-multiple-dynamics-365-apps-such-as-sales-marketing-and-customer-service"></a>Regisztrálhatok több Dynamics 365 alkalmazásra, például a Sales, Marketing és Customer Service alkalmazásokra?

Igen, ez lehetséges. Az összes rendelkezésre álló próbaverzió megtekintéséhez [látogasson el a próbaverzió-központ oldalára](https://dynamics.microsoft.com/dynamics-365-free-trial). Ugyanazt az e-mail fiókot használhatja a különböző próbaverziókra való feliratkozáshoz. Azonban nem lehetséges, hogy több alkalmazás legyen ugyanazon a próbawebhelyen. Minden próbaverzió másik szervezetben és URL-címen lesz. A próbaverziók adatai nem lesznek megosztva az alkalmazások között.

## <a name="trial-app"></a>Próbaverziós alkalmazás

### <a name="i-didnt-receive-the-trial-details-email-after-signing-up-what-should-i-do"></a>A regisztráció után nem kapom meg a próba részletei e-mailt, mit tegyek?

Amikor feliratkozik a próbaverzióra, egy e-mailt kap a próbaverzió adataival. Ha nem látja az e-mailt a postaládájában, ellenőrizze a levélszemét mappát. Másik megoldásként az alkalmazás eléréséhez használja a következő lépéseket:

1. Lépjen a próbaverzió webhelyére, és válassza a **Kipróbálás ingyen lehetőséget**.
1. Adja meg a használt e-mail-azonosítót a próbaverzióra való feliratkozáshoz. Átirányítjuk a próbaverziós alkalmazásba.

### <a name="how-do-i-add-more-users-to-a-trial"></a>Hogyan lehetséges további felhasználók hozzáadása a próbaverzióhoz?

Felhasználók hozzáadásához lépjen a [Microsoft 365 felügyeleti központba](https://admin.microsoft.com) a próbaverziós rendszergazdai fiókkal. Kövesse a [felügyeleti központ útmutatását](/microsoft-365/admin/add-users/add-users), hogy további felhasználókat adjon hozzá a próbaverzió licenckorlátjáig. Ha a hozzáadott felhasználó már rendelkezik Microsoft 365-fiókkal, rendeljen hozzá megfelelő biztonsági szerepkör a próbaverziós szervezetben. További információ: [Biztonsági szerepkör hozzárendelése egy felhasználóhoz](/power-platform/admin/create-users-assign-online-security-roles#assign-a-security-role-to-a-user).

### <a name="how-many-users-can-i-add-to-my-trial-environment"></a>Hány felhasználót lehet hozzáadni a próbakörnyezethez?

A próbakörnyezethez korlátlan számú felhasználót adhat hozzá.

### <a name="how-do-i-reset-the-trial-environment"></a>Hogyan állítható alaphelyzetbe meg a próbaverziós környezet?

A próbaverziós környezetet nem állíthatja alaphelyzetbe. Megvárhatja azonban a próbaidőszak végét, majd újra feliratkozhat egy új próbaverzióra.

## <a name="trial-expiration-and-extension"></a>Próbaverzió lejárata és meghosszabbítása

### <a name="how-do-i-extend-the-trial"></a>Hogyan hosszabbítható meg a próbaverzió időszaka?

A próbaverziót közvetlenül az alkalmazásban is kibővítheti. A próbaverziót egyszer hosszabbíthatja meg.

### <a name="can-i-convert-the-trial-to-a-paid-license"></a>Átalakíthatom a próbaverziót fizetett licencre?

Általában javasoljuk, hogy a Customer Insights fizetett verziójára való frissítéskor elölről kezdje a saját adataival. 

Ha csak a célközönség használja, akkor a Customer Insights megvásárlásakor másolhatja az adatokat a próbakörnyezetből. Önnek kell a Customer Insights próbaverzió rendszergazdájának és a Microsoft 365-bérlő globális rendszergazdájának vagy a szervezet Dynamics 365 rendszergazdájának lennie ahhoz, hogy a beállításokat a próbakörnyezetből fizetett környezetbe át tudja telepíteni. 

Miután először bejelentkezett a Customer Insights fizetett példányába, a rendszer kéri, hogy hozzon létre egy új környezetet. Ebben a folyamatban megadhatja, hogy a konfigurációt egy meglévő környezetből másolja át, és a beállítások nagy részét áttelepíti. Ha rendelkezik a fenti jogosultságokkal, akkor a próbakörnyezet megjelenik ebben a listában. További információ: [Környezetkonfiguráció másolása](audience-insights/manage-environments.md#copy-the-environment-configuration).

### <a name="what-are-the-trial-limits-and-quotas"></a>Mik a próbaverzió korlátozásai kvótái?

- A saját Azure Data Lake Storage-fiókkal nem tárolhatja a kimeneti adatokat a célközönséggel kapcsolatos információk próbaverziója során. Azonban betölthet adatokat a Data Lake tárfiókból.
- A Customer Insights próbaverziójával maximum 3 GB- adat tárolható a Dataverse környezetben, amely automatikusan ki van építve, amikor elindítja a Customer Insights próbaverzióját.

## <a name="customer-insights-specific-questions"></a>A Customer Insights-ra vonatkozó kérdések

### <a name="how-do-i-start-using-the-trial"></a>Hogyan kezdhetem el használni a próbaverziót?

Miután feliratkozott a próbaverzióra, megérkezik az alkalmazás főképernyőjére. A főképernyő hivatkozásokat biztosít a felhasználói útmutatókhoz és oktatóanyagokhoz. További információért látogasson el a [További források](trial-signup.md#additional-resources) szakasz hivatkozásaira a próbaverzió regisztrációs oldalán.

### <a name="what-features-are-available-in-the-trial"></a>Milyen funkciók érhetők el a próbaverzióban?

A Customer Insights szolgáltatásainak legtöbb szolgáltatása elérhető a próbaverzióban.

Nem érhetők el a következő funkciók: 
- Nem hozhat létre olyan új környezeteket, amelyek saját Azure Data Lake Storage-fiókját használják.

### <a name="how-long-does-the-trial-last"></a>Meddig tart a próbaverzió?

A Customer Insights próbaverziója 30 napig tart. A próbakörnyezetbe való bejelentkezéskor 23 nap után ismét kibővítheti a próbaverziót.

### <a name="how-do-i-remove-sample-data-from-the-trial"></a>Hogyan távolíthatom el a mintaadatokat a próbaverzióból?

Nem távolíthatja el a mintaadatokat a próbaverzióból.
