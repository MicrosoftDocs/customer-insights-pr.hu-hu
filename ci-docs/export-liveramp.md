---
title: Szegmensek exportálása a LiveRampbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a LiveRampbe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 55eacea3af83f46583a3a43797d625479f56586b
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196719"
---
# <a name="export-segments-to-liverampreg-preview"></a>Szegmensek exportálása a LiveRampbe&reg; (előzetes verzió)

Aktiválja az adatokat a LiveRampben, hogy több mint 500 platformmal kapcsolódhasson a digitális és közösségi médiához, illetve a tévéadáshoz. A LiveRamp megoldásban az adatokkal dolgozhat a kampányok megcélzott, letiltási és személyre szabása céljából.

## <a name="prerequisites"></a>Előfeltételek

- Egy LiveRamp-előfizetés az összekötő használatához. Az előfizetés megkezdéséhez [forduljon a LiveRamphez](https://liveramp.com/contact/) közvetlenül. [További információ a LiveRamp előkészítésről](https://liveramp.com/our-platform/data-onboarding/).

## <a name="known-limitations"></a>Ismert korlátozások

- A LiveRamp-exportálás SFTP-exportálást használ. A tűzfalak mögötti SFTP-célhelyek jelenleg nem támogatottak.
- Ha SSH-kulcsot használ a hitelesítéshez, győződjön meg arról, hogy [a titkos kulcsot](/azure/virtual-machines/linux/create-ssh-keys-detailed#basic-example) PEM vagy SSH.COM formátumban hozza létre. Ha Gittet használ, konvertálja a titkos kulcsot exportálással nyissa meg az SSH-t. A következő titkos kulcsformátumok támogatottak:
  - RSA OpenSSL PEM és ssh.com formátumban
  - DSA OpenSSL PEM és ssh.com formátumban
  - ECDSA 256/384/521 OpenSSL PEM formátumban
  - ED25519 és RSA OpenSSH kulcsformátumban
- Az exportálás futtatása a rendszer teljesítményétől függ. A kiszolgáló minimális konfigurációjának ajánlott két processzormag és 1 Gb memória.
- Az legfeljebb 100 millió ügyfélprofillal rendelkező entitások exportálása 90 percet is igénybe fog venni, ha két processzormag és 1 Gb memória ajánlott minimális konfigurációját használja.
- A LiveRamp-be exportálható profilok (vagy adatok) tényleges száma a LiveRamp-pel való előfizetésétől függ.

## <a name="set-up-connection-to-liveramp"></a>Állítsa be a LiveRamp való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a LiveRamp **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza ki, hogy SSH-n vagy felhasználónévn/jelszón keresztül szeretne-e hitelesíteni a kapcsolatot, és adja meg a szükséges adatokat.

1. A LiveRamp kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. A sikeres ellenőrzés után tekintse át az adatvédelmet és a megfelelőséget [, és válassza az](connections.md#data-privacy-and-compliance) Elfogadom **lehetőséget**.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a LiveRamp szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az Adatok **csatlakoztatása mezőben válassza az** E-mail **,** a Név és cím **vagy** a Telefon **lehetőséget** a LiveRamp-nek való küldéshez identitásfeloldáshoz.

   :::image type="content" source="media/export-liveramp-segments.png" alt-text="LiveRamp összekötő attribútum-hozzárendeléssel.":::

1. Az *Ügyfél* entitása megfelelő attribútumainak leképezhető a kijelölt kulcsazonosítóra.

1. Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének LiveRampbe küldéséhez.

   > [!TIP]
   > Ha további kulcsazonosító attribútumokat küld a LiveRamp számára, akkor valószínűleg magasabb szintű egyeztetést fog kapni.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
