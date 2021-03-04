---
title: Robot a Microsoft Teamshez
description: Az egyesített ügyfélprofilok keresése a Microsoft Teams robot segítségével tekinthető meg.
ms.date: 04/21/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 03299610fd41a7e142e3c9723fad56ce7f90e083
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267955"
---
# <a name="teams-bot-for-dynamics-365-customer-insights-preview"></a><span data-ttu-id="c831b-103">Teams robot a Dynamics 365 Customer Insights (előzetes verzió) szolgáltatáshoz</span><span class="sxs-lookup"><span data-stu-id="c831b-103">Teams bot for Dynamics 365 Customer Insights (preview)</span></span>

<span data-ttu-id="c831b-104">Csatlakozzon a Microsoft Teams szolgáltatáshoz, és a robot segítségével keressen meg egyesített ügyfélprofilokat a Teams csatornákon.</span><span class="sxs-lookup"><span data-stu-id="c831b-104">Connect with Microsoft Teams to let a bot look up unified customer profiles in Teams channels.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="c831b-105">![Ügyfélrekordot mutató Teams bot](media/teams-bot.png "Ügyfélrekordot mutató Teams bot")</span><span class="sxs-lookup"><span data-stu-id="c831b-105">![Teams bot showing a customer record](media/teams-bot.png "Teams bot showing a customer record")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c831b-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="c831b-106">Prerequisites</span></span>

<span data-ttu-id="c831b-107">A robot beállításához és konfigurálásához a következő előfeltételeknek kell teljesülnie:</span><span class="sxs-lookup"><span data-stu-id="c831b-107">To set up and configure the bot, the following prerequisites must be met:</span></span>

- <span data-ttu-id="c831b-108">Van legalább egy [adatforrás hozzáadva](data-sources.md).</span><span class="sxs-lookup"><span data-stu-id="c831b-108">There's at least one [data source added](data-sources.md).</span></span>
- <span data-ttu-id="c831b-109">Az [egyesítési eljárás](data-unification.md) teljes.</span><span class="sxs-lookup"><span data-stu-id="c831b-109">The [unification process](data-unification.md) is complete.</span></span>
- <span data-ttu-id="c831b-110">A mezők hozzáadódnak a [keresési és a szűrő indexhez](search-filter-index.md).</span><span class="sxs-lookup"><span data-stu-id="c831b-110">Fields are added to the [search and filter index](search-filter-index.md).</span></span>
- <span data-ttu-id="c831b-111">A Customer Insights és a Teams ugyanabban a szervezetben található.</span><span class="sxs-lookup"><span data-stu-id="c831b-111">Customer Insights and Teams are in the same organization.</span></span>

## <a name="configure-the-bot"></a><span data-ttu-id="c831b-112">Konfigurálja a robotot</span><span class="sxs-lookup"><span data-stu-id="c831b-112">Configure the bot</span></span>

1. <span data-ttu-id="c831b-113">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="c831b-113">In audience insights, go to **Admin** > **Export Destinations**.</span></span>
1. <span data-ttu-id="c831b-114">A Microsoft Teams mozaikon válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c831b-114">On the Microsoft Teams tile, select **Set up**.</span></span>
1. <span data-ttu-id="c831b-115">Átirányítják az **Alkalmazások** területre a Teams megoldásban.</span><span class="sxs-lookup"><span data-stu-id="c831b-115">You're redirected to the **Apps** area in Teams.</span></span> <span data-ttu-id="c831b-116">Alternatívaként a Teamst megnyithatja és az **alkalmazások** kiválasztásához kattinthat a bal alsó sarokban, vagy közvetlenül [lekérheti az AppSource megoldásból](https://go.microsoft.com/fwlink/?linkid=2124104).</span><span class="sxs-lookup"><span data-stu-id="c831b-116">You can also open Teams and select **Apps** in the bottom-left corner or [get it from AppSource](https://go.microsoft.com/fwlink/?linkid=2124104) directly.</span></span>
1. <span data-ttu-id="c831b-117">Keresse meg a **Customer Insights** elemet, és válassza ki az alkalmazást.</span><span class="sxs-lookup"><span data-stu-id="c831b-117">Search for **Customer Insights** and select the app.</span></span>
1. <span data-ttu-id="c831b-118">Válassza a **Hozzáadás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c831b-118">Select **Add**.</span></span>
1. <span data-ttu-id="c831b-119">Ha bejelentkezik a Customer Insights megoldásba a Teams megoldásban, megjelenik egy üdvözlő üzenet, és elkezdhető a munka.</span><span class="sxs-lookup"><span data-stu-id="c831b-119">After signing in to Customer Insights in Teams, you'll see a welcome message and can get started.</span></span>

## <a name="things-you-can-do-with-the-bot"></a><span data-ttu-id="c831b-120">Dolgok, amelyeket a robot segítségével megtehet</span><span class="sxs-lookup"><span data-stu-id="c831b-120">Things you can do with the bot</span></span>

<span data-ttu-id="c831b-121">A robot keresési lehetőségeket biztosít az egyesített ügyfelek profiljaihoz.</span><span class="sxs-lookup"><span data-stu-id="c831b-121">The bot provides lookup capabilities for unified customer profiles.</span></span>

- <span data-ttu-id="c831b-122">Adja meg a **keresést** és a szűrő indexbe felvett egyesített ügyfélkapcsolat-profil neve, e-mail címe vagy bármely más mezője után.</span><span class="sxs-lookup"><span data-stu-id="c831b-122">Enter **search** followed by a name, email address, or any other field on the unified customer profile that is added to the search and filter index.</span></span>

  <span data-ttu-id="c831b-123">Az így kapott ügyfélprofilból legfeljebb 15 mezőt tartalmazó kártyát kaphat.</span><span class="sxs-lookup"><span data-stu-id="c831b-123">You'll get a card with up to 15 fields from the resulting customer profile.</span></span> <span data-ttu-id="c831b-124">A többszörös egyezések olyan eredménylistát adnak vissza, ahol lehetőség van a profilok kiválasztására.</span><span class="sxs-lookup"><span data-stu-id="c831b-124">Multiple matches return a list of results where you can select a profile.</span></span> <span data-ttu-id="c831b-125">A keresőszót idézőjelek között a pontos egyezés megkereséséhez adhatja hozzá.</span><span class="sxs-lookup"><span data-stu-id="c831b-125">You can add the search term in double quotes to look up an exact match.</span></span>

- <span data-ttu-id="c831b-126">Ha a szervezet több Customer Insights-környezetet tart fenn ugyanabban a szervezetben, megadhatja a **switchinstance** kifejezést a környezet kiválasztásához, amelyhez a robotot szeretné kapcsolni.</span><span class="sxs-lookup"><span data-stu-id="c831b-126">If your organization maintains multiple Customer Insights environments in the same organization, you can enter **switchinstance** to choose which environment you want to connect the bot to.</span></span>

- <span data-ttu-id="c831b-127">Adja meg a **súgót** a bot számára elérhető parancsok listájának megjelenítéséhez.</span><span class="sxs-lookup"><span data-stu-id="c831b-127">Enter **help** to see a list of available commands for the bot.</span></span>  


[!INCLUDE[footer-include](../includes/footer-banner.md)]