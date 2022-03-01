---
title: Finomított események exportálása
description: A finomított események és az alapesemények exportálása.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 04/30/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: faa0c3afb08d1c0282b2164ed914637ce9aad88117af37ba44fdb81e7610e574
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7032388"
---
# <a name="export-events"></a>Események exportálása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az esemény a felhasználói viselkedésnek megfelelő. Akkor rögzíti, amikor a felhasználó megtekint egy oldalt (esemény megtekintése), vagy együttműködik a tartalommal (műveletesemény). Amikor döntést hoz arról, hogy az adatok mely tulajdonságait szeretné megjeleníteni a jelentésben, az adatok virtuális nézetét nevezzük *finomított eseménynek*. 

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

Az események exportálásának két módja van: 
- Válassza az **Adatok** > **Export** menüpontot, és válassza az **Új export** lehetőséget.
- Válassza az **Adat** > **Események**, majd a **Több [...]** lehetőséget az exportálni kívánt esemény mellett, majd válassza az **Exportálás** parancsot a legördülő menüből. 

Az exportálás létrehozásához szükséges lépések végigvezetik a következő lépéseken:

1. Adja meg az **Export nevét**.

1. Az **Események kiválasztása** legördülő listában válassza ki az alapeseményeket és pontosított eseményeket, hogy szerepeljenek az exportálásban. 

1. A **Fájlstruktúra** alatt válassza ki a lépésméretet, ha új fájlokat hoz létre a céltárolóban. Az események importálása folyamatosan meg fog érkezni.

1. Válassza ki az exportálás formátumát. Választhat a **Common Data Model**, a **CSV** és **JSON formátum** közül. Az exportálás más Dynamics 365-alkalmazásokkal való használata a Common Data Model formátum használata ajánlott.

1. A **Célhely kiválasztása** lépésben adja meg a Azure Data Lake Storage Gen 2 helyet.
    1. Az **ADLS Gen 2 fiók neve** annak a tárolófióknak a neve, amelybe menteni szeretné az exportálást. 
    1. A **mappa elérési útja** határozza meg, hogy az exportálás hol tárolható a storage-fiók fájlrendszerében és könyvtárstruktúrájában.
    1. A **megosztott kulcs** az Azure portálon érhető el a storage-fiókhoz.

1. Kijelölések átttekintése és megerősítése.

## <a name="view-and-manage-exports"></a>Exportok megjelenítése és kezelése

Az exportálás beállítása után, a megtekintéséhez lépjen az **Adatok** > **Exportok** lehetőségre. Válassza a **További [...]** lehetőséget meglévő export szerkesztése vagy törlése esetén.


[!INCLUDE[footer-include](../includes/footer-banner.md)]