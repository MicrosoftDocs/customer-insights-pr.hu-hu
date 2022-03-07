---
title: LiveRamp identitásadatok gazdagítása
description: Gazdagítsa az ügyfélprofilokat LiveRamp adatokkal.
ms.date: 03/02/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: ee65cb49447df61dd5c298a84ad21bc119ead558
ms.sourcegitcommit: bb1f9e96023490ab340c114f54200ab4dd48da78
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/02/2022
ms.locfileid: "8373078"
---
# <a name="enrich-customer-profiles-with-identity-data-from-liveramp-preview"></a>Ügyfélprofilok gazdagítása a LiveRamp azonosító adataival (előzetes verzió) 

A LiveRamp determinisztikus offline identitásmegoldást és az ügyféladatok összevonását biztosítja. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec azonosító grafikonjára, és AbiliTec azonosítókat kaphat. Ezután ezeket az adatokat felhasználhatja az ügyféladatok jobb egyesítéséhez. 

## <a name="prerequisites"></a>Előfeltételek 

A gazdagodás konfigurálásához a következő előfeltételeknek kell teljesülniük: 

- Aktív LiveRamp előfizetéssel rendelkezik. Előfizetés megszerzéséhez lépjen kapcsolatba a LiveRamp-fiókcsapatával, vagy [dynamics@liveramp.com](mailto:dynamics@liveramp.com) további információkért.   

- Aktív AbiliTec-előfizetés ügyfélazonosítóval és titkossággal az API eléréséhez. További információ: [AbiliTec API Developer Hub](https://developers.liveramp.com/abilitec-api/). 

## <a name="supported-countriesregions"></a>Támogatott országok/régiók 

Jelenleg csak az Egyesült Államokban támogatjuk az ügyfélprofilok LiveRamp adatokkal való gazdagítását. 

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása 

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot. 

1. Válassza az **Adatok** gazdagítása lehetőséget az **Identitás** csempén. 

   :::image type="content" source="media/liveramp-tile.png" alt-text="Identitás csempe a gazdagodás áttekintése lapon.":::

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, a Kapcsolat **hozzáadása lehetőséget választva** hozhat létre kapcsolatot. Válassza a LiveRamp **elemet** a legördülő listából. 

1. Válassza a Tovább **lehetőséget**, és válassza ki a **LiveRamp azonosító adataival gazdagítani kívánt Ügyfél adatkészlet**. Kiválaszthatja a Vevő *entitást az összes ügyfélprofil gazdagításához, vagy kiválaszthat egy szegmens* entitást *, hogy csak az* adott szegmensben található vevőprofilokat gazdagítsa. 

1. Válassza a Tovább **lehetőséget**, és határozza meg, hogy az egyesített profilok mely típusú mezőit kell használni a LiveRamp azonos identitásadatainak megkeresésére. A Név és cím, Telefon vagy E-mail **mezők** közül legalább egyre szükség van.**·** **·** 

   > [!TIP]
   > Minél több kulcsfontosságú azonosítót és mezőt térképez fel, annál nagyobb a valószínűsége a magasabb egyezési aránynak 

1. Térképezze fel az egyesített *Ügyfél* entitás mezőit, amelyek a LiveRamp AbiliTec ID grafikonjával való egyeztetéshez lesznek használva. 

   :::image type="content" source="media/liveramp-data-mapping.png" alt-text="Adatleképezési beállítások a LiveRamp gazdagításhoz.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget. 

1. Adjon nevet **a** gazdagításnak és a **output entitásnak**. 

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit. 

## <a name="configure-the-connection-for-liveramp"></a>A LiveRamp kapcsolatának konfigurálása 

A kapcsolatok [konfigurálásához rendszergazdának](connections.md) kell lennie. A gazdagodás konfigurálásakor válassza a Kapcsolat hozzáadása lehetőséget **, vagy lépjen az AdminConnections** **elemre,** > **és válassza a Beállítás** lehetőséget **a** LiveRamp **csempén.** 

:::image type="content" source="media/liveramp-connection.png" alt-text="Konfigurációs ablaktábla a LiveRamp AbiliTec szolgáltatással való kapcsolat beállításához.":::

1. A **megjelenítendő név** adja meg a kapcsolat nevét. 

1. Adjon meg érvényes LiveRamp ügyfélazonosítót és egy titkot. 

1. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével. 

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget. 

1. A kapcsolat befejezéséhez válassza a Mentés **lehetőséget**. 

## <a name="enrichment-results"></a>Bővítési eredmények 

A gazdagítási folyamat elindításához válassza a Futtatás parancsot a parancssávról. Azt is lehetővé teheti, hogy a rendszer automatikusan futtassa a gazdagodást az [ütemezett frissítés](system.md#schedule-tab) részeként. A feldolgozási idő az ügyféladatok mennyiségétől függ. 

Miután a gazdagodási folyamat befejeződött, áttekintheti az újonnan gazdagodott ügyfélprofilok adatait aMy gazdagodások **alatt**. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is. 

Az egyes gazdagított profil részletes nézetét a Bővített **adatok megtekintése lehetőséget választva** érheti el. 

## <a name="next-steps"></a>További lépések

Építsen a bővített ügyféladatokra. Az AbiliTec-i edd-kkel az ügyfélprofilokat személyalapú nézetbe konszolidálja. 
[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség 

Ha engedélyezi Dynamics 365 Customer Insights az adatok LiveRamp-nak történő továbbítását, engedélyezi az adatok átvitelét a megfelelőségi határon Dynamics 365 Customer Insights kívül, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős annak biztosításáért, hogy a LiveRamp megfeleljen az Ön esetleges adatvédelmi vagy biztonsági kötelezettségeinek. További információt a [Microsoft adatvédelmi nyilatkozatában](https://go.microsoft.com/fwlink/?linkid=396732) talál. A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
