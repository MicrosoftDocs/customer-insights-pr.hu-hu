---
title: Az entitások és entitásútvonalak közti kapcsolatok.
description: Kapcsolatok létrehozása és kezelése a több adatforrásból származó entitások között.
ms.date: 06/01/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: MichelleDevaney
ms.author: midevane
manager: shellyha
ms.openlocfilehash: d5b9566ec88096fec31d8e164a51598159ec26d4
ms.sourcegitcommit: ece48f80a7b470fb33cd36e3096b4f1e9190433a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/03/2021
ms.locfileid: "6171167"
---
# <a name="relationships-between-entities"></a><span data-ttu-id="ec336-103">Entitások közötti kapcsolatok</span><span class="sxs-lookup"><span data-stu-id="ec336-103">Relationships between entities</span></span>

<span data-ttu-id="ec336-104">Kapcsolatok összekapcsolják az entitásokat, és meghatározza az adatok grafikonját, ha az entitások közös azonosítón és idegen kulcson osztoznak.</span><span class="sxs-lookup"><span data-stu-id="ec336-104">Relationships connect entities and define a graph of your data when entities share a common identifier, a foreign key.</span></span> <span data-ttu-id="ec336-105">Ez az idegen kulcs egyik entitásról a másikra hivatkozhat.</span><span class="sxs-lookup"><span data-stu-id="ec336-105">This foreign key can be referenced from one entity to another.</span></span> <span data-ttu-id="ec336-106">Az összekapcsolt entitások több adatforráson alapuló szegmensek és mérőszámok definiálását teszik lehetővé.</span><span class="sxs-lookup"><span data-stu-id="ec336-106">Connected entities enable the definition of segments and measures based on multiple data sources.</span></span>

<span data-ttu-id="ec336-107">A kapcsolatoknak három típusa van:</span><span class="sxs-lookup"><span data-stu-id="ec336-107">There are three types of relationships:</span></span> 
- <span data-ttu-id="ec336-108">Nem szerkeszthető rendszerkapcsolat, amelyet a rendszer az adategyesítési folyamat részeként hoz létre</span><span class="sxs-lookup"><span data-stu-id="ec336-108">Non-editable system relationships, created by the system as part of the data unification process</span></span>
- <span data-ttu-id="ec336-109">Nem szerkeszthető öröklött kapcsolatok, amelyek automatikusan jönnek létre az adatforrások betöltésekor</span><span class="sxs-lookup"><span data-stu-id="ec336-109">Non-editable inherited relationships, which are created automatically from ingesting data sources</span></span> 
- <span data-ttu-id="ec336-110">Szerkeszthető egyéni kapcsolatok, amelyet a felhasználók hoztak létre és konfiguráltak</span><span class="sxs-lookup"><span data-stu-id="ec336-110">Editable custom relationships, created and configured by users</span></span>

## <a name="non-editable-system-relationships"></a><span data-ttu-id="ec336-111">Nem szerkeszthető rendszerkapcsolatok</span><span class="sxs-lookup"><span data-stu-id="ec336-111">Non-editable system relationships</span></span>

<span data-ttu-id="ec336-112">Az adatok egyesítése során a rendszerkapcsolatok automatikusan jönnek létre az intelligens egyeztetés alapján.</span><span class="sxs-lookup"><span data-stu-id="ec336-112">During data unification, system relationships are created automatically based on intelligent matching.</span></span> <span data-ttu-id="ec336-113">Ezek a kapcsolatok segítenek az ügyfélprofil rekordjainak összekapcsolásában más kapcsolódó entitások rekordjaival.</span><span class="sxs-lookup"><span data-stu-id="ec336-113">These relationships help relate the customer profile records with corresponding records.</span></span> <span data-ttu-id="ec336-114">Az alábbi ábra három rendszeralapú kapcsolat létrehozását szemlélteti.</span><span class="sxs-lookup"><span data-stu-id="ec336-114">The following diagram illustrates the creation of three system-based relationships.</span></span> <span data-ttu-id="ec336-115">Az ügyfél entitása más entitásokkal van egyeztetve az egységes *Ügyfél* entitás előállításához.</span><span class="sxs-lookup"><span data-stu-id="ec336-115">The customer entity is matched with other entities to produce the unified *Customer* entity.</span></span>

