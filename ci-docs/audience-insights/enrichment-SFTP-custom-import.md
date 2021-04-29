---
title: Bővítés SFTP egyéni importálással
description: Általános információk az SFTP egyéni importálási bővítésről.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: a2d450635c19432bdd88db74b61c17febdeb568d
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896284"
---
# <a name="enrich-customer-profiles-with-custom-data-preview"></a>Felhasználói profilok bővítése egyéni adatokkal (előzetes verzió)

A Biztonságos fájlátviteli protokoll (SFTP) egyéni importálás lehetővé teszi olyan adatok importálását, amelyeknek nem kell végigmenniük az adategyesítési folyamaton. Az adatok bevitelének rugalmas, biztonságos és egyszerű módja. Az SFTP egyéni Importálás az [SFTP exportálással](export-sftp.md) együtt használható, amely lehetővé teszi a bővítéshez szükséges ügyfélprofiladatok exportálását. Az adatok ezután feldolgozhatók és bővíthetők, és az SFTP egyéni importálás segítségével a bővített adat visszavihető a Dynamics 365 Customer Insights célközönség-információk funkciójába.

## <a name="prerequisites"></a>Előfeltételek

Az SFTP egyéni importálás konfigurálásához a következő előfeltételeknek kell teljesülnie:

- Az SFTP állomásra importálni kívánt fájl neve és helye (elérési útja) megvan.
- Van egy *model.json* fájl, amely megadja az importálni kívánt adatok [Common Data Model sémáját](/common-data-model/). A fájlnak ugyanabban a könyvtárban kell lennie, mint az importálandó fájlnak.
- Egy SFTP-kapcsolatot már konfigurált egy rendszergazda, *vagy* Ön rendelkezik a [rendszergazdai](permissions.md#administrator) engedélyekkel. Ahhoz az SFTP-helyhez, ahonnan az adatokat importálni szeretné, szüksége lesz a felhasználói hitelesítő adatokra, az URL-címre és a portszámra.


## <a name="configure-the-import"></a>Importálás konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Az **SFTP egyéni importálási csempe** lehetőségen válassza az **Adatok bővítése**, majd az **Első lépések** lehetőséget.

   :::image type="content" source="media/SFTP_Custom_Import_tile.png" alt-text="SFTP egyéni importálás csempe.":::

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, akkor a legördülő menüből válassza ki a **Kapcsolat hozzáadása** és az **SFTP Egyéni importálás** lehetőséget a kapcsolat létrehozásához.

1. A kijelölt kapcsolat megerősítéséhez válassza a **Csatlakozás egyéni importáláshoz** lehetőséget.

1.  Válassza a **Következő** lehetőséget, és adja meg az importálni kívánt adatfájl **Fájlnevét** és **Elérési** útját.

    :::image type="content" source="media/enrichment-SFTP-path-and-filename.png" alt-text="Képernyőkép készítése az adathely megadásakor.":::

1. Válassza a **Következő** lehetőséget, és adja meg a bővítés nevét és a kimeneti entitás nevét. 

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="configure-the-connection-for-sftp-custom-import"></a>Az SFTP egyéni importálás kapcsolatának beállítása 

A kapcsolatok konfiguráljához rendszergazdának kell lennie. A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget az Egyéni importálás csempén.

1. Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.

1. Az importálni kívánt adatokkal érvényes felhasználónevet, jelszót és állomás URL-címet adjon meg az STFP kiszolgáló számára.

1. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezését követően a kapcsolat menthető a **Mentés** gombra kattintással.

> [!div class="mx-imgBorder"]
   > ![Az Experian kapcsolat konfigurációs oldala](media/enrichment-SFTP-connection.png "Az Experian kapcsolat konfigurációs oldala")


## <a name="defining-field-mappings"></a>Mezőleképezések meghatározása 

Az SFTP-kiszolgálón importálandó fájlt tartalmazó könyvtárnak tartalmaznia kell egy *model.json* fájlt is. Ez a fájl határozza meg az adatok importálásához használandó sémát. A sémának a [Common Data Model](/common-data-model/) használatával kell megadnia a mező leképezését. A model.json fájl egyszerű példája a következőképpen néz ki:

```
{
    "name": "EnrichmentFromMicrosoft",
    "description": "Model containing data enrichment",
    "entities": [
        {
            "name": "CustomImport",
            "attributes": [
                {
                    "name": "CustomerId",
                    "friendlyName": "Client id",
                    "dataType": "string"
                },
                {
                    "name": "PreferredCity",
                    "friendlyName": "Preferred City for vacation",
                    "dataType": "string"
                },
                {
                    "name": "PreferredTransportation",
                    "friendlyName": "Preferred transportation",
                    "dataType": "string"
                }
            ],
            "annotations": [
                {
                    "name": "c360:PrimaryKey",
                    "value": "CustomerId"
                }
            ]
        }
    ],
    "modifiedTime": "2020-01-02T12:00:00+08:00",
    "annotations": [
        {
            "name": "testAnnotation",
            "value": "testValue"
        }
    ]
}
```

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az importálandó adatok méretétől és az SFTP kiszolgálóval létesített kapcsolattól függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan importált egyéni bővítési adatokat a **Saját bővítések** részben. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>Következő lépések

Építsen a bővített ügyféladatokra. Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) és [exportálja az adatot](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
