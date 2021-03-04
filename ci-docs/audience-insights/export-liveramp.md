---
title: LiveRamp összekötő
description: Megismerkedhet vele, hogyan exportálhatja az adatokat a LiveRamp megoldásba.
ms.date: 12/02/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 64d781f52e8124fc3e83a7b84f468830c5249cfd
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5270161"
---
# <a name="liverampreg-connector-preview"></a>LiveRamp&reg; összekötő (előzetes verzió)

Az adatok aktiválása a LiveRamp megoldásban, hogy a digitális, a közösségi és a TV-ökoszisztémákban több mint 500 platformot csatlakoztasson. A LiveRamp megoldásban az adatokkal dolgozhat a kampányok megcélzott, letiltási és személyre szabása céljából.

## <a name="prerequisites"></a>Előfeltételek

- Az összekötő használatához LiveRamp-előfizetésre van szükség.
- Az előfizetés megkezdéséhez [forduljon a LiveRamphez](https://liveramp.com/contact/) közvetlenül. [További információ a LiveRamp előkészítésről](https://liveramp.com/our-platform/data-onboarding/).

## <a name="connect-to-liveramp"></a>LiveRamp csatlakoztatás

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. A **LiveRamp** csempében válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.

1. Adja meg a **felhasználónevet** és a **jelszót** a LiveRamp Secure FTP (SFTP) fiókhoz.
Ezek a hitelesítő adatok eltérhetnek a LiveRamp betanítási hitelesítő adatoktól.

1. A LiveRamp kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. A sikeres ellenőrzés után adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.

1. A LiveRamp csatlakozó beállításához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **adja meg a kulcs azonosítóját** mezőben jelölje ki az **e-mailt**, a **nevet és a címet** vagy a **telefont**, hogy elküldje a LiveRamp rendszerbe a személyazonosság feloldása céljából.

1. Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.

1. Válassza az **Attribútum hozzáadása** lehetőséget, ha további attribútumokat szeretne leképezni, amelyeket el szeretne küldeni a LiveRamp rendszerébe.

   > [!TIP]
   > Ha további kulcsazonosító attribútumokat küld a LiveRamp számára, akkor valószínűleg magasabb szintű egyeztetést fog kapni.

1. Jelölje ki azokat a szegmenseket, amelyeket exportálni szeretne a LiveRamp rendszerébe.

1. Válassza a **Mentés** parancsot.

> [!div class="mx-imgBorder"]
> ![LiveRamp összekötő attribútum-hozzárendeléssel](media/export-liveramp-segments.png "LiveRamp összekötő attribútum-hozzárendeléssel")

## <a name="export-the-data"></a>Az adatok exportálása

Az exportálás hamarosan megkezdődik, ha az exportálás minden előfeltétele befejeződött. Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.
Miután az exportálás sikeresen befejeződött, bejelentkezhet az LiveRamp előkészítésbe az adatok aktiválásához és terjesztéséhez.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Liveramphez való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Liveramp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.

[!INCLUDE[footer-include](../includes/footer-banner.md)]