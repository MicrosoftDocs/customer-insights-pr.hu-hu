---
title: Customer Insights-adatok exportálása SFTP-gazdagépekbe (videót tartalmaz)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az SFTP helyre.
ms.date: 06/09/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: b56d628c8286ba6697cccc9b002f609aa929951b
ms.sourcegitcommit: 8e9f0a9693fd8d91ad0227735ff03688fef5406f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/10/2022
ms.locfileid: "8947187"
---
# <a name="export-segments-and-other-data-to-sftp-preview"></a>Szegmensek és egyéb adatok exportálása az SFTP-be (előzetes verzió)

Az ügyféladatokat külső alkalmazásokban használhatja, ha exportálja őket egy Biztonságos fájlátviteli protokoll (SFTP) helyre.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWO94X]

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

- Egy SFTP állomás és a hozzájuk tartozó hitelesítő adatok elérhetősége.

## <a name="known-limitations"></a>Ismert korlátozások

- A tűzfalak mögötti SFTP-célhelyek jelenleg nem támogatottak. 
- Az exportálás futtatása a rendszer teljesítményétől függ. A kiszolgáló minimális konfigurációjának ajánlott két processzormag és 1 Gb memória.
- Az legfeljebb 100 millió ügyfélprofillal rendelkező entitások exportálása 90 percet is igénybe fog venni, ha két processzormag és 1 Gb memória ajánlott minimális konfigurációját használja.

## <a name="set-up-connection-to-sftp"></a>Kapcsolatok beállítása SFTP-hez

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **SFTP** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adjon meg egy **Felhasználónevet**, **Jelszót**, **Állomásnevet** és **Exportálási mappát** az SFTP-fiókhoz.

1. A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. Válassza ki, hogy szeretné-e exportálni a **Tömörített** vagy **Tömörítetlen** adatokat, és a **mező elválasztó karaktert** az exportált fájlokhoz.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az SFTP szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Jelölje ki az exportálni kívánt entitásokat, például szegmenseket.

   > [!NOTE]
   > Az egyes kijelölt entitások exportáláskor legfeljebb öt kimeneti fájlra lesznek felosztva.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.
Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).

> [!TIP]
> A nagy mennyiségű adatot tartalmazó entitások exportálása több CSV-fájlhoz vezethet ugyanabban a mappában minden exportáláshoz. Az exportálások felosztása teljesítménybeli okokból történik, hogy minimalizálja az exportálás befejezéséhez szükséges időt.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.

[!INCLUDE [footer-include](includes/footer-banner.md)]
