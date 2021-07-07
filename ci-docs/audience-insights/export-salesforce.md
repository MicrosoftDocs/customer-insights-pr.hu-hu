---
title: Customer Insights-adatok exportálása a Salesforce Marketing Cloud-ba
description: További információ a kapcsolat konfigurálásához és a Salesforce Marketing Cloud-ba való exportáláshoz.
ms.date: 06/24/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 123f8b2dbb6140785dec6c1b4164d2f513f66a53
ms.sourcegitcommit: 057079532e31c12bac36f374857ba3dc847d6ad0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2021
ms.locfileid: "6314624"
---
# <a name="export-segments-and-other-data-to-salesforce-marketing-cloud-preview"></a><span data-ttu-id="a2264-103">Szegmensek és egyéb adatok exportálása a Salesforce Marketing Cloud-ba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="a2264-103">Export segments and other data to Salesforce Marketing Cloud (preview)</span></span>

<span data-ttu-id="a2264-104">Használja az ügyféladatokat a Salesforce Marketing Cloud szolgáltatásban egy Biztonságos Fájlátviteli Protokoll (SFTP) helyen keresztül történő exportálással.</span><span class="sxs-lookup"><span data-stu-id="a2264-104">Use your customer data in Salesforce Marketing Cloud by exporting them through a Secure File Transfer Protocol (SFTP) location.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="a2264-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="a2264-105">Prerequisites for connection</span></span>

