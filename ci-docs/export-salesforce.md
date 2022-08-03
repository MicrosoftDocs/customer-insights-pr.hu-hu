---
title: Adatok exportálása a Salesforce Marketing Cloudba (előzetes verzió)
description: További információ a kapcsolat konfigurálásához és a Salesforce Marketing Cloud-ba való exportáláshoz.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 58e76e51c18c25177f9b4551b70b25b41248b142
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9197041"
---
# <a name="export-data-to-salesforce-marketing-cloud-preview"></a>Adatok exportálása a Salesforce Marketing Cloudba (előzetes verzió)

Használja az ügyféladatokat a Salesforce Marketing Cloud szolgáltatásban egy Biztonságos Fájlátviteli Protokoll (SFTP) helyen keresztül történő exportálással.

## <a name="prerequisites"></a>Előfeltételek

- Egy [SFTP-gazdagép a Salesforce Marketing Cloudhoz](https://help.salesforce.com/articleView?id=sf.mc_es_configure_enhanced_ftp.htm&type=5) és a megfelelő rendszergazdai hitelesítő adatokhoz.

## <a name="set-up-connection-to-salesforce-marketing-cloud"></a>Kapcsolat beállítása a Salesforce Marketing Clouddal

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Salesforce Marketing Cloud **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adjon meg egy **Felhasználónevet**, **Jelszót**, **Állomásnevet** és **Exportálási mappát** az SFTP-fiókhoz.

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

## <a name="import-customer-insights-data-from-sftp-location-to-salesforce-marketing-cloud"></a>Customer Insights adatok importálása a Salesforce Marketing Cloud-ba SFTP helyről

1. Hozzon létre [adatbővítményeket a Salesforce Marketing Cloud szolgáltatásban](https://help.salesforce.com/articleView?id=sf.mc_es_create_data_extension.htm&type=5) hogy a Customer Insights adatfájlt az SFTP helyről importálja.

2. [Importálja az adatokat az SFTP helyéről](https://help.salesforce.com/articleView?id=sf.mc_es_import_data_extension_classic.htm&type=5) a Salesforce Marketing Cloud adatbővítménybe.

3. Az automatizálás beállítása az adatok adatbővítményekbe való importálásához. További információk a [fájl dropautomatizálásról és az ütemezett automatizálásról](https://help.salesforce.com/articleView?id=sf.mc_as_triggered_automations.htm&type=5).

   Definiáljon egy [fájl drop automatizálást](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_triggered_automation.htm&type=5) vagy egy  [ütemezett automatizálást](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_scheduled_automation.htm&type=5).

Egy példa [SFTP-vel történő automatizálásra](https://help.salesforce.com/articleView?id=sf.mc_as_ftp_and_triggered_automation_scenario.htm&type=5).

[!INCLUDE [footer-include](includes/footer-banner.md)]
