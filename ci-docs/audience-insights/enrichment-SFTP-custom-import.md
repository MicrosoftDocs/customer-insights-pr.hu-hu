---
title: Bővítés SFTP egyéni importálással
description: Általános információk az SFTP egyéni importálási bővítésről.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: f92b36ac5364ea8586f9cbba7ba03178641555c0
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6304653"
---
# <a name="enrich-customer-profiles-with-custom-data-preview"></a><span data-ttu-id="3deb3-103">Felhasználói profilok bővítése egyéni adatokkal (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="3deb3-103">Enrich customer profiles with custom data (preview)</span></span>

<span data-ttu-id="3deb3-104">A Secure File Transfer Protocol (SFTP) egyéni importálás lehetővé teszi, hogy olyan bővítési adatokat importáljon, amik még nem mentek keresztül az adategységesítési folyamaton.</span><span class="sxs-lookup"><span data-stu-id="3deb3-104">Secure File Transfer Protocol (SFTP) custom import enables you to import data that doesn't have to go through the process of data unification.</span></span> <span data-ttu-id="3deb3-105">Az adatok bevitelének rugalmas, biztonságos és egyszerű módja.</span><span class="sxs-lookup"><span data-stu-id="3deb3-105">It's a flexible, secure, and easy way to bring in your data.</span></span> <span data-ttu-id="3deb3-106">Az SFTP egyéni Importálás az [SFTP exportálással](export-sftp.md) együtt használható, amely lehetővé teszi a bővítéshez szükséges ügyfélprofiladatok exportálását.</span><span class="sxs-lookup"><span data-stu-id="3deb3-106">SFTP custom import can be used in combination with [SFTP export](export-sftp.md) that lets you export the customer profile data that is needed for enrichment.</span></span> <span data-ttu-id="3deb3-107">Ezután az adatok feldolgozhatók és bővíthetők, és az SFTP egyéni importálása felhasználható a bővített adatok visszahozására a Dynamics 365 Customer Insights célközönségi elemzések lehetőségeihez.</span><span class="sxs-lookup"><span data-stu-id="3deb3-107">The data can then be processed and enriched, and SFTP custom import can be used to bring the enriched data back to the audience insights capability of Dynamics 365 Customer Insights.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3deb3-108">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="3deb3-108">Prerequisites</span></span>

<span data-ttu-id="3deb3-109">Az SFTP egyéni importálás konfigurálásához a következő előfeltételeknek kell teljesülnie:</span><span class="sxs-lookup"><span data-stu-id="3deb3-109">To configure SFTP custom import, the following prerequisites must be met:</span></span>