:::image type="content" source="media/relationships-entities-merge.png" alt-text="Diagram az ügyfél entitás kapcsolati elérési útjaival három 1-n kapcsolattal.":::

- <span data-ttu-id="ec336-117">***CustomerToContact* kapcsolat** az *Ügyfél* entitás és a *Kapcsolattartó* entitás között jött létre.</span><span class="sxs-lookup"><span data-stu-id="ec336-117">***CustomerToContact* relationship** was created between the *Customer* entity and the *Contact* entity.</span></span> <span data-ttu-id="ec336-118">Az *Ügyfél* entitás a **Contact_contactId** kulcsmezőjét kapcsolja össze a *Kapcsolattartó* entitás **contactId** kulcsmezőjével.</span><span class="sxs-lookup"><span data-stu-id="ec336-118">The *Customer* entity gets the key field **Contact_contactID** to relate to the *Contact* entity key field **contactID**.</span></span>
- <span data-ttu-id="ec336-119">A ***CustomerToAccount* kapcsolat** az *Ügyfél* entitás és a *Partner* entitás között jött létre.</span><span class="sxs-lookup"><span data-stu-id="ec336-119">***CustomerToAccount* relationship** was created between the *Customer* entity and the *Account* entity.</span></span> <span data-ttu-id="ec336-120">Az *Ügyfél* entitás **Account_accountID** kulcsmezőjét kapcsolja össze a *Partner* entitás **accountID** kulcsmezőjével.</span><span class="sxs-lookup"><span data-stu-id="ec336-120">The *Customer* entity gets the key field **Account_accountID** to relate to the *Account* entity key field **accountID**.</span></span>
- <span data-ttu-id="ec336-121">A ***CustomerToWebAccount* kapcsolat** az *Ügyfél* entitás és a *WebAccount* entitás között jött létre.</span><span class="sxs-lookup"><span data-stu-id="ec336-121">***CustomerToWebAccount* relationship** was created between the *Customer* entity and the *WebAccount* entity.</span></span> <span data-ttu-id="ec336-122">Az *Ügyfél* entitás **WebAccount_webaccountID** kulcsmezőjét kapcsolja össze a *WebAccount* entitás **webaccountID** kulcsmezőjével.</span><span class="sxs-lookup"><span data-stu-id="ec336-122">The *Customer* entity gets the key field **WebAccount_webaccountID** to relate to the *WebAccount* entity key field **webaccountID**.</span></span>

## <a name="non-editable-inherited-relationships"></a><span data-ttu-id="ec336-123">Nem szerkeszthető örökölt kapcsolatok</span><span class="sxs-lookup"><span data-stu-id="ec336-123">Non-editable inherited relationships</span></span>

<span data-ttu-id="ec336-124">Az adatbetöltési folyamat során a rendszer ellenőrzi a meglévő kapcsolatokhoz tartozó adatforrásokat.</span><span class="sxs-lookup"><span data-stu-id="ec336-124">During the data ingestion process, the system checks data sources for existing relationships.</span></span> <span data-ttu-id="ec336-125">Ha nincs kapcsolat, a rendszer automatikusan létrehozza azokat.</span><span class="sxs-lookup"><span data-stu-id="ec336-125">If no relationship exists, the system automatically creates them.</span></span> <span data-ttu-id="ec336-126">Ezeket a kapcsolatokat a lefelé irányuló folyamatokban is használják.</span><span class="sxs-lookup"><span data-stu-id="ec336-126">These relationships are also used in downstream processes.</span></span>

## <a name="create-a-custom-relationship"></a><span data-ttu-id="ec336-127">Egyéni kapcsolat létrehozása</span><span class="sxs-lookup"><span data-stu-id="ec336-127">Create a custom relationship</span></span>

<span data-ttu-id="ec336-128">A kapcsolat egy olyan *forrásentitásból* áll, amely tartalmazza az idegen kulcsot és egy *célentitást*, amelyre a forrás entitás idegen kulcsa mutat.</span><span class="sxs-lookup"><span data-stu-id="ec336-128">Relationship consists of a *source entity* containing the foreign key and a *target entity* that the source entity's foreign key points to.</span></span> 

1. <span data-ttu-id="ec336-129">A célközönség információin belül nyissa meg a következőt **Adatok** > **Kapcsolatok**.</span><span class="sxs-lookup"><span data-stu-id="ec336-129">In audience insights, go to **Data** > **Relationships**.</span></span>

