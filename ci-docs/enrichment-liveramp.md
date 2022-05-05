---
title: LiveRamp identitásadatok gazdagítása
description: Bővítse az ügyfélprofilokat LiveRamp-adatokkal.
ms.date: 03/02/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 0727818f6df565d9a031966a68d521ae7167e484
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642568"
---
# <a name="enrich-customer-profiles-with-identity-data-from-liveramp-preview"></a>Ügyfélprofilok gazdagítása a LiveRamp (Preview) identitásadataival 

A LiveRamp determinisztikus offline identitásfeloldást és az ügyféladatok összevonását biztosítja. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásdiagramra, és AbiliTec azonosítókat kaphat. Ezután ezeket az azonosítókat használhatja az ügyféladatok jobb egyesítéséhez. 

## <a name="prerequisites"></a>Előfeltételek 

A gazdagodás konfigurálásához a következő előfeltételeknek kell teljesülniük: 

- Aktív LiveRamp-előfizetéssel rendelkezik. Előfizetés megszerzéséhez lépjen kapcsolatba LiveRamp-fiókcsapatával, vagy [dynamics@liveramp.com](mailto:dynamics@liveramp.com) további információért.   

- Aktív AbiliTec-előfizetés ügyfélazonosítóval és titkossággal az API eléréséhez. További információ: [AbiliTec API Developer Hub](https://developers.liveramp.com/abilitec-api/). 

## <a name="supported-countriesregions"></a>Támogatott országok/régiók 

Jelenleg csak az Egyesült Államokban támogatjuk az ügyfélprofilok LiveRamp-adatokkal való gazdagítását. 

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása 

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot. 

1. Válassza **az Adatok** gazdagítása lehetőséget az **Identitás** csempén. 

   :::image type="content" source="media/liveramp-tile.png" alt-text="Identitáscsempét a gazdagodás áttekintése lapon.":::

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, kapcsolatot hozhat létre a Kapcsolat hozzáadása **választógombbal**. Válassza a **LiveRamp** elemet a legördülő listából. 

1. Válassza a Tovább **lehetőséget**, és válassza ki az **Ügyfél adatkészlet**, amelyet a LiveRamp identitásadataival szeretne gazdagítani. Kiválaszthatja a Vevő *entitást az összes ügyfélprofil gazdagításához, vagy kiválaszthat egy szegmens* entitást *, hogy csak az* adott szegmensben található ügyfélprofilokat gazdagítsa. 

1. Válassza **a Tovább lehetőséget**, és határozza meg, hogy az egyesített profilok mely mezőit használja a LiveRamp megfelelő identitásadatainak kereséséhez. Legalább az egyik mező **neve és címe**, **telefon** vagy **e-mail** szükséges. 

   > [!TIP]
   > Minél több kulcsazonosítót és mezőt térképez fel, annál nagyobb a valószínűsége a magasabb egyezési aránynak 

1. Rendelje hozzá az egyesített *Ügyfél* entitás mezőit, amelyek a LiveRamp AbiliTec ID grafikonjával való egyeztetéshez lesznek használva. 

   :::image type="content" source="media/liveramp-data-mapping.png" alt-text="A LiveRamp-gazdagodás adatleképezési beállításai.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget. 

1. **Adjon nevet** a gazdagodásnak és a **Kimeneti entitásnak**. 

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit. 

## <a name="configure-the-connection-for-liveramp"></a>A LiveRamp kapcsolatának konfigurálása 

A kapcsolatok [konfigurálásához rendszergazdának](connections.md) kell lennie. Válassza **a Kapcsolat** hozzáadása lehetőséget a gazdagodás konfigurálásakor, vagy lépjen **az AdminConnections** > **elemre,** és válassza **a Beállítás** lehetőséget a **LiveRamp** csempén. 

:::image type="content" source="media/liveramp-connection.png" alt-text="Konfigurációs ablaktábla a LiveRamp AbiliTec szolgáltatással való kapcsolat beállításához.":::

1. A **megjelenítendő név** adja meg a kapcsolat nevét. 

1. Adjon meg egy érvényes LiveRamp ügyfélazonosítót és egy titkot. 

1. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével. 

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget. 

1. A kapcsolat befejezéséhez válassza a Mentés **lehetőséget**. 

## <a name="enrichment-results"></a>Bővítési eredmények 

A gazdagodási folyamat elindításához válassza a Futtatás parancssávról lehetőséget. Azt is engedélyezheti, hogy a rendszer automatikusan futtassa a gazdagodást a [tervezett frissítés](system.md#schedule-tab) részeként. A feldolgozási idő az ügyféladatok mennyiségétől függ. 

A gazdagodási folyamat befejezése után áttekintheti az újonnan gazdagított ügyfélprofilok adatait a Saját gazdagodások **alatt**. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is. 

Az egyes bővített profilok részletes nézetét a Gazdagított **adatok megtekintése lehetőséget választva** érheti el. 

## <a name="next-steps"></a>További lépések

Építsen a bővített ügyféladatokra. Az AbiliTec azonosítók segítségével konszolidálhatja az ügyfélprofilokat egy személyalapú nézetben. 
[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség 

Ha engedélyezi Dynamics 365 Customer Insights az adatok továbbítását a LiveRamp-nak, engedélyezi az adatok átvitelét a megfelelőségi határokon kívülre Dynamics 365 Customer Insights, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat is. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős annak biztosításáért, hogy a LiveRamp megfeleljen az Esetleges adatvédelmi vagy biztonsági kötelezettségeinek. További információt a [Microsoft adatvédelmi nyilatkozatában talál](https://go.microsoft.com/fwlink/?linkid=396732). A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést. 


[!INCLUDE [footer-include](includes/footer-banner.md)]
