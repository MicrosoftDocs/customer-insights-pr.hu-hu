---
title: Adatok exportálása SFTP-gazdagépekre (előzetes verzió) (videót tartalmaz)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az SFTP helyre.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: b12d25ecbd2e5fb31d7d5a6bb775dc3e7c1bf007
ms.sourcegitcommit: 5807b7d8c822925b727b099713a74ce2cb7897ba
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/28/2022
ms.locfileid: "9207232"
---
# <a name="export-data-to-sftp-hosts-preview"></a>Adatok exportálása SFTP-gazdagépekre (előzetes verzió)

Az ügyféladatokat külső alkalmazásokban használhatja, ha exportálja őket egy Biztonságos fájlátviteli protokoll (SFTP) helyre.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWO94X]

## <a name="prerequisites"></a>Előfeltételek

- Egy SFTP állomás és a hozzájuk tartozó hitelesítő adatok elérhetősége.

## <a name="known-limitations"></a>Ismert korlátozások

- A tűzfalak mögötti SFTP-célhelyek jelenleg nem támogatottak.
- Az exportálás futtatása a rendszer teljesítményétől függ. A kiszolgáló minimális konfigurációjának ajánlott két processzormag és 1 Gb memória.
- Akár 100 millió ügyfélprofil is eltarthat, ami 90 percet is igénybe vehet, ha két processzormag és 1 Gb memória ajánlott minimális konfigurációját használja.
- Ha SSH-kulcsot használ a hitelesítéshez, győződjön meg arról, hogy [a titkos kulcsot](/azure/virtual-machines/linux/create-ssh-keys-detailed#basic-example) PEM vagy SSH.COM formátumban hozza létre. Ha Gittet használ, konvertálja a titkos kulcsot exportálással nyissa meg az SSH-t. A következő titkos kulcsformátumok támogatottak:
  - RSA OpenSSL PEM és ssh.com formátumban
  - DSA OpenSSL PEM és ssh.com formátumban
  - ECDSA 256/384/521 OpenSSL PEM formátumban
  - ED25519 és RSA OpenSSH kulcsformátumban

## <a name="set-up-connection-to-sftp"></a>Kapcsolatok beállítása SFTP-hez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd az SFTP **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza ki, hogy SSH-n vagy felhasználónévn/jelszón keresztül szeretne-e hitelesíteni a kapcsolatot, és adja meg a szükséges adatokat. Ha SSH-kulcsot használ a hitelesítéshez, győződjön meg arról, hogy [a titkos kulcsot](/azure/virtual-machines/linux/create-ssh-keys-detailed#basic-example) PEM vagy SSH.COM formátumban hozza létre. Ha Gittet használ, konvertálja a titkos kulcsot exportálással nyissa meg az SSH-t. A következő titkos kulcsformátumok támogatottak:
   - RSA OpenSSL PEM és ssh.com formátumban
   - DSA OpenSSL PEM és ssh.com formátumban
   - ECDSA 256/384/521 OpenSSL PEM formátumban
   - ED25519 és RSA OpenSSH kulcsformátumban

1. A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az SFTP szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki, hogy szeretné-e exportálni a **Tömörített** vagy **Tömörítetlen** adatokat, és a **mező elválasztó karaktert** az exportált fájlokhoz.

1. Válassza ki az exportálni kívánt entitásokat, például szegmenseket.

   > [!NOTE]
   > Exportáláskor minden kiválasztott entitás legfeljebb öt kimeneti fájlra lesz felosztva.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

> [!TIP]
> A nagy mennyiségű adatot tartalmazó entitások exportálása több CSV-fájlhoz vezethet ugyanabban a mappában minden exportáláshoz. Az exportálások felosztása teljesítménybeli okokból történik, hogy minimalizálja az exportálás befejezéséhez szükséges időt.

[!INCLUDE [footer-include](includes/footer-banner.md)]
