---
ms.openlocfilehash: 1d79987893986148421c316193b27d268cfe0a0b
ms.sourcegitcommit: 4ae316c856b8de0f08a4605f73e75a8c2cf51c4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2022
ms.locfileid: "8755547"
---
Az adatok betöltése után indítsa el az adategyesítési folyamatot egy egységes ügyfélprofil létrehozásához. További információkért lásd: [Adatok egységesítése](../data-unification.md).

### <a name="select-source-fields"></a>Forrásmezők kijelölése

1. Az adatok betáplálása után képezze le a kapcsolattartókat az eCommerce-ből és a Loyalty data-ból a közös adattípusokba. Nyissa meg az **Adatok** > **egyesítését**.

1. Válassza ki az entitást, amely jelképezi az ügyfélprofilt – **eCommerceContacts** és **loyCustomers**.

   ![az ecommerce és a loyality adatforrások egységesítése.](../media/unify-ecommerce-loyalty.png)

1. Jelölje ki a **ContactId**-t elsődleges kulcsaként az **eCommerceContacts**-hoz és a **LoyaltyID** a **loyCustomers** elsődleges kulcsaként.

1. Válassza a **Következő** lehetőséget. Hagyja ki az ismétlődő rekordokat, és válassza a Tovább **lehetőséget**.

### <a name="match-conditions"></a>Feltételek egyeztetése

1. Válassza az **eCommerceContacts: eCommerce: eCommerce** mint elsődleges entitás lehetőséget, és tartalmazza az összes rekordot.

1. Válassza a **loyCustomers: LoyaltyScheme** lehetőséget, és tartalmazza az összes rekordot.

1. Szabály hozzáadása:
   - Válassza **a FullName lehetőséget** mind az eCommerceContacts, mind a loyCustomers esetében.
   - Válassza a Típus (Telefon, Név, Cím, ...) lehetőséget a **Normalizáláshoz**.**·**
   - Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.
   - Írja be a **Teljes név, e-mail címet** a névhez.

1. Adjon hozzá egy második feltételt az e-mail címhez:
   - Válassza **az E-mail lehetőséget** mind az e-kereskedelmi kapcsolatok, mind a loyCustomers számára.
   - Hagyja üresen a Normalizálást.
   - Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.

   ![Egységesítése az egyezési szabályt a névhez és az e-mailhez.](../media/unify-match-rule.png)

1. Válassza a **Kész** lehetőséget.

1. Válassza a **Következő** lehetőséget.

### <a name="unify-fields"></a>Mezők egyesítése

1. Nevezze át a **LoyCustomers** entitás ContactId azonosítóját ContactIdid-re **·** **ContactIdLOYALTY-ra**, hogy megkülönböztesse azt a többi betöltött azonosítótól.

1. Az ellenőrzéshez kattintson **a Tovább** gombra, majd válassza a Vevőprofilok **létrehozása lehetőséget**.
