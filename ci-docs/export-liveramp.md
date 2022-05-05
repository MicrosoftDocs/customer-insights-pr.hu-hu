---
title: LiveRamp összekötő
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a LiveRampbe.
ms.date: 10/08/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 973f69c94c625fe4ec543ca5fb57289c4102ea97
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642908"
---
# <a name="export-segments-to-liverampreg-preview"></a>Szegmensek exportálása a LiveRampbe&reg; (előzetes verzió)

Aktiválja az adatokat a LiveRampben, hogy több mint 500 platformmal kapcsolódhasson a digitális és közösségi médiához, illetve a tévéadáshoz. A LiveRamp megoldásban az adatokkal dolgozhat a kampányok megcélzott, letiltási és személyre szabása céljából.

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

- Az összekötő használatához LiveRamp-előfizetésre van szükség.
- Az előfizetés megkezdéséhez [forduljon a LiveRamphez](https://liveramp.com/contact/) közvetlenül. [További információ a LiveRamp előkészítésről](https://liveramp.com/our-platform/data-onboarding/).

## <a name="set-up-connection-to-liveramp"></a>Állítsa be a LiveRamp való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **LiveRamp** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **felhasználónevet** és a **jelszót** a LiveRamp Secure FTP (SFTP) fiókhoz.
Ezek a hitelesítő adatok eltérhetnek a LiveRamp betanítási hitelesítő adatoktól.

1. A LiveRamp kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. A sikeres ellenőrzés után adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a LiveRamp szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Az **adja meg a kulcs azonosítóját** mezőben jelölje ki az **e-mailt**, a **nevet és a címet** vagy a **telefont**, hogy elküldje a LiveRamp rendszerbe a személyazonosság feloldása céljából.
   > [!div class="mx-imgBorder"]
   > ![LiveRamp összekötő attribútum-hozzárendeléssel.](media/export-liveramp-segments.png "LiveRamp összekötő attribútum-hozzárendeléssel")

1. Az *Ügyfél* entitása megfelelő attribútumainak leképezhető a kijelölt kulcsazonosítóra.

1. Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének LiveRampbe küldéséhez.

   > [!TIP]
   > Ha további kulcsazonosító attribútumokat küld a LiveRamp számára, akkor valószínűleg magasabb szintű egyeztetést fog kapni.

1. Jelölje ki azokat a szegmenseket, amelyeket exportálni szeretne a LiveRamp rendszerébe.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Liveramphez való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Liveramp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.

[!INCLUDE [footer-include](includes/footer-banner.md)]