2. <span data-ttu-id="ec336-130">Válassza az **Új kapcsolat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ec336-130">Select **New relationship**.</span></span>

3. <span data-ttu-id="ec336-131">Az **Új kapcsolat** ablaktáblában adja meg a következő információkat:</span><span class="sxs-lookup"><span data-stu-id="ec336-131">In the **New relationship** pane, provide the following information:</span></span>

   :::image type="content" source="media/relationship-add.png" alt-text="Új kapcsolat oldalsóablaktábla üres beviteli mezőkkel.":::

   - <span data-ttu-id="ec336-133">**Kapcsolat neve**: A kapcsolat célját tükröző név.</span><span class="sxs-lookup"><span data-stu-id="ec336-133">**Relationship name**: Name that reflects the purpose of the relationship.</span></span> <span data-ttu-id="ec336-134">Példa: CustomerToSupportCase.</span><span class="sxs-lookup"><span data-stu-id="ec336-134">Example: CustomerToSupportCase.</span></span>
   - <span data-ttu-id="ec336-135">**Leírás**: A kapcsolat leírása.</span><span class="sxs-lookup"><span data-stu-id="ec336-135">**Description**: Description of the relationship.</span></span>
   - <span data-ttu-id="ec336-136">**Forrásentitás**: A kapcsolat forrásaként használt entitás.</span><span class="sxs-lookup"><span data-stu-id="ec336-136">**Source entity**: Entity that is used as a source in the relationship.</span></span> <span data-ttu-id="ec336-137">Példa: SupportCase.</span><span class="sxs-lookup"><span data-stu-id="ec336-137">Example: SupportCase.</span></span>
   - <span data-ttu-id="ec336-138">**Célentitás**: A kapcsolat céljaként használt entitás.</span><span class="sxs-lookup"><span data-stu-id="ec336-138">**Target entity**: Entity that is used as a target in the relationship.</span></span> <span data-ttu-id="ec336-139">Példa: Ügyfél.</span><span class="sxs-lookup"><span data-stu-id="ec336-139">Example: Customer.</span></span>
   - <span data-ttu-id="ec336-140">**Forrás-számossága**: Adja meg a forrásentitás számosságát.</span><span class="sxs-lookup"><span data-stu-id="ec336-140">**Source cardinality**: Specify the cardinality of the source entity.</span></span> <span data-ttu-id="ec336-141">A számosság egy halmaz lehetséges elemeinek számát írja le.</span><span class="sxs-lookup"><span data-stu-id="ec336-141">Cardinality describes the number of possible elements in a set.</span></span> <span data-ttu-id="ec336-142">Mindig a cél számossághoz kapcsolódik.</span><span class="sxs-lookup"><span data-stu-id="ec336-142">It always relates to the target cardinality.</span></span> <span data-ttu-id="ec336-143">Választhat az **Egy** és a **Sok** közül.</span><span class="sxs-lookup"><span data-stu-id="ec336-143">You can choose between **One** and **Many**.</span></span> <span data-ttu-id="ec336-144">Csak sok-az-egyhez és egy-az-egyhez kapcsolatok támogatottak.</span><span class="sxs-lookup"><span data-stu-id="ec336-144">Only many-to-one and one-to-one relationships are supported.</span></span>  
     - <span data-ttu-id="ec336-145">Sok az egyhez: Több forrásrekord is kapcsolódhat egy célrekordhoz.</span><span class="sxs-lookup"><span data-stu-id="ec336-145">Many-to-one: Multiple source records can relate to one target record.</span></span> <span data-ttu-id="ec336-146">Példa: Több támogatási eset egyetlen ügyféltől.</span><span class="sxs-lookup"><span data-stu-id="ec336-146">Example: Multiple support cases from a single customer.</span></span>
     - <span data-ttu-id="ec336-147">Egy az egyhez: Egyetlen forrásrekord egyetlen célrekordhoz kapcsolódik.</span><span class="sxs-lookup"><span data-stu-id="ec336-147">One-to-one: A single source record relates to a one target record.</span></span> <span data-ttu-id="ec336-148">Példa: Egyetlen ügyfél hűségazonosítója.</span><span class="sxs-lookup"><span data-stu-id="ec336-148">Example: One loyalty ID for a single customer.</span></span>

     > [!NOTE]
     > <span data-ttu-id="ec336-149">Sok-a-sok kapcsolatokat lehet létrehozni két sok-az-egyhez kapcsolattal és egy összekötő entitással, amely összeköti a forrás entitást és a cél entitást.</span><span class="sxs-lookup"><span data-stu-id="ec336-149">Many-to-many relationships can be created using two many-to-one relationships and a linking entity, which connects the source entity and the target entity.</span></span>

   - <span data-ttu-id="ec336-150">**Cél számossága**: Válassza ki a Célentitás rekordjainak számosságát.</span><span class="sxs-lookup"><span data-stu-id="ec336-150">**Target cardinality**: Select the cardinality of the target entity records.</span></span> 
   - <span data-ttu-id="ec336-151">**Forráskulcs mező**: A forrásentitás idegen kulcs mezője.</span><span class="sxs-lookup"><span data-stu-id="ec336-151">**Source key field**: The foreign key field in the source entity.</span></span> <span data-ttu-id="ec336-152">Példa: A SupportCase a CaseID-t idegen kulcsmezőként használhatja.</span><span class="sxs-lookup"><span data-stu-id="ec336-152">Example: SupportCase could use CaseID as a foreign key field.</span></span>
   - <span data-ttu-id="ec336-153">**Cél kulcsmezője**: A célentitás kulcsmezője.</span><span class="sxs-lookup"><span data-stu-id="ec336-153">**Target key field**: The key field of the target entity.</span></span> <span data-ttu-id="ec336-154">Példa: Az ügyfél használhatja a **CustomerID** kulcsmezőt.</span><span class="sxs-lookup"><span data-stu-id="ec336-154">Example Customer could use the **CustomerID** key field.</span></span>

