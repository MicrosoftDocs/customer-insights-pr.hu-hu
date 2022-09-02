---
title: Ügyfélprofilok gazdagítása egyéni SFTP-importálással (előzetes verzió)
description: Általános információk az SFTP egyéni importálási bővítésről.
ms.date: 08/08/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: 831d1d3d3045379bbc5bcdcd4b05b8a147221f31
ms.sourcegitcommit: b1d06fe26934f12f0c5ed13e8ef1d37e52e67cc7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/08/2022
ms.locfileid: "9237769"
---
# <a name="enrich-customer-profiles-with-sftp-custom-import-preview"></a>Ügyfélprofilok gazdagítása egyéni SFTP-importálással (előzetes verzió)

A Secure File Transfer Protocol (SFTP) egyéni importálás lehetővé teszi, hogy olyan bővítési adatokat importáljon, amik még nem mentek keresztül az adategységesítési folyamaton. Az adatok bevitelének rugalmas, biztonságos és egyszerű módja. Az SFTP egyéni Importálás az [SFTP exportálással](export-sftp.md) együtt használható, amely lehetővé teszi a bővítéshez szükséges ügyfélprofiladatok exportálását. Az adatok ezután feldolgozhatók és bővíthetők, és az egyéni SFTP-importálással visszahozhatja a bővített adatokat a következőre:Dynamics 365 Customer Insights.

## <a name="prerequisites"></a>Előfeltételek

- Az SFTP-állomásra importálandó fájl neve és helye (elérési útja) ismert.

- Elérhető egy *model.json* fájl, amely meghatározza az importálandó adatok Common Data Model sémáját. A fájlnak ugyanabban a könyvtárban kell lennie, mint az importálandó fájlnak.

- SFTP-kapcsolat [van](connections.md) [konfigurálva](#configure-the-connection-for-sftp-custom-import).

## <a name="file-schema-example"></a>Példa fájlséma

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
                    "friendlyName": "Client ID",
                    "dataType": "string"
                },
                {
                    "name": "PreferredCity",
                    "friendlyName": "Preferred city for vacation",
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

## <a name="configure-the-connection-for-sftp-custom-import"></a>Az SFTP egyéni importálás kapcsolatának beállítása

Rendszergazdának [kell](permissions.md#admin) lennie a Customer Insights szolgáltatásban, és rendelkeznie kell annak az SFTP-helynek a felhasználói hitelesítő adataival, URL-címével és portszámával, ahonnan adatokat szeretne importálni.

1. Válassza a Kapcsolat **hozzáadása lehetőséget** a gazdagítás konfigurálásakor, vagy lépjen a **Rendszergazdai** > **kapcsolatok** elemre, és válassza a Beállítás **lehetőséget** az Egyéni importálás csempén.

   :::image type="content" source="media/enrichment-SFTP-connection.png" alt-text="Egyéni kapcsolat importálása konfigurációja lap.":::

1. Adja meg a kapcsolat nevét.

1. Adja meg annak az SFTP-kiszolgálónak az érvényes felhasználónevét, jelszavát és állomás URL-címét, ahol az importálni kívánt adatok találhatók.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

## <a name="configure-the-import"></a>Importálás konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok **gazdagítása lehetőséget** az **egyéni SFTP importálási** csempén.

   :::image type="content" source="media/SFTP_Custom_Import_tile.png" alt-text="SFTP egyéni importálás csempe.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki a gazdagítani kívánt profilt vagy szegmenst. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Válassza a **Következő** lehetőséget.

1. Adja meg az **importálni kívánt adatfájl elérési útját** és **fájlnevét**.

1. Válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimeneti entitás nevét**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

## <a name="view-enrichment-results"></a>Gazdagítási eredmények megtekintése

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]