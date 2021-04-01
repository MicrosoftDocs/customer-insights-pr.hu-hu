---
title: Az entitások és entitásútvonalak közti kapcsolatok.
description: Kapcsolatok létrehozása és kezelése a több adatforrásból származó entitások között.
ms.date: 04/14/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: c25bfcb8e2a8223498dd1a5e8cfb3712a40ab85e
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5595215"
---
# <a name="relationships-between-entities"></a><span data-ttu-id="044fe-103">Entitások közötti kapcsolatok</span><span class="sxs-lookup"><span data-stu-id="044fe-103">Relationships between entities</span></span>

<span data-ttu-id="044fe-104">A kapcsolatok segítséget nyújtanak az entitások összekapcsolásában, illetve az adatok gráfjának generálásában, amikor az entitások egy közös azonosítóval (idegen kulccsal) rendelkeznek, amellyel hivatkozni lehet az egyik entitásról a másikra.</span><span class="sxs-lookup"><span data-stu-id="044fe-104">Relationships help you connect entities and generate a graph of your data when entities share a common identifier (foreign key) that can be referenced from one entity to another.</span></span> <span data-ttu-id="044fe-105">Az összekapcsolt entitások több adatforráson alapuló szegmensek és mérőszámok definiálását teszik lehetővé.</span><span class="sxs-lookup"><span data-stu-id="044fe-105">Connected entities enable you to define segments and measures based on multiple data sources.</span></span>

<span data-ttu-id="044fe-106">A kapcsolatoknak két típusa van:</span><span class="sxs-lookup"><span data-stu-id="044fe-106">There are two types of relationships.</span></span> <span data-ttu-id="044fe-107">Nem szerkeszthető rendszerkapcsolatok, amelyek automatikusan jönnek létre, és egyéni kapcsolatok, amelyeket felhasználók hoznak létre és konfigurálnak.</span><span class="sxs-lookup"><span data-stu-id="044fe-107">Non-editable system relationships, which are created automatically, and custom relationships created and configured by users.</span></span>

<span data-ttu-id="044fe-108">Az egyeztetési és egyesítési folyamatok során a rendszerkapcsolatok a háttérben jönnek létre az intelligens egyeztetés alapján.</span><span class="sxs-lookup"><span data-stu-id="044fe-108">During the match and merge processes, system relationships are created behind the scenes based on intelligent matching.</span></span> <span data-ttu-id="044fe-109">Ezek a kapcsolatok segítenek az Ügyfélprofil rekordjainak összekapcsolásában más kapcsolódó entitások rekordjaival.</span><span class="sxs-lookup"><span data-stu-id="044fe-109">These relationships help relate the Customer Profile records with other corresponding entities' records.</span></span> <span data-ttu-id="044fe-110">A következő ábra három rendszerkapcsolat létrehozását mutatja be, amikor az ügyfél entitást további entitásokkal társítják, hogy előállítsák a végső ügyfélprofil entitást.</span><span class="sxs-lookup"><span data-stu-id="044fe-110">The following diagram illustrates the creation of three system relationships when the customer entity is matched with additional entities to produce the final Customer Profile entity.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="044fe-111">![Kapcsolat létrehozása](media/relationships-entities-merge.png "Kapcsolat létrehozása")</span><span class="sxs-lookup"><span data-stu-id="044fe-111">![Relationship creation](media/relationships-entities-merge.png "Relationship creation")</span></span>

- <span data-ttu-id="044fe-112">***CustomerToContact* kapcsolat** jaz Ügyfél entitás és a Kapcsolattartó entitás között jött létre.</span><span class="sxs-lookup"><span data-stu-id="044fe-112">***CustomerToContact* relationship** was created between the Customer entity and the Contact entity.</span></span> <span data-ttu-id="044fe-113">Az Ügyfél entitás **Contact_contactId** kulcsmezőjét kapcsolja össze a Kapcsolattartó entitás **contactId** kulcsmezőjével.</span><span class="sxs-lookup"><span data-stu-id="044fe-113">The Customer entity gets the key field **Contact_contactId** to relate to the Contact entity key field **contactId**.</span></span>
- <span data-ttu-id="044fe-114">***CustomerToAccount* kapcsolat** az Ügyfél entitás és a Partner entitás között jött létre.</span><span class="sxs-lookup"><span data-stu-id="044fe-114">***CustomerToAccount* relationship** was created between the Customer entity and the Account entity.</span></span> <span data-ttu-id="044fe-115">Az Ügyfél entitás **Account_accountId** kulcsmezőjét kapcsolja össze a Partner entitás **accountId** kulcsmezőjével.</span><span class="sxs-lookup"><span data-stu-id="044fe-115">The Customer entity gets the key field **Account_accountId** to relate to the Account entity key field **accountId**.</span></span>
- <span data-ttu-id="044fe-116">***CustomerToWebAccount* kapcsolat** az Ügyfél entitás és a WebAccount entitás között jött létre.</span><span class="sxs-lookup"><span data-stu-id="044fe-116">***CustomerToWebAccount* relationship** was created between the Customer entity and the WebAccount entity.</span></span> <span data-ttu-id="044fe-117">Az Ügyfél entitás **WebAccount_webaccountId** kulcsmezőjét kapcsolja össze a WebAccount entitás **webaccountId** kulcsmezőjével.</span><span class="sxs-lookup"><span data-stu-id="044fe-117">The Customer entity gets the key field **WebAccount_webaccountId** to relate to the WebAccount entity key field **webaccountId**.</span></span>

