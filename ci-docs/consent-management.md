---
title: Az ügyfél hozzájárulásának használata
description: Tisztelje meg az ügyfelek hozzájárulási preferenciáit a Customer Insights szolgáltatásban a hozzájárulási adatok importálásával.
ms.date: 06/07/2022
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 6c951219410b55adc34691f677158b574cea1e01
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9245698"
---
# <a name="use-customer-consent"></a>Az ügyfél hozzájárulásának használata

Az adatvédelmi és adatvédelmi szabályok feljogosítják az egyéneket arra, hogy szabályozzák, hogyan használja fel egy szervezet a személyes adataikat. Ilyen szabályozás például az Európai Unió általános adatvédelmi rendelete vagy az Egyesült Államokban a kaliforniai fogyasztói adatvédelmi törvény. Ezek a szabályok lehetővé teszik az emberek számára, hogy leiratkozzanak arról, hogy személyes adataikat harmadik felek gyűjtsék, dolgozzák fel vagy osszák meg velük.  

Az ügyfelek dönthetnek úgy, hogy visszavonják vagy visszatartják hozzájárulásukat bizonyos kapcsolatfelvételi formákhoz. Azt is kérhetik, hogy tiltsa le őket személyes adataik gyűjtéséről, tárolásáról, felhasználásáról vagy értékesítéséről. Fontos, hogy szervezete tiszteletben tartsa az összes ügyfél beleegyezését és adatvédelmi beállításait.  

Dynamics 365 Customer Insights segít az ügyfelek kéréseinek teljesítésében azáltal, hogy importálja és tárolja preferenciáikat az egységes ügyfélprofilok részeként.

Ha a hozzájárulási adatokat az ügyfélprofiloktól elkülönítve tárolja, [adja hozzá a hozzájárulási adatokat új adatforrás](#import-and-unify-consent-data). A hozzájárulási adatokat tartalmazó adatforrás hozzáadjuk az adategyesítési folyamathoz. A hozzájárulási adatok és az ügyfélprofilok sikeres egyesítése ezután egységes ügyfélprofilokhoz vezet, amelyek tartalmazzák a hozzájárulási információkat. Az olyan ügyfélprofilok esetében, amelyek már tartalmaznak hozzájárulási információkat, lépjen közvetlenül a [használati hozzájárulási adatok](#use-consent-data) szakaszba.

## <a name="prerequisites"></a>Előfeltételek

A következő információknak kell rendelkezésre állniuk a forrásadatokban a hozzájárulási adatok más ügyfélprofilokkal való egységesítéséhez:

- Másodlagos kulcs, hogy leképezze a hozzájárulási adatokat a felhasználói profilokra a Customer Insights szolgáltatásban. Például egy e-mail-cím vagy egy telefonszám.
- Hozzájárulási érték az ügyfél hozzájárulásának állapotának meghatározásához.

Fontolja meg a következő *opcionális* információk hozzáadását:

- Elsődleges kulcs a hozzájárulási állapot frissítéséhez, ha az ügyfél módosítást kér.
- A hozzájárulás típusa, ha az ügyféladatok feldolgozásának egynél több módja van.
- A hozzájárulás dátuma vagy bármely más, a hozzájárulási forgatókönyvek szempontjából releváns adat.

Példatábla egy egyszerű hozzájárulási adatbázisra több hozzájárulási lehetőséggel:

|Hozzájárulás azonosítója (elsődleges kulcs)   |E-mail cím (másodlagos kulcs)  |Hozzájárulási lehetőség  |Hozzájárulási érték  |
|---------|---------|---------|---------|
|0    |  holly@contoso.com       |  Hírlevél       |  Hamis       |
|2    |  holly@contoso.com       |  Termékfrissítések       |  Igaz       |
|3    |  frank@contoso.com       |  Hírlevél       | Igaz        |
|4    |  frank@contoso.com       |  Termékfrissítések       |  Hamis       |

## <a name="import-and-unify-consent-data"></a>Hozzájárulási adatok importálása és egységesítése

A hozzájárulási adatokat ugyanúgy importálhatja, mint ahogyan más adatforrásokat is betölt a Customer Insights szolgáltatásba. A támogatott adatforrásokkal és importálásukkal kapcsolatos további információkért lásd: [Adatforrások áttekintése](data-sources.md).

Az adatforrások egységesítésével kapcsolatos további információkért lásd: [Adategyesítés áttekintése](data-unification.md).

## <a name="use-consent-data"></a>Hozzájárulási adatok felhasználása

Miután a hozzájárulási adatok az egységes ügyfélprofilok részét képezik, felhasználhatja azokat a Customer Insights szolgáltatásban. Hozzon létre például egy szegmenst egy szabállyal, amely biztosítja, hogy tiszteletben tartsa az ügyfelek adatvédelmi és adatvédelmi beállításait. A hozzájárulási beállításokat támogató szabályok arra szolgálnak, hogy a rendszer profilattribútumok alapján kizárja a felhasználókat egy szegmensből. Adjon hozzá egy szabályt egy olyan szegmenshez, amely kizárja azokat az ügyfélprofilokat, amelyek nem adtak hozzájárulást a kapcsolatfelvételhez.

A fenti mintatáblázatra hivatkozva egy szegmens tartalmazhatja ezt a szabályt:`Consent option=Newsletter & Consent value=True`. Ez a konfiguráció azt eredményezi, hogy egy olyan szegmens, amely tiszteletben tartja a kapcsolattartási beállításokat, hogy hírlevelet küldjön.

További információ a szegmensek felépítéséről: [Szegmensek](segment-builder.md) létrehozása.

A szegmens létrehozása után a számos [exportálási lehetőség](export-destinations.md) egyikével használhatja a szegmenst más alkalmazásokban.

## <a name="ensure-updated-consent-status"></a>Frissített hozzájárulási állapot biztosítása

Fontos, hogy folyamatosan frissítse az ügyfelek hozzájárulási állapotát. A Customer Insights ütemezett frissítése mindig az adatforrások legújabb állapotát importálja. Ezeket az információkat ezután az adatok egyesítése révén dolgozzák fel, és frissített ügyfélprofilokat eredményeznek. Ezeket a frissített profilokat a rendszer a szegmensek frissítésére használja, hogy a legfrissebb információkkal dolgozzon.

Más szóval győződjön meg arról, hogy a Customer Insights szolgáltatásba importált forrásadatok mindig a legfrissebb információkkal rendelkeznek.

További információ: [Szegmensek manuális](segments.md#refresh-segments) frissítése vagy [ütemezett frissítés](schedule-refresh.md) konfigurálása.

[!INCLUDE [footer-include](includes/footer-banner.md)]
