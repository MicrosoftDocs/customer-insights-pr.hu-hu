---
title: Customer Insights adatok exportálása a SFTP gazdaszámítógépekhez
description: Megismerkedhet vele, hogyan konfigurálható egy SFTP-hoszt kapcsolata.
ms.date: 01/27/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 9ec14fafa8f99e34b95349371298082e166535d0
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598388"
---
# <a name="connector-for-sftp-preview"></a>SFTP-összekötő (előzetes verzió)

Ügyféladatait külső alkalmazásokban is használhatja, ha Secure File Transfer Protocol (SFTP) gazdaszámítógépra exportálja.

## <a name="prerequisites"></a>Előfeltételek

- Egy SFTP állomás és a hozzájuk tartozó hitelesítő adatok elérhetősége.

## <a name="connect-to-sftp"></a>Csatlakozás a SFTP-hez

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. Az **SFTP** alatt válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.

1. Adjon meg egy **Felhasználónevet**, **Jelszót**, **Állomásnevet** és **Exportálási mappát** az SFTP-fiókhoz.

1. A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. A sikeres ellenőrzés után válassza ki, hogy szeretné-e exportálni az adatokat **Tömörített** vagy **Nem tömörített** formátumban, válassza ki a **mezőelválasztót** az exportált fájlokhoz.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Az exportálás konfigurálásának megkezdéséhez válassza a **Tovább** lehetőséget.

## <a name="configure-the-export"></a>Az exportálás konfigurálása

1. Jelölje ki az exportálni kívánt entitásokat, például szegmenseket.

   > [!NOTE]
   > Minden egyes kijelölt entitás legfeljebb öt kimeneti fájlt képes exportálni. 

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.

## <a name="known-limitations"></a>Ismert korlátozások

- Az exportálás futtatása a rendszer teljesítményétől függ. A kiszolgáló minimális konfigurációjának ajánlott két processzormag és 1 Gb memória. 
- Az legfeljebb 100 millió ügyfélprofillal rendelkező entitások exportálása 90 percet is igénybe fog venni, ha két processzormag és 1 Gb memória ajánlott minimális konfigurációját használja. 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]