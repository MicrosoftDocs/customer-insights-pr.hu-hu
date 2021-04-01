---
title: Bővítés SFTP egyéni importálással
description: Általános információk az SFTP egyéni importálási bővítésről.
ms.date: 11/18/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: d9e095ef793cbd25415864f76a541dce68fafe47
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5595858"
---
# <a name="enrich-customer-profiles-with-custom-data-preview"></a>Felhasználói profilok bővítése egyéni adatokkal (előzetes verzió)

A Secure File Transfer Protocol (SFTP) egyéni importálás lehetővé teszi, hogy olyan bővítési adatokat importáljon, amik még nem mentek keresztül az adategységesítési folyamaton. Az adatok bevitelének rugalmas, biztonságos és egyszerű módja. Az SFTP egyéni Importálás az [SFTP exportálással](export-sftp.md) együtt használható, amely lehetővé teszi a bővítéshez szükséges ügyfélprofiladatok exportálását. Az adatok ezután feldolgozhatók és bővíthetők, és az SFTP egyéni importálás segítségével a bővített adat visszavihető a Dynamics 365 Customer Insights célközönség-információk funkciójába.

## <a name="prerequisites"></a>Előfeltételek

Az SFTP egyéni importálás konfigurálásához a következő előfeltételeknek kell teljesülnie:

- Felhasználói hitelesítő adatokkal (felhasználónévvel és jelszóval) rendelkezik ahhoz az SFTP-helyhez, ahol az importálandó adatok származnak.
- Rendelkezik az STFP gazdaszámítógép URL-címével és portszámával (általában 22).
- Rendelkezik a fájl fájlnevével és helyével, amelyet az SFTP gazdaszámítógépen kell importálni.
- Van egy olyan *model.json* fájl, amely megadja az importálandó adatok sémáját. A fájlnak ugyanabban a könyvtárban kell lennie, mint az importálandó fájlnak.
- [Rendszergazda](permissions.md#administrator) engedéllyel rendelkezik.

## <a name="configuration"></a>Konfigurálás

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Az **SFTP egyéni importálási csempén** jelölje be a **Saját adatok bővítése** jelölőnégyzetet.

   > [!div class="mx-imgBorder"]
   > ![SFTP egyéni importálás csempe](media/SFTP_Custom_Import_tile.png "SFTP egyéni importálás csempe")

1. Válassza az **Első lépések** lehetőséget, és adja meg a hitelesítő adatokat és az SFTP kiszolgáló címét. Például sftp://mysftpserver.com:22.

1. Adja meg annak a fájlnak a nevét, amely az adatot tartalmazza, és a fájl elérési útját az SFTP kiszolgálón, ha nem szerepel a gyökérkönyvtárban.

1. A **Csatlakozás egyéni importáláshoz** jelölőnégyzet bejelölésével erősítse meg az összes bemenetet.

   > [!div class="mx-imgBorder"]
   > ![SFTP egyéni importálási konfiguráció úszó panel](media/SFTP_Custom_Import_Configuration_flyout.png "SFTP egyéni importálási konfiguráció úszó panel")

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