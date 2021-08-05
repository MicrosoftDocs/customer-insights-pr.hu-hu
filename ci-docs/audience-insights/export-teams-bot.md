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
ms.openlocfilehash: e563619f40be859f3f02638adbd60b80423182b3
ms.sourcegitcommit: dab2cbf818fafc9436e685376df94c5e44e4b144
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/13/2021
ms.locfileid: "6554383"
---
# <a name="teams-bot-for-dynamics-365-customer-insights-preview"></a>Teams robot a Dynamics 365 Customer Insights (előzetes verzió) szolgáltatáshoz

Csatlakozzon a Microsoft Teams szolgáltatáshoz, és a robot segítségével keressen meg egyesített ügyfélprofilokat a Teams csatornákon.

> [!div class="mx-imgBorder"]
> ![Ügyfélrekordot mutató Teams bot.](media/teams-bot.png "Ügyfélrekordot mutató Teams bot")

## <a name="prerequisites"></a>Előfeltételek

A robot beállításához és konfigurálásához a következő előfeltételeknek kell teljesülnie:

- Van legalább egy [adatforrás hozzáadva](data-sources.md).
- Az [egyesítési eljárás](data-unification.md) teljes.
- A mezők hozzáadódnak a [keresési és a szűrő indexhez](search-filter-index.md).
- A Customer Insights és a Teams ugyanabban a szervezetben található.

## <a name="configure-the-bot"></a>Konfigurálja a robotot

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.
1. A Microsoft Teams mozaikon válassza a **Beállítás** lehetőséget.
1. Átirányítják az **Alkalmazások** területre a Teams megoldásban. Alternatívaként a Teamst megnyithatja és az **alkalmazások** kiválasztásához kattinthat a bal alsó sarokban, vagy közvetlenül [lekérheti az AppSource megoldásból](https://go.microsoft.com/fwlink/?linkid=2124104).
1. Keresse meg a **Customer Insights** elemet, és válassza ki az alkalmazást.
1. Válassza a **Hozzáadás** lehetőséget.
1. Ha bejelentkezik a Customer Insights megoldásba a Teams megoldásban, megjelenik egy üdvözlő üzenet, és elkezdhető a munka.

## <a name="things-you-can-do-with-the-bot"></a>Dolgok, amelyeket a robot segítségével megtehet

A robot keresési lehetőségeket biztosít az egyesített ügyfelek profiljaihoz.

- Adja meg a **keresést** és a szűrő indexbe felvett egyesített ügyfélkapcsolat-profil neve, e-mail címe vagy bármely más mezője után.

  Az így kapott ügyfélprofilból legfeljebb 15 mezőt tartalmazó kártyát kaphat. A többszörös egyezések olyan eredménylistát adnak vissza, ahol lehetőség van a profilok kiválasztására. A keresőszót idézőjelek között a pontos egyezés megkereséséhez adhatja hozzá.

- Ha a szervezet több Customer Insights-környezetet tart fenn ugyanabban a szervezetben, megadhatja a **switchinstance** kifejezést a környezet kiválasztásához, amelyhez a robotot szeretné kapcsolni.

- Adja meg a **súgót** a bot számára elérhető parancsok listájának megjelenítéséhez.  


[!INCLUDE[footer-include](../includes/footer-banner.md)]