- <span data-ttu-id="a2264-106">Egy SFTP állomás és a hozzájuk tartozó rendszergazdai hitelesítő adatok elérhetősége.</span><span class="sxs-lookup"><span data-stu-id="a2264-106">Availability of an SFTP host and corresponding admin credentials.</span></span> [<span data-ttu-id="a2264-107">Az SFTP-helyek beállítása a Salesforce Marketing Cloud szolgáltatáshoz</span><span class="sxs-lookup"><span data-stu-id="a2264-107">How to setup SFTP locations for Salesforce Marketing Cloud</span></span>](https://help.salesforce.com/articleView?id=sf.mc_es_configure_enhanced_ftp.htm&type=5) 

## <a name="known-limitations"></a><span data-ttu-id="a2264-108">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="a2264-108">Known limitations</span></span>

- <span data-ttu-id="a2264-109">Az exportálás futtatása a rendszer teljesítményétől függ.</span><span class="sxs-lookup"><span data-stu-id="a2264-109">The runtime of an export depends on your system performance.</span></span> <span data-ttu-id="a2264-110">A kiszolgáló minimális konfigurációjának ajánlott két processzormag és 1 Gb memória.</span><span class="sxs-lookup"><span data-stu-id="a2264-110">We recommend two CPU cores and 1 Gb of memory as minimal configuration of your server.</span></span> 
- <span data-ttu-id="a2264-111">Az ajánlott minimális konfiguráció használata esetén az entitások legfeljebb 100 millió ügyfélprofillal való exportálása 90 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="a2264-111">Exporting entities with up to 100 million customer profiles can take 90 minutes when using the recommended minimal configuration.</span></span> 

## <a name="set-up-the-connection-to-salesforce-marketing-cloud"></a><span data-ttu-id="a2264-112">A Salesforce Marketing Cloud kapcsolatának beállítása</span><span class="sxs-lookup"><span data-stu-id="a2264-112">Set up the connection to Salesforce Marketing Cloud</span></span>

1. <span data-ttu-id="a2264-113">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a2264-113">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="a2264-114">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Salesforce Marketing Cloud** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="a2264-114">Select **Add connection** and choose **Salesforce Marketing Cloud** to configure the connection.</span></span>

1. <span data-ttu-id="a2264-115">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="a2264-115">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="a2264-116">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="a2264-116">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="a2264-117">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="a2264-117">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="a2264-118">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="a2264-118">Choose who can use this connection.</span></span> <span data-ttu-id="a2264-119">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="a2264-119">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="a2264-120">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="a2264-120">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="a2264-121">Adjon meg egy **Felhasználónevet**, **Jelszót**, **Állomásnevet** és **Exportálási mappát** az SFTP-fiókhoz.</span><span class="sxs-lookup"><span data-stu-id="a2264-121">Provide a **Username**, **Password**, **Hostname**, and **Export folder** for your SFTP account.</span></span>

1. <span data-ttu-id="a2264-122">A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a2264-122">Select **Verify** to test the connection.</span></span>

1. <span data-ttu-id="a2264-123">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="a2264-123">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="a2264-124">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a2264-124">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="a2264-125">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="a2264-125">Configure an export</span></span>

<span data-ttu-id="a2264-126">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="a2264-126">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="a2264-127">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="a2264-127">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="a2264-128">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a2264-128">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="a2264-129">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a2264-129">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="a2264-130">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az SFTP szakaszból.</span><span class="sxs-lookup"><span data-stu-id="a2264-130">In the **Connection for export** field, choose a connection from the SFTP section.</span></span> <span data-ttu-id="a2264-131">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="a2264-131">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="a2264-132">Válassza ki, hogy szeretné-e exportálni a **Tömörített** vagy **Tömörítetlen** adatokat, és a **mező elválasztó karaktert** az exportált fájlokhoz.</span><span class="sxs-lookup"><span data-stu-id="a2264-132">Choose if you want to export your data **Gzipped** or **Unzipped** and the **field delimiter** for the exported files.</span></span>

1. <span data-ttu-id="a2264-133">Jelölje ki az exportálni kívánt entitásokat, például szegmenseket.</span><span class="sxs-lookup"><span data-stu-id="a2264-133">Select the entities, for example segments, you want to export.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a2264-134">Az egyes kijelölt entitások exportáláskor legfeljebb öt kimeneti fájlra lesznek felosztva.</span><span class="sxs-lookup"><span data-stu-id="a2264-134">Each selected entity will be split up into up to five output files when exported.</span></span> 

1. <span data-ttu-id="a2264-135">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="a2264-135">Select **Save**.</span></span>

<span data-ttu-id="a2264-136">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="a2264-136">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="a2264-137">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="a2264-137">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="a2264-138">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="a2264-138">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="import-customer-insights-data-from-sftp-location-to-salesforce-marketing-cloud"></a><span data-ttu-id="a2264-139">Customer Insights adatok importálása a Salesforce Marketing Cloud-ba SFTP helyről</span><span class="sxs-lookup"><span data-stu-id="a2264-139">Import Customer Insights data from SFTP location to Salesforce Marketing Cloud</span></span>

1. <span data-ttu-id="a2264-140">Hozzon létre [adatbővítményeket a Salesforce Marketing Cloud szolgáltatásban](https://help.salesforce.com/articleView?id=sf.mc_es_create_data_extension.htm&type=5) hogy a Customer Insights adatfájlt az SFTP helyről importálja.</span><span class="sxs-lookup"><span data-stu-id="a2264-140">Create [data extensions in Salesforce Marketing Cloud](https://help.salesforce.com/articleView?id=sf.mc_es_create_data_extension.htm&type=5) to import the Customer Insights data file from the SFTP location.</span></span>

2. <span data-ttu-id="a2264-141">[Importálja az adatokat az SFTP helyéről](https://help.salesforce.com/articleView?id=sf.mc_es_import_data_extension_classic.htm&type=5) a Salesforce Marketing Cloud adatbővítménybe.</span><span class="sxs-lookup"><span data-stu-id="a2264-141">[Import the data from the SFTP location](https://help.salesforce.com/articleView?id=sf.mc_es_import_data_extension_classic.htm&type=5) into the Salesforce Marketing Cloud data extension.</span></span> 

3. <span data-ttu-id="a2264-142">Az automatizálás beállítása az adatok adatbővítményekbe való importálásához.</span><span class="sxs-lookup"><span data-stu-id="a2264-142">Set up the automation to import the data into the data extensions.</span></span> <span data-ttu-id="a2264-143">További információk a [fájl dropautomatizálásról és az ütemezett automatizálásról](https://help.salesforce.com/articleView?id=sf.mc_as_triggered_automations.htm&type=5).</span><span class="sxs-lookup"><span data-stu-id="a2264-143">Learn more about [file drop automations and scheduled automations](https://help.salesforce.com/articleView?id=sf.mc_as_triggered_automations.htm&type=5).</span></span>

   <span data-ttu-id="a2264-144">Definiáljon egy [fájl drop automatizálást](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_triggered_automation.htm&type=5) vagy egy  [ütemezett automatizálást](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_scheduled_automation.htm&type=5).</span><span class="sxs-lookup"><span data-stu-id="a2264-144">Define a [file drop automation](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_triggered_automation.htm&type=5) or a  [scheduled automation](https://help.salesforce.com/articleView?id=sf.mc_as_define_a_scheduled_automation.htm&type=5).</span></span> 

<span data-ttu-id="a2264-145">Egy példa [SFTP-vel történő automatizálásra](https://help.salesforce.com/articleView?id=sf.mc_as_ftp_and_triggered_automation_scenario.htm&type=5).</span><span class="sxs-lookup"><span data-stu-id="a2264-145">Here's an example of [an automation with SFTP](https://help.salesforce.com/articleView?id=sf.mc_as_ftp_and_triggered_automation_scenario.htm&type=5).</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="a2264-146">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="a2264-146">Data privacy and compliance</span></span>

<span data-ttu-id="a2264-147">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="a2264-147">When you enable Dynamics 365 Customer Insights to transmit data via SFTP, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="a2264-148">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="a2264-148">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that the export destination meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="a2264-149">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="a2264-149">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="a2264-150">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="a2264-150">Your Dynamics 365 Customer Insights administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