- <span data-ttu-id="3deb3-110">Az SFTP állomáson importálni kívánt fájl neve és helye (elérési útvonal) megvan.</span><span class="sxs-lookup"><span data-stu-id="3deb3-110">You have the file name and location (path) of the file to be imported on the SFTP host.</span></span>
- <span data-ttu-id="3deb3-111">Van egy *model.json* fájl, amely megadja az importálni kívánt adatok [Common Data Model sémáját](/common-data-model/).</span><span class="sxs-lookup"><span data-stu-id="3deb3-111">There is a *model.json* file that specifies [the Common Data Model schema](/common-data-model/) for the data to be imported.</span></span> <span data-ttu-id="3deb3-112">A fájlnak ugyanabban a könyvtárban kell lennie, mint az importálandó fájlnak.</span><span class="sxs-lookup"><span data-stu-id="3deb3-112">This file must be in the same directory as the file to import.</span></span>
- <span data-ttu-id="3deb3-113">Egy SFTP-kapcsolatot már konfigurált egy rendszergazda, *vagy* Ön rendelkezik a [rendszergazdai](permissions.md#administrator) engedélyekkel.</span><span class="sxs-lookup"><span data-stu-id="3deb3-113">An SFTP connection has already been configured by an administrator *or* you have [administrator](permissions.md#administrator) permissions.</span></span> <span data-ttu-id="3deb3-114">Ahhoz az SFTP-helyhez, ahonnan az adatokat importálni szeretné, szüksége lesz a felhasználói hitelesítő adatokra, az URL-címre és a portszámra.</span><span class="sxs-lookup"><span data-stu-id="3deb3-114">You'll need the user credentials, URL, and port number for the SFTP location where you want to import data from.</span></span>


## <a name="configure-the-import"></a><span data-ttu-id="3deb3-115">Importálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="3deb3-115">Configure the import</span></span>

1. <span data-ttu-id="3deb3-116">Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.</span><span class="sxs-lookup"><span data-stu-id="3deb3-116">Go to **Data** > **Enrichment** and select the **Discover** tab.</span></span>

1. <span data-ttu-id="3deb3-117">Az **SFTP egyéni importálási csempe** lehetőségen válassza az **Adatok bővítése**, majd az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3deb3-117">On the **SFTP custom import tile**, select **Enrich my data** and then select **Get started**.</span></span>

   :::image type="content" source="media/SFTP_Custom_Import_tile.png" alt-text="SFTP egyéni importálás csempe.":::

1. <span data-ttu-id="3deb3-119">Válasszon egy [kapcsolatot](connections.md) a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="3deb3-119">Select a [connection](connections.md) from the dropdown list.</span></span> <span data-ttu-id="3deb3-120">Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.</span><span class="sxs-lookup"><span data-stu-id="3deb3-120">Contact an administrator if no connection is available.</span></span> <span data-ttu-id="3deb3-121">Ha Ön rendszergazda, akkor kapcsolatot hozhat létre a **Kapcsolat hozzáadása** majd **SFTP Egyéni Importálás** kiválasztásával a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="3deb3-121">If you are an administrator, you can create a connection by selecting **Add connection** and choosing **SFTP Custom Import** from the dropdown list.</span></span>

1. <span data-ttu-id="3deb3-122">A kijelölt kapcsolat megerősítéséhez válassza a **Csatlakozás egyéni importáláshoz** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3deb3-122">Select **Connect to Custom Import** to confirm the selected connection.</span></span>

1.  <span data-ttu-id="3deb3-123">Válassza a **Tovább** lehetőséget, és írja be az importálni kívánt adatfájl **Elérési útvonal** és **Fájlnév** részleteit.</span><span class="sxs-lookup"><span data-stu-id="3deb3-123">Select **Next** and enter the **Path** and **Filename** of the data file that you want to import.</span></span>

    :::image type="content" source="media/enrichment-SFTP-path-and-filename.png" alt-text="Képernyőkép készítése az adathely megadásakor.":::

1. <span data-ttu-id="3deb3-125">Válassza a **Következő** lehetőséget, és adja meg a bővítés nevét és a kimeneti entitás nevét.</span><span class="sxs-lookup"><span data-stu-id="3deb3-125">Select **Next** and provide a name for the enrichment and a name for the output entity.</span></span> 

1. <span data-ttu-id="3deb3-126">Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.</span><span class="sxs-lookup"><span data-stu-id="3deb3-126">Select **Save enrichment** after reviewing your choices.</span></span>

## <a name="configure-the-connection-for-sftp-custom-import"></a><span data-ttu-id="3deb3-127">Az SFTP egyéni importálás kapcsolatának beállítása</span><span class="sxs-lookup"><span data-stu-id="3deb3-127">Configure the connection for SFTP Custom Import</span></span> 

<span data-ttu-id="3deb3-128">A kapcsolatok konfiguráljához rendszergazdának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="3deb3-128">You need to be an administrator to configure connections.</span></span> <span data-ttu-id="3deb3-129">A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget az Egyéni importálás csempén.</span><span class="sxs-lookup"><span data-stu-id="3deb3-129">Select **Add connection** when configuring an enrichment *or* go to **Admin** > **Connections** and select **Set up** on the Custom Import tile.</span></span>

1. <span data-ttu-id="3deb3-130">Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="3deb3-130">Enter a name for the connection in the **Display name** box.</span></span>

1. <span data-ttu-id="3deb3-131">Adja meg annak az SFTP-kiszolgálónak az érvényes felhasználónevét, jelszavát és állomás URL-címét, ahol az importálni kívánt adatok találhatók.</span><span class="sxs-lookup"><span data-stu-id="3deb3-131">Enter a valid username, password, and host URL for the SFTP server that the data to be imported resides on.</span></span>

1. <span data-ttu-id="3deb3-132">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="3deb3-132">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span>

1. <span data-ttu-id="3deb3-133">A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3deb3-133">Select **Verify** to validate the configuration.</span></span>

1. <span data-ttu-id="3deb3-134">Az ellenőrzés befejezését követően a kapcsolat menthető a **Mentés** lehetőség kiválasztásával.</span><span class="sxs-lookup"><span data-stu-id="3deb3-134">Once the verification has completed, the connection can be saved by selecting **Save**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="3deb3-135">![Experian kapcsolati konfiguráció oldal](media/enrichment-SFTP-connection.png "Experian kapcsolati konfiguráció oldal")</span><span class="sxs-lookup"><span data-stu-id="3deb3-135">![Experian connection configuration page](media/enrichment-SFTP-connection.png "Experian connection configuration page")</span></span>


## <a name="defining-field-mappings"></a><span data-ttu-id="3deb3-136">Mezőleképezések meghatározása</span><span class="sxs-lookup"><span data-stu-id="3deb3-136">Defining field mappings</span></span> 

<span data-ttu-id="3deb3-137">Az SFTP-kiszolgálón importálandó fájlt tartalmazó könyvtárnak tartalmaznia kell egy *model.json* fájlt is.</span><span class="sxs-lookup"><span data-stu-id="3deb3-137">The directory that contains the file to be imported on the SFTP server must also contain a *model.json* file.</span></span> <span data-ttu-id="3deb3-138">Ez a fájl határozza meg az adatok importálásához használandó sémát.</span><span class="sxs-lookup"><span data-stu-id="3deb3-138">This file defines the schema to use for importing the data.</span></span> <span data-ttu-id="3deb3-139">A sémának használnia kell a [Közös Adatmodellt](/common-data-model/) a mező leképezésének megadásához.</span><span class="sxs-lookup"><span data-stu-id="3deb3-139">The schema has to use [Common Data Model](/common-data-model/) to specify the field mapping.</span></span> <span data-ttu-id="3deb3-140">A model.json fájl egyszerű példája a következőképpen néz ki:</span><span class="sxs-lookup"><span data-stu-id="3deb3-140">A simple example of a model.json file looks like this:</span></span>

```
{
    "name": "EnrichmentFromMicrosoft",
    "description": "Model containing data enrichment",
    "entities": [
        {
            "name": "CustomImport",
            "attributes": [
                {
                    "name": "CustomerId",
                    "friendlyName": "Client id",
                    "dataType": "string"
                },
                {
                    "name": "PreferredCity",
                    "friendlyName": "Preferred City for vacation",
                    "dataType": "string"
                },
                {
                    "name": "PreferredTransportation",
                    "friendlyName": "Preferred transportation",
                    "dataType": "string"
                }
            ],
            "annotations": [
                {
                    "name": "c360:PrimaryKey",
                    "value": "CustomerId"
                }
            ]
        }
    ],
    "modifiedTime": "2020-01-02T12:00:00+08:00",
    "annotations": [
        {
            "name": "testAnnotation",
            "value": "testValue"
        }
    ]
}
```

## <a name="enrichment-results"></a><span data-ttu-id="3deb3-141">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="3deb3-141">Enrichment results</span></span>

<span data-ttu-id="3deb3-142">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="3deb3-142">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="3deb3-143">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="3deb3-143">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="3deb3-144">A feldolgozási idő az importálandó adatok méretétől és az SFTP kiszolgálóval létesített kapcsolattól függ.</span><span class="sxs-lookup"><span data-stu-id="3deb3-144">The processing time will depend on the size of the data to be imported and the connection to the SFTP server.</span></span>

<span data-ttu-id="3deb3-145">A bővítési folyamat befejeződése után áttekintheti az újonnan importált egyéni bővítési adatokat a **Saját bővítések** részben.</span><span class="sxs-lookup"><span data-stu-id="3deb3-145">After the enrichment process completes, you can review your newly imported custom enrichment data under **My enrichments**.</span></span> <span data-ttu-id="3deb3-146">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="3deb3-146">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="3deb3-147">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="3deb3-147">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3deb3-148">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="3deb3-148">Next steps</span></span>

<span data-ttu-id="3deb3-149">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="3deb3-149">Build on top of your enriched customer data.</span></span> <span data-ttu-id="3deb3-150">Hozzon létre [szegmenseket](segments.md) és [intézkedéseket](measures.md), továbbá [exportálja az adatokat](export-destinations.md) , hogy személyre szabott élményt nyújtson ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="3deb3-150">Create [segments](segments.md) and [measures](measures.md), and [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
