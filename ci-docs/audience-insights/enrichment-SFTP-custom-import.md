---
title: Bővítés SFTP egyéni importálással
description: Általános információk az SFTP egyéni importálási bővítésről.
ms.date: 11/18/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: jdahl
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 59f7f05ca0825ba147e9e93f10fa3508ec3a16dd
ms.sourcegitcommit: ff824bbbd31fd666ab0da682bf48ea31580d242c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/18/2020
ms.locfileid: "4568453"
---
# <a name="enrich-customer-profiles-with-custom-data-preview"></a><span data-ttu-id="a923f-103">Felhasználói profilok bővítése egyéni adatokkal (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="a923f-103">Enrich customer profiles with custom data (preview)</span></span>

<span data-ttu-id="a923f-104">A Secure File Transfer Protocol (SFTP) egyéni importálás lehetővé teszi, hogy olyan bővítési adatokat importáljon, amik még nem mentek keresztül az adategységesítési folyamaton.</span><span class="sxs-lookup"><span data-stu-id="a923f-104">Secure File Transfer Protocol(SFTP) custom import enables you to import data that doesn't have to go through the process of data unification.</span></span> <span data-ttu-id="a923f-105">Az adatok bevitelének rugalmas, biztonságos és egyszerű módja.</span><span class="sxs-lookup"><span data-stu-id="a923f-105">It's a flexible, secure, and easy way to bring in your data.</span></span> <span data-ttu-id="a923f-106">Az SFTP egyéni Importálás az [SFTP exportálással](export-sftp.md) együtt használható, amely lehetővé teszi a bővítéshez szükséges ügyfélprofiladatok exportálását.</span><span class="sxs-lookup"><span data-stu-id="a923f-106">SFTP custom import can be used in combination with [SFTP export](export-sftp.md) that lets you export the customer profile data that is needed for enrichment.</span></span> <span data-ttu-id="a923f-107">Az adatok ezután feldolgozhatók és bővíthetők, és az SFTP egyéni importálás segítségével a bővített adat visszavihető a Dynamics 365 Customer Insights célközönség-információk funkciójába.</span><span class="sxs-lookup"><span data-stu-id="a923f-107">The data can then be processed, enriched, and SFTP custom import can be used to bring the enriched data back to the audience insights capability of Dynamics 365 Customer Insights.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a923f-108">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="a923f-108">Prerequisites</span></span>

<span data-ttu-id="a923f-109">Az SFTP egyéni importálás konfigurálásához a következő előfeltételeknek kell teljesülnie:</span><span class="sxs-lookup"><span data-stu-id="a923f-109">To configure SFTP custom import, the following prerequisites must be met:</span></span>

