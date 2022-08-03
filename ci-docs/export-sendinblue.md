---
title: Szegmensek exportálása Sendinblue-ba (előzetes verzió)
description: További információ a kapcsolat konfigurálásához és az Sendinblue-ba való exportáláshoz.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 816a3b242fadaa5a75db878adf0a76baf638e41c
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196949"
---
# <a name="export-segments-to-sendinblue-preview"></a>Szegmensek exportálása Sendinblue-ba (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseinek exportálása kampányok létrehozásához, e-mail-marketing szolgáltatást biztosíthat és az ügyfelek meghatározott csoportját használhatja a Sendinblue szolgáltatással.

## <a name="prerequisites"></a>Előfeltételek

- Sendinblue-fiók [és](https://www.sendinblue.com/) a megfelelő rendszergazdai hitelesítő adatok.
- Egy [SendinBlue API-kulcs](https://developers.sendinblue.com/docs/getting-started#:~:text=Get%20your%20API%20key&text=You%20can%20create%20one%20from,your%20settings%20This%20API%20key).
- Meglévő listák a Sendinblue-ban és a megfelelő azonosítók.
- [Konfigurált szegmensek](segments.md).
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Sendinblue-ba exportálva akár 1 millió ügyfélprofil is lehet, ami akár 90 percet is igénybe vehet. A Sendinblue-ba exportálható ügyfélprofilok száma a Sendinblue-val kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-sendinblue"></a>Sendinblue-val való kapcsolat beállítása

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Sendinblue **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **SendinBlue API-kulcsot**.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot a Sendinblue szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg Sendinblue **listaazonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Opcionálisan exportálja **utónév**, **vezetéknév** és **telefonját**, hogy személyre szabottabb e-maileket hozzon létre. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
