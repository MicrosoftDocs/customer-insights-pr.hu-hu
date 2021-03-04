---
title: Valós idejű adatbetöltés és korlátozások.
description: Általános információk a valós idejű képességekről a célközönséggel kapcsolatosan.
ms.date: 10/27/2020
ms.reviewer: nikeller
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 7421ed9d2cb399d546815b2d1b0ea5ec51ca6b6d
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5270283"
---
# <a name="real-time-data-ingestion-preview"></a>Valós idejű adatbetöltés (előzetes verzió)

A közel valós idejű funkció segítségével másodpercek alatt megtekintheti az ügyfelek által a termékekkel vagy szolgáltatásokkal kapcsolatban tett legújabb interakciókat.

[Ütemezett frissítések](system.md#schedule-tab) magában foglal nagy számú rekordot és számos összetett műveletet. Elsőként az adat lekérésre kerül az adatforrásból. Következő lépésként az adatok egységítése megtörténik, majd a rendszer további információkkal bővíti azt. A folyamat minden futtatása percekig vagy órákig is eltarthat.

A valós idejű funkciók azonnali adatokat biztosítanak a fogyasztásról, amíg a következő ütemezett frissítés le nem hívja az adatokat az adatforrásból.

A valós idejű frissítések lejárati idővel rendelkeznek, amely után már nem írják felül az értéket az adatforrásból:

- A profil frissítései 4 órán keresztül megmaradnak
- A tevékenységek 30 napig megmaradnak

Ezek az értékek a módosítható API-hívási paraméterek. Céljuk annak biztosítása, hogy a forrásadatok továbbra is az igazság forrásai legyenek. Ha szeretné, hogy a valós idejű frissítések tovább elérhetők maradjanak, hozzá kell adja őket az adatforráshoz, így azok betölthetők a következő ütemezett frissítés alatt is.

## <a name="real-time-update-of-the-unified-customer-profile-fields"></a>Az egyesített ügyfélprofil mezőinek valós idejű frissítése

A frissített profilok megjelennek az ügyfélkártya nézeten, vagy bármilyen más megjelenítőn, pár másodpercen belül.

Mivel a valós idejű műveletek az adategyesítés megtörténte után történnek, csak az egyesített ügyfelek profiljaira vonatkoznak. Következésképpen a valós idejű Profilbeállítások nem frissítik a mértékeket, a szegmenstagságot vagy a bővítést.

### <a name="limitations"></a>Korlátozások

- Az ügyfelek profiljai frissíthetők, de nem hozhatók létre és nem törölhetők.
- Jelenleg nem lehetséges a frissítések valós idejű exportálása külső rendszerekbe, mint például a Power BI.

## <a name="real-time-creation-of-activities"></a>A tevékenységek valós idejű létrehozása

A valós idejű API-k segítségével közzétehet egy új tevékenységet a forrásrendszeréből (egy egyedi forrásrekordot), egy egyesített ügyfélprofilhoz. Az új tevékenység az egyesített ügyfélprofil idővonalában, másodperceken belül egyesített tevékenységként lesz elérhető. Megtekintheti az idővonalat az ügyfélkártya nézeten, vagy más idővonal-integráción, amit megadott.

> [!NOTE]
>
> - A tevékenységek nem módosíthatók. A létrehozás után nem változnak.
> - Jelenleg a szegmensek és az intézkedések nem frissülnek az új tevékenység alapján.
> - A csak a valós idejű API-val felvett tevékenységek nem részei az exportálásnak, és nem jelennek meg a PowerBI modulban.

A valós idejű API-khoz két módon lehet kapcsolódni:

- [közvetett módon](#connect-via-the-dynamics-365-customer-insights-connector), a [Dynamics 365 Customer Insights.összekötő](https://docs.microsoft.com/connectors/customerinsights/) használatával
- [közvetlenül](#connect-directly-to-the-real-time-api), kóddal

Mindkettőnél az alábbi előfeltételek egyaránt érvényesek:

- A Customer Insights-környezet
- Egyesített ügyfélprofilok
- Konfigurált és futtatott tevékenységek
- Közreműködő vagy rendszergazdai jogosultságok a fiók hitelesítéséhez

## <a name="connect-via-the-dynamics-365-customer-insights-connector"></a>Csatlakozás a Dynamics 365 Customer Insights-összekötőn keresztül

A valós idejű API képes betölteni adatokat egy dedikált Power Platform-összekötőből, a [Dynamics 365 Customer Insights-összekötőből](https://docs.microsoft.com/connectors/customerinsights/) anélkül, hogy írni és üzembe kell helyezni a kódot.    
Az összekötő ugyanolyan valós idejű műveleteket hajthat végre, mint az API-t. A prémium összekötőkhöz érvényes licenccel kell rendelkezniük. További információkért lásd: [Power Apps és Power Automate licencelési GYIK](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq).

- Power Platform [Power Apps és/vagy Power Automate](https://docs.microsoft.com/connectors/)
- Azure [Logic Apps](https://docs.microsoft.com/azure/connectors/apis-list)

A folyamatok létrehozásáról a [Power Automate-dokumentáció](https://docs.microsoft.com/power-automate/) tartalmaz további tudnivalókat.

## <a name="connect-directly-to-the-real-time-api"></a>Közvetlen kapcsolódás a valós idejű API-hoz

Saját folyamatainak létrehozásával és a valós idejű API-khoz kapcsolásával használhatja a valós idejű képességeket.    
A tevékenységet a forrásrendszer vagy a UnifiedActivity formátumában teheti közzé. A formátumot a következő helyre mutató API-hívás indításával szerezheti meg: /api/instances/{instanceId}/manage/entities/UnifiedActivity.

Az API-kra vonatkozó részletek, beleértve a paramétereket és válaszokat, megtalálhatók az **EntityData** szakaszban, a [Customer Insights API-k segédletében](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights). További információkért lásd: [Customer Insights API-k használata](apis.md).

## <a name="understand-your-real-time-usage-with-telemetry"></a>A valós idejű használatát felmérése telemetriával

Tekintse át a valós idejű API-k használatára vonatkozó kérések mennyiségét és az információkat a lehetséges problémákról, melyek a rendszerrel kapcsolatosan felmerülhetnek. A [valós idejű telemetria](system.md#api-usage-tab) elérhető. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]