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
ms.openlocfilehash: f92b36ac5364ea8586f9cbba7ba03178641555c0
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6304653"
---
# <a name="enrich-customer-profiles-with-custom-data-preview"></a>Felhasználói profilok bővítése egyéni adatokkal (előzetes verzió)

A Secure File Transfer Protocol (SFTP) egyéni importálás lehetővé teszi, hogy olyan bővítési adatokat importáljon, amik még nem mentek keresztül az adategységesítési folyamaton. Az adatok bevitelének rugalmas, biztonságos és egyszerű módja. Az SFTP egyéni Importálás az [SFTP exportálással](export-sftp.md) együtt használható, amely lehetővé teszi a bővítéshez szükséges ügyfélprofiladatok exportálását. Ezután az adatok feldolgozhatók és bővíthetők, és az SFTP egyéni importálása felhasználható a bővített adatok visszahozására a Dynamics 365 Customer Insights célközönségi elemzések lehetőségeihez.

## <a name="prerequisites"></a>Előfeltételek

Az SFTP egyéni importálás konfigurálásához a következő előfeltételeknek kell teljesülnie:

- Az SFTP állomáson importálni kívánt fájl neve és helye (elérési útvonal) megvan.
- Van egy *model.json* fájl, amely megadja az importálni kívánt adatok [Common Data Model sémáját](/common-data-model/). A fájlnak ugyanabban a könyvtárban kell lennie, mint az importálandó fájlnak.
- Egy SFTP-kapcsolatot már konfigurált egy rendszergazda, *vagy* Ön rendelkezik a [rendszergazdai](permissions.md#administrator) engedélyekkel. Ahhoz az SFTP-helyhez, ahonnan az adatokat importálni szeretné, szüksége lesz a felhasználói hitelesítő adatokra, az URL-címre és a portszámra.


## <a name="configure-the-import"></a>Importálás konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Az **SFTP egyéni importálási csempe** lehetőségen válassza az **Adatok bővítése**, majd az **Első lépések** lehetőséget.

   :::image type="content" source="media/SFTP_Custom_Import_tile.png" alt-text="SFTP egyéni importálás csempe.":::

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, akkor kapcsolatot hozhat létre a **Kapcsolat hozzáadása** majd **SFTP Egyéni Importálás** kiválasztásával a legördülő listából.

1. A kijelölt kapcsolat megerősítéséhez válassza a **Csatlakozás egyéni importáláshoz** lehetőséget.

1.  Válassza a **Tovább** lehetőséget, és írja be az importálni kívánt adatfájl **Elérési útvonal** és **Fájlnév** részleteit.

    :::image type="content" source="media/enrichment-SFTP-path-and-filename.png" alt-text="Képernyőkép készítése az adathely megadásakor.":::

1. Válassza a **Következő** lehetőséget, és adja meg a bővítés nevét és a kimeneti entitás nevét. 

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="configure-the-connection-for-sftp-custom-import"></a>Az SFTP egyéni importálás kapcsolatának beállítása 

A kapcsolatok konfiguráljához rendszergazdának kell lennie. A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget az Egyéni importálás csempén.

1. Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.

1. Adja meg annak az SFTP-kiszolgálónak az érvényes felhasználónevét, jelszavát és állomás URL-címét, ahol az importálni kívánt adatok találhatók.

1. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezését követően a kapcsolat menthető a **Mentés** lehetőség kiválasztásával.

   > [!div class="mx-imgBorder"]
   > ![Experian kapcsolati konfiguráció oldal](media/enrichment-SFTP-connection.png "Experian kapcsolati konfiguráció oldal")


## <a name="defining-field-mappings"></a>Mezőleképezések meghatározása 

Az SFTP-kiszolgálón importálandó fájlt tartalmazó könyvtárnak tartalmaznia kell egy *model.json* fájlt is. Ez a fájl határozza meg az adatok importálásához használandó sémát. A sémának használnia kell a [Közös Adatmodellt](/common-data-model/) a mező leképezésének megadásához. A model.json fájl egyszerű példája a következőképpen néz ki:

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

Építsen a bővített ügyféladatokra. Hozzon létre [szegmenseket](segments.md) és [intézkedéseket](measures.md), továbbá [exportálja az adatokat](export-destinations.md) , hogy személyre szabott élményt nyújtson ügyfeleinek.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