## <a name="create-a-relationship"></a><span data-ttu-id="044fe-118">Egy kapcsolat létrehozása</span><span class="sxs-lookup"><span data-stu-id="044fe-118">Create a relationship</span></span>

<span data-ttu-id="044fe-119">Egyéni kapcsolatok definiálása a **kapcsolatok** oldalon történhet.</span><span class="sxs-lookup"><span data-stu-id="044fe-119">Define custom relationships on the **Relationships** page.</span></span> <span data-ttu-id="044fe-120">Minden kapcsolat egy forrásoldali entitásból (az idegen kulcsot tartalmazó entitásból) és a céloldali entitásból (az a entitás, amelyre a forrásentitás idegen kulcsa mutat) áll.</span><span class="sxs-lookup"><span data-stu-id="044fe-120">Each relationship consists of a Source entity (the entity that holds the foreign key) and a Target entity (the entity that the source entity's foreign key points to).</span></span>

1. <span data-ttu-id="044fe-121">A célközönség információin belül nyissa meg a következőt **Adatok** > **Kapcsolatok**.</span><span class="sxs-lookup"><span data-stu-id="044fe-121">In audience insights, go to **Data** > **Relationships**.</span></span>

2. <span data-ttu-id="044fe-122">Válassza az **Új kapcsolat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="044fe-122">Select **New relationship**.</span></span>

3. <span data-ttu-id="044fe-123">A **Kapcsolat hozzáadása** ablaktáblában adja meg a következő információkat:</span><span class="sxs-lookup"><span data-stu-id="044fe-123">In the **Add relationship** pane, provide the following information:</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="044fe-124">![Kapcsolati adatok megadása](media/relationships-add.png "Kapcsolati adatok megadása")</span><span class="sxs-lookup"><span data-stu-id="044fe-124">![Enter relationship details](media/relationships-add.png "Enter relationship details")</span></span>

   - <span data-ttu-id="044fe-125">**Kapcsolat neve**: A kapcsolat célját tükröző név (például **AccountWebLogs**).</span><span class="sxs-lookup"><span data-stu-id="044fe-125">**Relationship name**: Name that reflects the purpose of the relationship (for example, **AccountWebLogs**).</span></span>
   - <span data-ttu-id="044fe-126">**Leírás**: A kapcsolat leírása.</span><span class="sxs-lookup"><span data-stu-id="044fe-126">**Description**: Description of the relationship.</span></span>
   - <span data-ttu-id="044fe-127">**Forrásoldali entitás**: válassza ki azt az entitást, amelyet a kapcsolat forrásaként használ (például WebLog).</span><span class="sxs-lookup"><span data-stu-id="044fe-127">**Source entity**: Select the entity that is used as a source in the relationship (for example, WebLog).</span></span>
   - <span data-ttu-id="044fe-128">**Számosság**: Válassza ki a Forrásentitás rekordjainak számosságát.</span><span class="sxs-lookup"><span data-stu-id="044fe-128">**Cardinality**: Select the cardinality of the source entity records.</span></span> <span data-ttu-id="044fe-129">Például a „sok” azt jelenti, hogy több Webnapló-rekord egy WebAccount partnerhez kapcsolódik.</span><span class="sxs-lookup"><span data-stu-id="044fe-129">For example, "many" means that multiple Weblog records are related to one WebAccount.</span></span>
   - <span data-ttu-id="044fe-130">**Forrás kulcsmezője**: Ez a forrásentitás idegenkulcs-mezőjének felel meg.</span><span class="sxs-lookup"><span data-stu-id="044fe-130">**Source key field**: This represents the foreign key field in the source entity.</span></span> <span data-ttu-id="044fe-131">A WebLog például a **accountId** idegen kulcsmezőt tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="044fe-131">For example, WebLog has the **accountId** foreign key field.</span></span>
   - <span data-ttu-id="044fe-132">**Céloldali entitás**: válassza ki azt az entitást, amelyet a kapcsolat céljaként használ (például WebAccount).</span><span class="sxs-lookup"><span data-stu-id="044fe-132">**Target entity**: Select the entity that is used as a target in the relationship (for example, WebAccount).</span></span>
   - <span data-ttu-id="044fe-133">**Cél számossága**: Válassza ki a Célentitás rekordjainak számosságát.</span><span class="sxs-lookup"><span data-stu-id="044fe-133">**Target cardinality**: Select the cardinality of the target entity records.</span></span> <span data-ttu-id="044fe-134">Például az „egy” azt jelenti, hogy több Webnapló-rekord egy WebAccount partnerhez kapcsolódik.</span><span class="sxs-lookup"><span data-stu-id="044fe-134">For example, "one" means that multiple Weblog records are related to one WebAccount.</span></span>
   - <span data-ttu-id="044fe-135">**Cél kulcsmezője**: Ez a mező a célentitás kulcsmezőjének felel meg.</span><span class="sxs-lookup"><span data-stu-id="044fe-135">**Target key field**: This field represents the key field of target entity.</span></span> <span data-ttu-id="044fe-136">A WebAccount például a **accountId** kulcsmezőt tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="044fe-136">For example, WebAccount has the **accountId** key field.</span></span>

> [!NOTE]
> <span data-ttu-id="044fe-137">Csak sok-az-egyhez és egy-az-egyhez kapcsolatok támogatottak.</span><span class="sxs-lookup"><span data-stu-id="044fe-137">Only many-to-one and one-to-one relationships are supported.</span></span> <span data-ttu-id="044fe-138">A sok-a-sokhoz kapcsolatok létrehozhatók két, sok-az-egyhez kapcsolat és egy kapcsolóentitás segítségével (egy entitás, amely a forrásoldali entitás és a céloldali entitás összekapcsolására szolgál).</span><span class="sxs-lookup"><span data-stu-id="044fe-138">Many-to-many relationships can be created using two many-to-one relationships and a link entity (an entity that is used to connect the source entity and the target entity).</span></span>

## <a name="delete-a-relationship"></a><span data-ttu-id="044fe-139">Kapcsolat törlése</span><span class="sxs-lookup"><span data-stu-id="044fe-139">Delete a relationship</span></span>

1. <span data-ttu-id="044fe-140">A célközönség információin belül nyissa meg a következőt **Adatok** > **Kapcsolatok**.</span><span class="sxs-lookup"><span data-stu-id="044fe-140">In audience insights, go to **Data** > **Relationships**.</span></span>

2. <span data-ttu-id="044fe-141">Jelölje be a törölni kívánt kapcsolatok jelölőnégyzetét.</span><span class="sxs-lookup"><span data-stu-id="044fe-141">Select check boxes for the relationships you want to delete.</span></span>

3. <span data-ttu-id="044fe-142">Válassza a **Törlés** lehetőséget a **kapcsolatok** tábla tetején.</span><span class="sxs-lookup"><span data-stu-id="044fe-142">Select **Delete** at the top of the **Relationships** table.</span></span>

4. <span data-ttu-id="044fe-143">Hagyja jóvá a törlést.</span><span class="sxs-lookup"><span data-stu-id="044fe-143">Confirm your deletion.</span></span>

## <a name="next-step"></a><span data-ttu-id="044fe-144">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="044fe-144">Next step</span></span>

<span data-ttu-id="044fe-145">A rendszerkapcsolatok és az egyéni kapcsolatok több adatforráson alapuló szegmensek létrehozására szolgálnak, amelyek már nincsenek elszigetelve.</span><span class="sxs-lookup"><span data-stu-id="044fe-145">System and custom relationships are used to create segments based on multiple data sources that are no longer siloed.</span></span> <span data-ttu-id="044fe-146">További tudnivalókat a [Szegmensek](segments.md) részben talál.</span><span class="sxs-lookup"><span data-stu-id="044fe-146">For more information, see [Segments](segments.md).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]