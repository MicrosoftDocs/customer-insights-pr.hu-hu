---
title: Customer Insights adatok exportálása Sendinblue-ba
description: További információ a kapcsolat konfigurálásához és az Sendinblue-ba való exportáláshoz.
ms.date: 10/08/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: b5924b2d4e7f0b11ce6478a31015fcbaaf44ff93
ms.sourcegitcommit: 23c8973a726b15050e368cc6e0aab78b266a89f6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/08/2021
ms.locfileid: "7617788"
---
# <a name="export-segments-to-sendinblue-preview"></a>Szegmensek exportálása Sendinblue-ba (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseinek exportálása kampányok létrehozásához, e-mail-marketing szolgáltatást biztosíthat és az ügyfelek meghatározott csoportját használhatja a Sendinblue szolgáltatással.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

-   [Sendinblue fiókkal](https://www.sendinblue.com/) és a megfelelő rendszergazdai hitelesítő adatokkal rendelkezik.
-   A Sendinblue-ban és a megfelelő azonosítókban vannak meglévő listák.
-   Rendelkezik [konfigurált szegmensekkel](segments.md).
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Exportálásonként legfeljebb 1 millió ügyfélprofil kerül a Sendinblue fájlba.
- Az Sendinblue-ba történő exportálás szegmensekre korlátozódik.
- Az összesen 1 millió ügyfélprofilt vevő szegmensek exportálása akár 90 percet is igénybe vehet. 
- A Sendinblue alkalmazásba exportálható ügyfélprofilok száma a Sendinblue-val kötött szerződéstől függ, és csak korlátozott.

## <a name="set-up-connection-to-sendinblue"></a>Sendinblue-val való kapcsolat beállítása

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Sendinblue** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg **[SendinBlue API-kulcsát](https://developers.sendinblue.com/docs/getting-started#:~:text=Get%20your%20API%20key&text=You%20can%20create%20one%20from,your%20settings%20This%20API%20key)**.

1. Válassza az **Elfogadom** lehetőséget, hogy megerősítse az **Adatvédelem és megfelelőség** opciót, és válassza a **Csatlakozás** lehetőséget, hogy inicializálja a kapcsolatot Sendinblue-val.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot a Sendinblue szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Adja meg **Sendinblue listaazonosítóját** 

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. 

1. Opcionálisan exportálhat **utónév**, **vezetéknév**, és **telefon**-ra,hogy személyre szabottabb e-maileket hozzon létre. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat Sendinblue-ba, engedélyezi az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat. A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy a Sendinblue megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