4. <span data-ttu-id="ec336-155">Az egyéni folyamat létrehozásához válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ec336-155">Select **Save** to create the custom relationship.</span></span>

## <a name="view-relationships"></a><span data-ttu-id="ec336-156">Kapcsolatok megtekintése</span><span class="sxs-lookup"><span data-stu-id="ec336-156">View relationships</span></span>

<span data-ttu-id="ec336-157">A Kapcsolatok oldal felsorolja az összes létrehozott kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="ec336-157">The Relationships page lists all the relationships that have been created.</span></span> <span data-ttu-id="ec336-158">Minden sor egy kapcsolatot jelent, amely a forrásentitásra, a célentitásra és a számosságra vonatkozó részleteket is tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="ec336-158">Each row represents a relationship, which also includes details about the source entity, the target entity, and the cardinality.</span></span> 

:::image type="content" source="media/relationships-list.png" alt-text="A kapcsolatok és lehetőségek listája a Kapcsolatok oldal műveletsávjában.":::

<span data-ttu-id="ec336-160">Ez az oldal számos lehetőséget kínál a meglévő és új kapcsolatokhoz:</span><span class="sxs-lookup"><span data-stu-id="ec336-160">This page offers a set of options for existing and new relationships:</span></span> 
- <span data-ttu-id="ec336-161">**Új kapcsolat:** Válassza az [Egyéni kapcsolat létrehozása](#create-a-custom-relationship) elemet.</span><span class="sxs-lookup"><span data-stu-id="ec336-161">**New Relationship**: [Create a custom relationship](#create-a-custom-relationship).</span></span>
- <span data-ttu-id="ec336-162">**Vizualizáció**: [Fedezze fel a kapcsolatvizualizálót](#explore-the-relationship-visualizer), hogy láthassa a meglévő kapcsolatok és azok számosságának hálózati diagramját.</span><span class="sxs-lookup"><span data-stu-id="ec336-162">**Visualizer**: [Explore the relationship visualizer](#explore-the-relationship-visualizer) to see a network diagram of the existing relationships and their cardinality.</span></span>
- <span data-ttu-id="ec336-163">**Szűrési szempont**: Válassza ki a listában megjelenítendő kapcsolatok típusát.</span><span class="sxs-lookup"><span data-stu-id="ec336-163">**Filter by**: Choose the type of relationships to show in the list.</span></span>
- <span data-ttu-id="ec336-164">**Kapcsolatok keresése**: Szöveges keresés használata a kapcsolatok tulajdonságai közötti kereséshez.</span><span class="sxs-lookup"><span data-stu-id="ec336-164">**Search relationships**: Use a text-based search on properties of the relationships.</span></span>

### <a name="explore-the-relationship-visualizer"></a><span data-ttu-id="ec336-165">Fedezze fel a kapcsolatvizualizálót</span><span class="sxs-lookup"><span data-stu-id="ec336-165">Explore the relationship visualizer</span></span>

<span data-ttu-id="ec336-166">A kapcsolatvizualizálót megjelenít egy hálózati diagramot, hogy láthassa a meglévő kapcsolatok és azok számossága közötti kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="ec336-166">The relationship visualizer shows a network diagram of the existing relationships between connected entities and their cardinality.</span></span>

<span data-ttu-id="ec336-167">A nézet testreszabásához módosíthatja a dobozok helyzetét a húzásukkal a vásznon.</span><span class="sxs-lookup"><span data-stu-id="ec336-167">To customize the view, you can change the position of the boxes by dragging them on the canvas.</span></span>

:::image type="content" source="media/relationship-visualizer.png" alt-text="Képernyőkép a kapcsolati vizualizáló hálózati diagramról a kapcsolódó entitások közötti kapcsolatokkal.":::

<span data-ttu-id="ec336-169">Választható beállítások:</span><span class="sxs-lookup"><span data-stu-id="ec336-169">Available options:</span></span> 
- <span data-ttu-id="ec336-170">**Exportálás képként**:Az aktuális nézet mentése képfájlként.</span><span class="sxs-lookup"><span data-stu-id="ec336-170">**Export as image**: Save the current view as an image file.</span></span>
- <span data-ttu-id="ec336-171">**Módosítás vízszintes/függőleges elrendezésre**: Módosítja az entitások és kapcsolatok elrendezését.</span><span class="sxs-lookup"><span data-stu-id="ec336-171">**Change to horizontal/vertical layout**: Change the alignment of the entities and relationships.</span></span>
- <span data-ttu-id="ec336-172">**Szerkesztés** : Az egyéni kapcsolatok tulajdonságainak frissítése a szerkesztőablakban, és módosítások mentése.</span><span class="sxs-lookup"><span data-stu-id="ec336-172">**Edit**: Update properties of custom relationships in the edit pane and save changes.</span></span>

## <a name="manage-existing-relationships"></a><span data-ttu-id="ec336-173">Meglévő kapcsolatok kezelése</span><span class="sxs-lookup"><span data-stu-id="ec336-173">Manage existing relationships</span></span> 

<span data-ttu-id="ec336-174">A Kapcsolatok oldalon minden kapcsolatot egy sor képvisel.</span><span class="sxs-lookup"><span data-stu-id="ec336-174">On the Relationships page, each relationship is represented by a row.</span></span> 

<span data-ttu-id="ec336-175">Válasszon ki egy kapcsolatot, és válasszon az alábbi lehetőségek közül:</span><span class="sxs-lookup"><span data-stu-id="ec336-175">Select a relationship and choose one of the following options:</span></span> 
 
- <span data-ttu-id="ec336-176">**Szerkesztés** : Az egyéni kapcsolatok tulajdonságainak frissítése a szerkesztőablakban, és módosítások mentése.</span><span class="sxs-lookup"><span data-stu-id="ec336-176">**Edit**: Update properties of custom relationships in the edit pane and save changes.</span></span>
- <span data-ttu-id="ec336-177">**Törlés**: Egyéni kapcsolatok törlése.</span><span class="sxs-lookup"><span data-stu-id="ec336-177">**Delete**: Delete custom relationships.</span></span>
- <span data-ttu-id="ec336-178">**Megtekintés**: A rendszer által létrehozott és örökölt kapcsolatok megtekintése.</span><span class="sxs-lookup"><span data-stu-id="ec336-178">**View**: View system-created and inherited relationships.</span></span> 

## <a name="next-step"></a><span data-ttu-id="ec336-179">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="ec336-179">Next step</span></span>

<span data-ttu-id="ec336-180">A rendszerkapcsolatok és az egyéni kapcsolatok több adatforráson alapuló [szegmensek létrehozására](segments.md) szolgálnak, amelyek már nincsenek elszigetelve.</span><span class="sxs-lookup"><span data-stu-id="ec336-180">System and custom relationships are used to [create segments](segments.md) based on multiple data sources that are no longer siloed.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
