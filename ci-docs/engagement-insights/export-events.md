---
title: Finomított események exportálása
description: A finomított események és az alapesemények exportálása.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 10/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 7881f8f63134170a7f76e3c75dcfc5fa8930754b
ms.sourcegitcommit: 693458e13e4b4d94b6205093559912f6a4dc4a1c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/06/2021
ms.locfileid: "7606221"
---
# <a name="export-events"></a>Események exportálása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az esemény a felhasználói viselkedésnek megfelelő. Akkor rögzíti, amikor a felhasználó megtekint egy oldalt (esemény megtekintése), vagy együttműködik a tartalommal (műveletesemény). Amikor döntést hoz arról, hogy az adatok mely tulajdonságait szeretné megjeleníteni a jelentésben, az adatok virtuális nézetét nevezzük *finomított eseménynek*. További tudnivalók: [Események létrehozása és módosítása](refined-events.md).

- A külső tárolóba exportálhatók események és eseményesemények. 
- Az exportálás továbbítási adatfolyam. Az adatfolyam nem töltődhet újra. 
- Az exportáláshoz rögzített sémák vannak. Ha egyéni tulajdonságokat ad hozzá egy eseményhez, azok nem fognak szerepelni a eseményben. Új exportálást kell létrehoznia.

## <a name="prerequisites"></a>Előfeltételek

Az exportálás beállítása előtt hozzáféréssel és aktív előfizetéssel kell rendelkezik az Azure portálhoz. Az exportálási folyamat során szükség van a storage-fiókra vonatkozó információkra. 

### <a name="create-an-azure-data-lake-storage-gen-2-accounts"></a>Hozzon létre Azure Data Lake Storage Gen 2 fiókokat

1. Jelentkezzen be az Azure portálra, és [hozzon létre egy új tárhelyfiókot](/azure/storage/common/storage-account-create). 

1. Ügyeljen arra, hogy engedélyezze a **Hierarchikus névtér** elemet a **Speciális** lapon. 

   :::image type="content" source="media/enable-hierarchical-namespace.png" alt-text="Hierarchikus névtér elem engedélyezése a Speciális lapon.":::

1. Üzembe helyezése után menjen az újonnan létrehozott storage-fiókhoz. A navigációs ablaktáblán válassza a **Beállítások** > **A hozzáférési billentyűk** lehetőséget. 

1. Másolja ki a **Fióknevet** és **Kulcsot**, hogy új export létrehozásakor felhasználhassa őket.
   :::image type="content" source="media/storage-account-access-keys.png" alt-text="A tárfiók hozzáférési kulcsai.":::

## <a name="export-events"></a>Események exportálása

Az **Események exportálása** párbeszédpanel kétféleképpen jelennek meg: 
- Válassza az **Adatok** > **Export** menüpontot, és válassza az **Új export** lehetőséget.
- Válassza az **Adat** > **Események**, majd a **Több [...]** lehetőséget az exportálni kívánt esemény mellett, majd válassza az **Exportálás** parancsot a legördülő menüből. 

:::image type="content" source="media/new-export.png" alt-text="Új export létrehozása.":::

Az exportálás létrehozásához szükséges lépések végigvezetik a következő lépéseken:

1. Adja meg az **Exportálás nevét**, majd válassza a **Tovább** lehetőséget.

1. Az **Események kiválasztása** legördülő listában válassza ki az alapeseményeket és pontosított eseményeket, hogy szerepeljenek az exportálásban. 

1. A **Fájlstruktúra** szakaszban válassza ki a lépésmennyiséget (óránként vagy naponta), hogy új fájlokat hozzon létre a céltárolóban, majd válassza a **Tovább** lehetőséget. Az események importálása folyamatosan meg fog érkezni.

1. A **Formátum kiválasztása** párbeszédpanelen válassza ki az exportálás formátumát. Választhat a **Common Data Model**, a **CSV** és a **JSON** formátumok közül. Az exportálás más Dynamics 365 alkalmazásokkal való használathoz a **Common Data Model** formátumot javasoljuk.

1. Adja meg a Azure Data Lake Storage Gen 2 helyet a **Cél kiválasztása** párbeszédpanelen.
    1. Az **ADLS Gen 2 fiók neve** annak a tárolófióknak a neve, amelybe menteni szeretné az exportálást. 
    1. A **mappa elérési útja** határozza meg, hogy az exportálás hol tárolható a storage-fiók fájlrendszerében és könyvtárstruktúrájában.
    1. A **megosztott kulcs** az Azure portálon érhető el a storage-fiókhoz.

1. Ellenőrizze és erősítse meg a megadott beállításokat a befejezéshez.

## <a name="view-and-manage-exports"></a>Exportok megjelenítése és kezelése

Az exportálás beállítása után, a megtekintéséhez lépjen az **Adatok** > **Exportok** lehetőségre. Válassza a **További [...]** lehetőséget meglévő export szerkesztése vagy törlése esetén.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
