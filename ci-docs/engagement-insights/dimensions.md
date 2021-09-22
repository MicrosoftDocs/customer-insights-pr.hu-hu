---
title: Dimenziók megtekintése és létrehozása
description: Dimenziók létrehozása, szerkesztése és törlése.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 06/09/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: b575c5e84197d76f53a722bac60c5af928c917f9671720ede1de38c4a7478be4
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7034000"
---
# <a name="view-and-create-dimensions"></a>Dimenziók megtekintése és létrehozása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A dimenzió olyan eseményattribútum, amely leírhatja, szűrheti vagy csoportosíthatja az adatokat. Ha marketingpromóciót futtat a webhelyén, a dimenziók segítségével rendezheti a látogatókat az új és visszatérő felhasználók szerint.  

Az elkötelezettségi információk gyári dimenziókat tartalmaz az eseménytulajdonságokhoz. Például:

- Böngésző neve
- Oldal neve
- Eszközmodell
- Operációs rendszer
- Ország/régió

## <a name="view-dimensions"></a>Dimenziók megtekintése

A dimenziók a meglévő eseménytulajdonságokon alapulnak. Amikor a követőkódot használja az elkötelezettségi információkhoz, a rendszer dimenziói automatikusan létrejönnek.

1. Válassza a bal navigációs ablaktáblán az **Adatok** elemet. 
1. Válassza a **Dimenziók** lehetőséget a munkaterület összes dimenziója listájának megtekintéséhez. 
   > [!NOTE]
   > A rendszer által generált dimenziók csak olvashatók. Ezeket nem szerkesztheti. Egyéni dimenziókat csak létrehozhat és szerkeszthet.

## <a name="create-a-dimension"></a>Dimenzió létrehozása

A rendszer által generált dimenziók mellett a környezet- és munkaterület-rendszergazdák egyéni dimenziókat is létrehozhatnak. Az egyéni dimenziók az alapesemények alapértelmezett tulajdonságain alapulnak, vagy [egy esemény egyéni tulajdonságait használhatják](advanced-SDK-implementation.md).

1. Menjen az **Adatok** > **Dimenziók** helyre.
1. Válassza a **Dimenzió hozzáadása** lehetőséget.

   :::image type="content" source="media/add-dimension.png" alt-text="Dimenzió hozzáadása egy eseményhez.":::

1. A **Dimenzió létrehozása** ablaktáblában jelöljön ki egy tulajdonságot, amelyre a dimenziót alapozza. A tulajdonságlista a munkaterületen lévő összes olyan tulajdonságot mutatja, amely nincs hozzárendelve egy dimenzióhoz.
1. A **Megjelenítendő név** mezőbe írjon be egy új nevet. Opcionális: megadhat egy leírást is.
1. Mentse a dimenziót a **Létrehozás** menüelemmel. Akár egy percet is igénybe vehet, mielőtt a dimenziót [egyéni jelentésben](custom-reports.md) vagy [szegmensben](segments.md) használhatja. 

## <a name="edit-a-dimension"></a>Egy dimenzió szerkesztése

Módosíthatja a dimenzió nevét és leírását.

1. Menjen az **Adatok** > **Dimenziók** helyre.
1. Jelölje ki a törlendő dimenziót.
1. A **Dimenzió szerkesztése** ablaktáblán frissítse a dimenziót.
1. Válassza a **Alkalmazás** lehetőséget a módosítások mentéséhez.

## <a name="delete-a-dimension"></a>Egy dimenzió törlése

Csak a felhasználó által létrehozott dimenziókat törölheti, de a rendszerdimenziókat nem.

A dimenzió törlése végleges. A törölt dimenziót használó jelentések és szegmensek a továbbiakban nem fognak működni. 

1. Menjen az **Adatok** > **Dimenziók** helyre.
1. Jelölje ki a törlendő dimenziót.
1. A **Dimenzió szerkesztése** ablaktáblán válassza a **Dimenzió törlése** lehetőséget.

   :::image type="content" source="media/delete-dimension.png" alt-text="Dimenzió törlése egy eseményből.":::

1. A törlés megerősítéséhez írja be a **CONFIRM DELETE** (minden nagybetűs) parancsot. 
1. Válassza a **Törlés** lehetőséget.

[!INCLUDE[footer-include](../includes/footer-banner.md)]