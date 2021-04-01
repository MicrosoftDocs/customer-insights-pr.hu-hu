---
title: Customer Insights adatok exportálása a SendGridbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a SendGriddel.
ms.date: 12/08/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 1a1f679fa42d47d524ebfdd6e931ae2822565f77
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597284"
---
# <a name="connector-for-sendgrid-preview"></a>A SendGrid összekötője (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a SendGrid partnerlistákba, és használja őket kampányokhoz és e-mail marketinghez a SendGridben. 

## <a name="prerequisites"></a>Előfeltételek

-   Rendelkezik [SendGrid-fiókkal](https://sendgrid.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A SendGridben és a megfelelő azonosítókban meglévő partnerlisták találhatók. További információért lásd: [SendGrid – Kapcsolattartók kezelése](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts).
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="connect-to-sendgrid"></a>Csatlakozás a SendGridhez

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **SendGrid** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

   :::image type="content" source="media/export-sendgrid.PNG" alt-text="SendGrid exportálás konfigurációs panel.":::

1. Adja meg **SendGrid API-kulcsot** [SendGrid API-kulcs](https://sendgrid.com/docs/ui/account-and-settings/api-keys/).

1. Adja meg a **[SendGrid lista azonosítóját](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts)**.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget a SendGrid kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév**, **Ország/régió**, **Állam** **Város** és **Irányítószám mezőben**.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. **Javasoljuk, hogy ne exportáljon összesen 100 000-nél több ügyfélprofilt** a SendGridbe. 

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.

## <a name="known-limitations"></a>Ismert korlátozások

- Összesen legfeljebb 100 000 profil a SendGrid számára.
- A SendGridbe való exportálás csak szegmensekre korlátozódik.
- Akár 100 000 profil SendGridbe való exportálása néhány órát is igénybe vehet. 
- A SendGridbe exportálható profilok száma függ a SendGrid szerződésről, és korlátozott.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok SendGridbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a SendGrid megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]