- <span data-ttu-id="a923f-110">Felhasználói hitelesítő adatokkal (felhasználónévvel és jelszóval) rendelkezik ahhoz az SFTP-helyhez, ahol az importálandó adatok származnak.</span><span class="sxs-lookup"><span data-stu-id="a923f-110">You have user credentials (user name and password) for the SFTP location where the data that is going to be imported from.</span></span>
- <span data-ttu-id="a923f-111">Rendelkezik az STFP gazdaszámítógép URL-címével és portszámával (általában 22).</span><span class="sxs-lookup"><span data-stu-id="a923f-111">You have the URL and port number (usually 22) for the STFP host.</span></span>
- <span data-ttu-id="a923f-112">Rendelkezik a fájl fájlnevével és helyével, amelyet az SFTP gazdaszámítógépen kell importálni.</span><span class="sxs-lookup"><span data-stu-id="a923f-112">You have the filename and location of the file to be imported on the SFTP host.</span></span>
- <span data-ttu-id="a923f-113">Van egy olyan *model.json* fájl, amely megadja az importálandó adatok sémáját.</span><span class="sxs-lookup"><span data-stu-id="a923f-113">There's a *model.json* file that specifies the schema for the data that are to be imported.</span></span> <span data-ttu-id="a923f-114">A fájlnak ugyanabban a könyvtárban kell lennie, mint az importálandó fájlnak.</span><span class="sxs-lookup"><span data-stu-id="a923f-114">This file must be in the same directory as the file to import.</span></span>
- <span data-ttu-id="a923f-115">[Rendszergazda](permissions.md#administrator) engedéllyel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="a923f-115">You have [Administrator](permissions.md#administrator) permission.</span></span>

## <a name="configuration"></a><span data-ttu-id="a923f-116">Konfigurálás</span><span class="sxs-lookup"><span data-stu-id="a923f-116">Configuration</span></span>

1. <span data-ttu-id="a923f-117">Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.</span><span class="sxs-lookup"><span data-stu-id="a923f-117">Go to **Data** > **Enrichment** and select the **Discover** tab.</span></span>

1. <span data-ttu-id="a923f-118">Az **SFTP egyéni importálási csempén** jelölje be a **Saját adatok bővítése** jelölőnégyzetet.</span><span class="sxs-lookup"><span data-stu-id="a923f-118">On the **SFTP custom import tile**, select **Enrich my data**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="a923f-119">![SFTP egyéni importálás csempe](media/SFTP_Custom_Import_tile.png "SFTP egyéni importálás csempe")</span><span class="sxs-lookup"><span data-stu-id="a923f-119">![SFTP Custom Import tile](media/SFTP_Custom_Import_tile.png "SFTP Custom Import tile")</span></span>

1. <span data-ttu-id="a923f-120">Válassza az **Első lépések** lehetőséget, és adja meg a hitelesítő adatokat és az SFTP kiszolgáló címét.</span><span class="sxs-lookup"><span data-stu-id="a923f-120">Select **Get started** and provide the credentials and the address for the SFTP server.</span></span> <span data-ttu-id="a923f-121">Például sftp://mysftpserver.com:22.</span><span class="sxs-lookup"><span data-stu-id="a923f-121">For example, sftp://mysftpserver.com:22.</span></span>

1. <span data-ttu-id="a923f-122">Adja meg annak a fájlnak a nevét, amely az adatot tartalmazza, és a fájl elérési útját az SFTP kiszolgálón, ha nem szerepel a gyökérkönyvtárban.</span><span class="sxs-lookup"><span data-stu-id="a923f-122">Enter the name of the file that contains the data and path to the file on the SFTP server if it's not in the root folder.</span></span>

1. <span data-ttu-id="a923f-123">A **Csatlakozás egyéni importáláshoz** jelölőnégyzet bejelölésével erősítse meg az összes bemenetet.</span><span class="sxs-lookup"><span data-stu-id="a923f-123">Confirm all inputs by selecting **Connect to Custom Import**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="a923f-124">![SFTP egyéni importálási konfiguráció úszó panel](media/SFTP_Custom_Import_Configuration_flyout.png "SFTP egyéni importálási konfiguráció úszó panel")</span><span class="sxs-lookup"><span data-stu-id="a923f-124">![SFTP Custom Import Configuration flyout](media/SFTP_Custom_Import_Configuration_flyout.png "SFTP Custom Import Configuration flyout")</span></span>

## <a name="defining-field-mappings"></a><span data-ttu-id="a923f-125">Mezőleképezések meghatározása</span><span class="sxs-lookup"><span data-stu-id="a923f-125">Defining field mappings</span></span> 

<span data-ttu-id="a923f-126">Az SFTP-kiszolgálón importálandó fájlt tartalmazó könyvtárnak tartalmaznia kell egy *model.json* fájlt is.</span><span class="sxs-lookup"><span data-stu-id="a923f-126">The directory that contains the file to be imported on the SFTP server must also contain a *model.json* file.</span></span> <span data-ttu-id="a923f-127">Ez a fájl határozza meg az adatok importálásához használandó sémát.</span><span class="sxs-lookup"><span data-stu-id="a923f-127">This file defines the schema to use for importing the data.</span></span> <span data-ttu-id="a923f-128">A sémának a [Common Data Model](https://docs.microsoft.com/common-data-model/) használatával kell megadnia a mező leképezését.</span><span class="sxs-lookup"><span data-stu-id="a923f-128">The schema has to use [the Common Data Model](https://docs.microsoft.com/common-data-model/) to specify the field mapping.</span></span> <span data-ttu-id="a923f-129">A model.json fájl egyszerű példája a következőképpen néz ki:</span><span class="sxs-lookup"><span data-stu-id="a923f-129">A simple example of a model.json file looks like this:</span></span>

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

## <a name="enrichment-results"></a><span data-ttu-id="a923f-130">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="a923f-130">Enrichment results</span></span>

<span data-ttu-id="a923f-131">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="a923f-131">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="a923f-132">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="a923f-132">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="a923f-133">A feldolgozási idő az importálandó adatok méretétől és az SFTP kiszolgálóval létesített kapcsolattól függ.</span><span class="sxs-lookup"><span data-stu-id="a923f-133">The processing time will depend on the size of the data to be imported and the connection to the SFTP server.</span></span>

<span data-ttu-id="a923f-134">A bővítési folyamat befejeződése után áttekintheti az újonnan importált egyéni bővítési adatokat a **Saját bővítések** részben.</span><span class="sxs-lookup"><span data-stu-id="a923f-134">After the enrichment process completes, you can review your newly imported custom enrichment data under **My enrichments**.</span></span> <span data-ttu-id="a923f-135">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="a923f-135">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="a923f-136">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="a923f-136">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a923f-137">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="a923f-137">Next steps</span></span>

<span data-ttu-id="a923f-138">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="a923f-138">Build on top of your enriched customer data.</span></span> <span data-ttu-id="a923f-139">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) és [exportálja az adatot](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="a923f-139">Create [segments](segments.md), [measures](measures.md), and [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>


