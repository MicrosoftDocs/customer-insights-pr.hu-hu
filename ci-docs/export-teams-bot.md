---
title: Teams robot a Dynamics 365 Customer Insights (előzetes verzió) szolgáltatáshoz
description: Az egyesített ügyfélprofilok keresése a Microsoft Teams robot segítségével tekinthető meg.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: d140ae72578b48091a41005c4acafe03bac540da
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195845"
---
# <a name="teams-bot-for-dynamics-365-customer-insights-preview"></a>Teams robot a Dynamics 365 Customer Insights (előzetes verzió) szolgáltatáshoz

Csatlakozzon a Microsoft Teams szolgáltatáshoz, és a robot segítségével keressen meg egyesített ügyfélprofilokat a Teams csatornákon.

:::image type="content" source="media/teams-bot.png" alt-text="Ügyfélrekordot mutató Teams bot":::

## <a name="prerequisites"></a>Előfeltételek

- Legalább egy [adatforrás hozzáadva](data-sources.md).
- Az [egyesítési eljárás](data-unification.md) teljes.
- A mezők hozzáadódnak a [keresési &szűrési indexhez](search-filter-index.md).
- A Customer Insights és a Teams ugyanabban a szervezetben található.
- A környezet az elsődleges célközönség ügyfelekre van állítva. Az üzleti fiókok nem támogatottak.


> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRElj]

## <a name="configure-the-bot"></a>Konfigurálja a robotot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.
1. A Microsoft Teams mozaikon válassza a **Beállítás** lehetőséget.
1. Átirányítják az **Alkalmazások** területre a Teams megoldásban. Alternatívaként a Teamst megnyithatja és az **alkalmazások** kiválasztásához kattinthat a bal alsó sarokban, vagy közvetlenül [lekérheti az AppSource megoldásból](https://go.microsoft.com/fwlink/?linkid=2124104).
1. Keresse meg a **Customer Insights** elemet, és válassza ki az alkalmazást.
1. Válassza a **Hozzáadás** lehetőséget.
1. Jelentkezzen be a Customer Insights szolgáltatásba a Teamsben. Üdvözlő üzenet jelenik meg.

## <a name="things-you-can-do-with-the-bot"></a>Dolgok, amelyeket a robot segítségével megtehet

A robot keresési lehetőségeket biztosít az egyesített ügyfelek profiljaihoz.

- Írja be **a keresést**, majd egy nevet, e-mail-címet vagy bármely más mezőt az egyesített ügyfélprofilban, amely hozzá van adva a keresési &szűrési indexhez.

  Az így kapott ügyfélprofilból legfeljebb 15 mezőt tartalmazó kártyát kaphat. A többszörös egyezések olyan eredménylistát adnak vissza, ahol lehetőség van a profilok kiválasztására. Pontos egyezés megkereséséhez adja hozzá a keresőszó (search word) dupla idézőjelben.

- Ha a szervezet több Customer Insights-környezetet tart fenn ugyanabban a szervezetben, írja be **a switchinstance** parancsot, és válassza ki, hogy melyik környezethez szeretné csatlakoztatni a robotot.

- Adja meg a **súgót** a bot számára elérhető parancsok listájának megjelenítéséhez.  

[!INCLUDE [footer-include](includes/footer-banner.md)]