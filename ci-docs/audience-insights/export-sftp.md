---
title: Customer Insights adatok exportálása a SFTP gazdaszámítógépekhez
description: Megismerkedhet vele, hogyan konfigurálható egy SFTP-hoszt kapcsolata.
ms.date: 06/05/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: c2529744d7a26a06324b79cad6a8001d75903545
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643506"
---
# <a name="connector-for-sftp-preview"></a>SFTP-összekötő (előzetes verzió)

Ügyféladatait külső alkalmazásokban is használhatja, ha Secure File Transfer Protocol (SFTP) gazdaszámítógépra exportálja.

## <a name="prerequisites"></a>Előfeltételek

- Az SFTP-hoszt és a megfelelő hitelesítő adatok rendelkezésre állása.

## <a name="connect-to-sftp"></a>Csatlakozás SFTP-hez

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. Az **SFTP** alatt válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.

1. Adjon meg egy **Felhasználónevet**, **Jelszót** és **Eszköznév** értéket az SFTP-fiókhoz. Példa: Ha az SFTP kiszolgáló gyökérkönyvtára/root/folder, és szeretné, hogy az adatok a /root/folder/ci_export_destination_folder mappába exportálódjanak, akkor a gazdaszámítógép legyen: sftp://<server_address>/ci_export_destination_folder".

1. A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. A sikeres ellenőrzés után válassza ki, hogy **Tömörített** vagy **Kibontott** formátumban szeretné exportálni az adatokat, és jelölje ki az exportált fájlokhoz tartozó **mezőhatárolót**.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Az exportálás konfigurálásának megkezdéséhez válassza a **Tovább** lehetőséget.

## <a name="configure-the-connection"></a>A kapcsolat konfigurálása

1. Jelölje ki az **ügyfélattribútumokat** amelyeket exportálni szeretne. Egy vagy több attribútum is exportálható.

1. Válassza a **Következő** lehetőséget.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
