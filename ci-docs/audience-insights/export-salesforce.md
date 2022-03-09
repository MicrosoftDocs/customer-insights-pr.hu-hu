---
title: Customer Insights-adatok exportálása a Salesforce Marketing Cloud-ba
description: További információ a kapcsolat konfigurálásához és a Salesforce Marketing Cloud-ba való exportáláshoz.
ms.date: 07/23/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 17a608a64433cdc395e0b503a42b6290db5c39ec
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8230207"
---
# <a name="export-segments-and-other-data-to-salesforce-marketing-cloud-preview"></a>Szegmensek és egyéb adatok exportálása a Salesforce Marketing Cloud-ba (előzetes verzió)

Használja az ügyféladatokat a Salesforce Marketing Cloud szolgáltatásban egy Biztonságos Fájlátviteli Protokoll (SFTP) helyen keresztül történő exportálással.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

- Egy SFTP állomás és a hozzájuk tartozó rendszergazdai hitelesítő adatok elérhetősége. [Az SFTP-helyek beállítása a Salesforce Marketing Cloud szolgáltatáshoz](https://help.salesforce.com/articleView?id=sf.mc_es_configure_enhanced_ftp.htm&type=5) 

## <a name="set-up-the-connection-to-salesforce-marketing-cloud"></a>A Salesforce Marketing Cloud kapcsolatának beállítása

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Salesforce Marketing Cloud** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adjon meg egy **Felhasználónevet**, **Jelszót**, **Állomásnevet** és **Exportálási mappát** az SFTP-fiókhoz.

1. A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az SFTP szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Válassza ki, hogy szeretné-e exportálni a **Tömörített** vagy **Tömörítetlen** adatokat, és a **mező elválasztó karaktert** az exportált fájlokhoz.

1. Jelölje ki az exportálni kívánt entitásokat, például szegmenseket.

   > [!NOTE]
   > Az egyes kijelölt entitások exportáláskor legfeljebb öt kimeneti fájlra lesznek felosztva. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="import-customer-insights-data-from-sftp-location-to-salesforce-marketing-cloud"></a>Customer Insights adatok importálása a Salesforce Marketing Cloud-ba SFTP helyről

1. Hozzon létre [adatbővítményeket a Salesforce Marketing Cloud szolgáltatásban](https://help.salesforce.com/articleView?id=sf.mc_es_create_data_extension.htm&type=5) hogy a Customer Insights adatfájlt az SFTP helyről importálja.

2. [Importálja az adatokat az SFTP helyéről](https://help.salesforce.com/articleView?id=sf.mc_es_import_data_extension_classic.htm&type=5) a Salesforce Marketing Cloud adatbővítménybe. 

3. Az automatizálás beállítása az adatok adatbővítményekbe való importálásához. További információk a [fájl dropautomatizálásról és az ütemezett automatizálásról](https://help.salesforce.com/articleView?id=sf.mc_as_triggered_automations.htm&type=5).

   Definiáljon egy [fájl drop automatizálást](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_triggered_automation.htm&type=5) vagy egy  [ütemezett automatizálást](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_scheduled_automation.htm&type=5). 

Egy példa [SFTP-vel történő automatizálásra](https://help.salesforce.com/articleView?id=sf.mc_as_ftp_and_triggered_automation_scenario.htm&type=5).

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
