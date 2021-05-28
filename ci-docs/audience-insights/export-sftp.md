---
title: Customer Insights adatok exportálása a SFTP gazdaszámítógépekhez
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az SFTP helyre.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 3663a48955f0b1db8a96e25403e5f8947bc6a220
ms.sourcegitcommit: e8e03309ba2515374a70c132d0758f3e1e1851d0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/04/2021
ms.locfileid: "5976896"
---
# <a name="export-segment-lists-and-other-data-to-sftp-preview"></a>Szegmenslisták és egyéb adatok exportálása az SFTP-be (előzetes verzió)

Az ügyféladatokat külső alkalmazásokban használhatja, ha exportálja őket egy Biztonságos fájlátviteli protokoll (SFTP) helyre.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

- Egy SFTP állomás és a hozzájuk tartozó hitelesítő adatok elérhetősége.

## <a name="known-limitations"></a>Ismert korlátozások

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

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
