---
title: Szegmensek exportálása a SendGridbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a SendGridbe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: f2990ad410dda0cbf952f82f3fc30b3a53a7bcd4
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196995"
---
# <a name="export-segments-to-sendgrid-preview"></a>Szegmensek exportálása a SendGridbe (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a SendGrid partnerlistákba, és használja őket kampányokhoz és e-mail marketinghez a SendGridben.

## <a name="prerequisites"></a>Előfeltételek

- Egy [SendGrid-fiók](https://sendgrid.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- [A SendGrid](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts) meglévő névjegyzékei és a megfelelő azonosítók.
- Egy [SendGrid API-kulcs](https://sendgrid.com/docs/ui/account-and-settings/api-keys/).
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Összesen akár 100 000 ügyfélprofil is lehet a SendGridhez, ami akár néhány órát is igénybe vehet. A SendGridbe exportálható ügyfélprofilok száma a SendGriddel kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-sendgrid"></a>Állítsa be a SendGriddel való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a SendGrid **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **SendGrid API-kulcsot**.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a SendGrid szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg a **SendGrid listaazonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Igény szerint olyan mezőket is kiválaszthat, mint **a utónév**, **a vezetéknév**, **az Ország/régió**, **az Állam**, **a Város** és **az Irányítószám**.

1. Válassza ki az exportálni kívánt szegmenseket az ismert korlátozásoknak megfelelően.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
