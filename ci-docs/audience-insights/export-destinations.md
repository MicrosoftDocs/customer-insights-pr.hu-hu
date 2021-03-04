---
title: Exportálási célhelyek
description: Adatok exportálása és az exportálási célhelyek kezelése.
ms.date: 07/21/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 63caa2ebdd7d637d14ac9c9cc7972095803aee2f
ms.sourcegitcommit: 0260ed244b97c2fd0be5e9a084c4c489358e8d4f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/18/2021
ms.locfileid: "5477136"
---
# <a name="export-destinations-preview-overview"></a>Exportálási célhelyek (előzetes verzió) áttekintése

Az **Exportálási célhelyek** lap megjeleníti az összes olyan helyet, amelyet beállított az adatok exportálási céljának. Az exportáláshoz új célhelyeket is hozzáadhat. Emellett a jelenleg elérhető exportálási lehetőségeket is mutatja. Gyors áttekintést, leírást kaphat, és megtudhatja, mit tehet az egyes bővíthetőség-beállításokkal. Egységesített profilok, intézkedések és szegmensek exportálása a vállalat szempontjából releváns támogatott alkalmazásokhoz.

Válassza a **Felügyelet** > **Exportálási célhelyek** lehetőséget a következő bővíthetőségi lehetőségek megkereséséhez:

- [Dynamics 365 Customer Card bővítmény](customer-card-add-in.md)
- [Facebook Ads Manager összekötő](export-facebook.md)
- [Power Automate-csatlakozó](export-power-automate.md)
- [Power Apps-csatlakozó](export-power-apps.md)
- [Power BI-csatlakozó](export-power-bi.md)
- [Autopilot](export-autopilot.md)
- [DotDigital](export-dotdigital.md)
- [Dynamics 365 Sales](export-dynamics365-sales.md)
- [Dynamics 365 Marketing](export-dynamics365-marketing.md)
- [Azure Blob Storage](export-azure-blob-storage.md)
- [Azure Data Lake Storage Gen2](export-azure-data-lake-storage-gen2.md)
- [SendGrid](export-sendgrid.md)
- [LiveRamp&reg; összekötő](export-liveramp.md)
- [Microsoft Teams robot](export-teams-bot.md)
- [Mailchimp](export-mailchimp.md)
- [Customer Insights API](apis.md)

## <a name="add-a-new-export-destination"></a>Új exportálási cél hozzáadása

Az exportálási célhelyek hozzáadásához [rendszergazdai jogosultságokkal kell rendelkeznie](permissions.md). Ha Microsoft-szolgáltatásokba exportál, akkor feltételezzük, hogy mindkét szolgáltatás ugyanabban a szervezetben van.

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. Váltson a **Saját exportálási célhelyek** lapra.

1. Válassza a **Célhely hozzáadása** lehetőséget új célhely létrehozásához.

1. A **Célhely hozzáadása** ablaktáblában válassza ki az exportálási cél **Típusát** a legördülő listában.

1. Adja meg a szükséges adatokat, és válassza a **Következő** lehetőséget az exportálási cél létrehozásához.

A **Beállítás** lehetőséget is választhatja egy mozaikon a **Felderítés** lapon.

## <a name="view-export-destinations"></a>Exportálási célhely megtekintése

Az exportálási célhelyek létrehozása után ezeket egy táblázatban találja a **Saját exportálási célhelyek** lapon. Ennek a táblának három oszlopa van:

- **mMegjelenítendő név**: A cél létrehozásakor megadott név.
- **Típus**: A cél létrehozásakor beállított exportálási célhely típus.
- **Létrehozva**: A célhely létrehozásának dátuma.

## <a name="edit-an-export-destination"></a>Exportálási cél szerkesztése

1. Jelölje ki a szerkeszteni kívánt Exportálási célhely függőleges három pontját.

   > [!div class="mx-imgBorder"]
   > ![Függőleges három pont](media/export-destinations-page-ellipsis.png "Függőleges három pont")

1. A legördülő menüben kattintson a **Szerkesztés** parancsra.

1. Módosítsa a frissítést igénylő értékeket, és válassza a **Mentés** lehetőséget.

## <a name="export-data-on-demand"></a>Adatok igény szerinti exportálása

Az exportálási célhely összekötőjének konfigurálása után az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt megtörténik.

Ha az adatok exportálását az ütemezett frissítésre való várakozás nélkül szeretné elvégezni, akkor nyissa meg a **Saját exportálási célhelyek** lapot itt: **Rendszergazda** > **Exportálási célhelyek**.

> [!div class="mx-imgBorder"]
> ![Függőleges három pont](media/export-destinations-page-ellipsis.png "Függőleges három pont")

- Válassza az **Exportálás** lehetőséget a lista felett, ha az exportálást egyszerre az összes exportálási célhelyre szeretné futtatni.
- Jelölje ki a három pontot (...) egy listaelem után, majd válassza az **Exportálás** lehetőséget az exportálás egyetlen exportálási célhelyre való futtatásához.

## <a name="remove-an-export-destination"></a>Exportálási cél eltávolítása

Az exportálási célhely eltávolításához induljon a fő **Exportálási célhelyek** oldalról.

1. Jelölje ki az eltávolítani kívánt Exportálási célhely függőleges három pontját.

   > [!div class="mx-imgBorder"]
   > ![Függőleges három pont](media/export-destinations-page-ellipsis.png "Függőleges három pont")

2. Válassza a legördülő menü **Eltávolítás** elemét.

3. Erősítse meg az eltávolítást az **Eltávolítás** lehetőség választásával a megerősítő képernyőn.


[!INCLUDE[footer-include](../includes/footer-banner.md)]