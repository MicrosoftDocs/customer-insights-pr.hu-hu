---
title: Az API-k használata
description: Az API-k használata és a korlátozások megismerése.
ms.date: 05/10/2021
ms.reviewer: wimohabb
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: 4d41d7d328dfa6699b5f5e992d3a5bf3179490d8
ms.sourcegitcommit: 33a8e21b3bf6521bdb8346f81f79fce88091ddfd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/10/2021
ms.locfileid: "6016595"
---
# <a name="work-with-customer-insights-apis"></a>Customer Insights API-k használata

Dynamics 365 Customer Insights az API-kat biztosít, amivel saját alkalmazásokat hozhat létre a Customer Insights adatok alapján.

> [!IMPORTANT]
> Az API-k részletes ismertetése a [Customer Insights API-k segédeletében](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) található. További információkat tartalmaznak a műveletekről, a paraméterekről és a válaszokról.

A cikk végigvezeti a Customer Insights API-k elérésén, Azure-alkalmazás regisztrálásának létrehozásához, valamint a rendelkezésre álló ügyféloldali tárak használatba vételéhez segítséget nyújt.

## <a name="get-started-trying-the-customer-insights-apis"></a>Ismerkedés a Customer Insights API-k kipróbálásával

1. [Jelentkezzen be](https://home.ci.ai.dynamics.com) a Customer Insights szolgáltatásba. Ha még nincs előfizetése, [iratkozzon fel a Customer Insights próbaverziójára](https://aka.ms/tryci).

1. Az API-k engedélyezéséhez a Customer Insights környezetében látogasson el a **Rendszergazda** > **Engedélyek** pontra. Ehhez rendszergazdai engedélyekre van szükség.

1. Nyissa meg az **API-k** lapot, és jelölje be az **Engedélyezés** gombot.    
   Az API-k engedélyezésekor a rendszer elsődleges és másodlagos előfizetési kulcsot hoz létre az API-kérésekben használt példányhoz. A kulcsok újbóli generálásához válassza az **Elsődleges újbóli létrehozása** vagy a **Másodlagos újbóli létrehozása** beállítást a **Rendszergazda** > **Engedélyek** > **API-k** között.

   :::image type="content" source="media/enable-apis.gif" alt-text="Customer Insights API-k engedélyezése":::

1. Az **API-k kipróbálásához** válassza az [API-k kipróbálása](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances) lehetőséget.

1. Válasszon egy API-műveletet, és válassza a **Kipróbálásá** lehetőséget.

1. Az oldalsó ablaktáblában állítsa az **Engedélyezés** legördülő menüt **Implicit** értékre. Az `Authorization` fejléchez hozzáadásra kerül egy tulajdonosi jogkivonat. Az előfizetési kulcsot a rendszer automatikusan kitölti.
  
1. Tetszés szerint hozzáadhatja az összes szükséges lekérdezési paramétert.

1. Görgessen az oldalsó panel aljára, és válassza a **Küldés** lehetőséget.

A HTTP-válasz hamarosan az alábbiakban jelenik meg.


   :::image type="content" source="media/try-apis.gif" alt-text="Az API-k kiválasztott tesztelését bemutató animált gif.":::

## <a name="create-a-new-app-registration-in-the-azure-portal"></a>Hozzon létre egy új alkalmazásregisztrációt az Azure Portalon

Ezekkel a lépésekkel megteheti az első lépéseket a Customer Insights API használatában egy Azure-alkalmazásban a delegált engedélyekkel. Győződjön meg róla, hogy először elvégezte az [Első lépések](#get-started-trying-the-customer-insights-apis) részt.

1. Jelentkezzen be az [Azure portálba](https://portal.azure.com) weboldalára azzal a fiókkal, amely hozzáfér a Customer Insights adatokhoz.

1. A bal oldalon válassza az **Alkalmazásregisztrációk** lehetőséget.

1. Válassza az **Új regisztráció** lehetőséget, és adja meg az alkalmazás nevét és a fiók típusát.
   Ha szeretne, megadhat egy átirányítási URL-címet. http://localhost elegendő az alkalmazások helyi számítógépen történő fejlesztéséhez.

1. Az új alkalmazás regisztrálásával nyissa meg az **API-engedélyeket**.

   :::image type="content" source="media/app-registration-1.gif" alt-text="API-engedélyek beállítása az alkalmazás regisztrálásához - animált gif.":::

1. Válassza az **Engedély hozzáadása** lehetőséget, és az oldalsó panelben válassza a **Customer Insights** lehetőséget.

1. A **Engedély típusához** válassza a **Delegált engedélyek** lehetőséget, és jelölje ki a **user_impersonation** engedélyt.

1. Jelölje be az **Engedélyek hozzáadása** lehetőséget. Ha felhasználói bejelentkezés nélkül kell elérnie az API-t, tekintse át a [Kiszolgálók közötti alkalmazásengedélyek](#server-to-server-application-permissions) szakaszt.

1. Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.

Használhatja az alkalmazás/ügyfélazonosítót az alkalmazásregisztrációhoz a Microsoft hitelesítési függvénytárral (MSAL), hogy megszerezze a tulajdonosi jogkivonatot, amelyet elküldhet a kéréssel az API-nak.

:::image type="content" source="media/grant-admin-consent.gif" alt-text="Animált gif a rendszergazdai hozzájárulás biztosítására.":::

Az MSAL-lel kapcsolatos további információkért tekintse át a [Microsoft hitelesítési függvénytár (MSAL) áttekintése](/azure/active-directory/develop/msal-overview).

Az alkalmazással kapcsolatos további információkért tekintse meg [Az Azure Portal alkalmazás új regisztrációs élményét](/azure/active-directory/develop/app-registration-portal-training-guide).

Az API-k ügyféltárakban való használatára vonatkozó információkért tekintse meg a [Customer Insights ügyféloldali tárakat](#customer-insights-client-libraries).

### <a name="server-to-server-application-permissions"></a>Kiszolgálók közötti alkalmazásengedélyek

Az [alkalmazásregisztráció című szakasz](#create-a-new-app-registration-in-the-azure-portal) ismerteti, hogyan lehet olyan alkalmazást regisztrálni, amelyhez a felhasználónak be kell jelentkeznie a hitelesítéshez. Megismerheti, hogyan hozhat létre olyan alkalmazásregisztrációt, amelyhez nincs szükség felhasználói beavatkozásra, és futtatható kiszolgálón is.

1. Az Azure portál alkalmazásregisztrációja után nyissa meg az **API-engedélyeket**.

1. Válassza az **Engedély hozzáadása** lehetőséget. 

1. Lépjen a **Szervezetem által használt API-k** lapra, és válassza ki a lista **Dynamics 365 AI for Customer Insights** elemét. 

1. A **Engedély típusához** válassza az **Alkalmazásengedélyek** lehetőséget, és jelölje ki a **CustomerInsights.Api.All** engedélyt.

1. Jelölje be az **Engedélyek hozzáadása** lehetőséget.

1. Az alkalmazás regisztrálásához lépjen vissza az **API-engedélyekhez**.

1. Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.

   :::image type="content" source="media/grant-admin-consent.gif" alt-text="Animált gif a rendszergazdai hozzájárulás biztosítására.":::

1. Következtetésképp hozzá kell adnunk az alkalmazásregisztráció nevét felhasználóként a Customer Insightsban.    
   Nyissa meg a Customer Insights szolgáltatást **Rendszergazda** > **Engedélyek** pontra, és válassza a **Felhasználó hozzáadása**.

1. Keresse meg az alkalmazásregisztrációjának nevét, jelölje ki a keresési eredmények között, és válassza a **Mentés** lehetőséget.

## <a name="customer-insights-client-libraries"></a>Customer Insights ügyféloldali tárak

Ez a szakasz segítséget nyújt a Customer Insights API-k számára elérhető ügyféloldali függvénytárak használatba vételéhez. Minden függvénytár-forráskód és mintaalkalmazás megtalálható a [Customer Insights GitHub oldalon](https://github.com/microsoft/Dynamics365-CustomerInsights-Client-Libraries). 

### <a name="c-nuget"></a>C# NuGet

Ismerje meg a C# ügyféloldali függvénytárak használatának első lépéseit a NuGet.org webhelyről. A NuGet csomaggal kapcsolatos további információkért lásd: [Microsoft.Dynamics.CustomerInsights.Api](https://www.nuget.org/packages/Microsoft.Dynamics.CustomerInsights.Api/). A csomag jelenleg a netstandard2.0 és a netcoreapp2.0 keretrendszert célozza meg.

#### <a name="add-the-c-client-library-to-a-c-project"></a>C# ügyféloldali függvénytár hozzáadása C#-projekthez

1. A Visual Studio szolgáltatásban nyissa meg a **NuGet csomagkezelő** elemet a projekthez.

1. Keresse meg a **Microsoft.Dynamics.CustomerInsights.Api**.

1. Válassza a **Telepítés** lehetőséget a csomag projekthez való hozzáadásához.
   Másik lehetőségként futtassa ezt a parancsot a **NuGet csomagkezelő konzolon**: `Install-Package -Id Microsoft.Dynamics.CustomerInsights.Api -Source nuget.org -ProjectName <project name> [-Version <version>]`

   :::image type="content" source="media/visual-studio-nuget-package.gif" alt-text="NuGet-csomag hozzáadása Visual Studio-projekthez":::

#### <a name="use-the-c-client-library"></a>A C# ügyféloldali függvénytár használata

1. Használja a [Microsoft hitelesítési függvénytárat (MSAL)](/azure/active-directory/develop/msal-overview), és használja a `AccessToken` meglévő [Azure alkalmazásregisztrációt](#create-a-new-app-registration-in-the-azure-portal).

1. A token sikeres hitelesítése és megszerzése után hozzon létre egy új `HttpClient` elemet, vagy használjon egy meglévőt a kiegészítő **DefaultRequestHeaders "Authorization"** beállítást **Tulajdonos <access token>** értékre állítva, és az **Ocp-Apim-Subscription-Key** beállítást [**előfizetési kulcs** a Customer Insights környeuetről](#get-started-trying-the-customer-insights-apis).    
   Szükség esetén állítsa vissza az **Engedélyezés** fejlécet. Ha például a token lejárt.

1. Adja át ezt a `HttpClient` elemet a `CustomerInsights` ügyfél felépítéséhez.

   :::image type="content" source="media/httpclient-sample.png" alt-text="Httpclient mintája":::

1. Indítson hívást a klienssel a „kiterjesztési módszerekhez”, például `GetAllInstancesAsync`. Ha az alapul szolgáló `Microsoft.Rest.HttpOperationResponse` elem elérését részesíti előnyben, használja a "http-üzenetek módszereit", például `GetAllInstancesWithHttpMessagesAsync`.

1. A válasz valószínűleg `object` típusú lesz, mert a módszer többféle típust képes visszaadni (például `IList<InstanceInfo>` és `ApiErrorResult`). A visszatérési típus ellenőrzéséhez biztonságosan konvertálhatja az objektumokat az adott művelet [API-részletek lapján](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) megadott választípusokká.    
   Ha a kérésre vonatkozóan további információra van szükség, akkor a **http-üzenetek módszereit** használhatja a nyers válasz objektum eléréséhez.

### <a name="nodejs-package"></a>NodeJS-csomag

Használja a NodeJS-ügyféltárakat, amelyek az NPM-en keresztül elérhetők: https://www.npmjs.com/package/@microsoft/customerinsights

### <a name="python-package"></a>Python-csomag

Használja a Python-ügyféltárakat, amelyek az PyPi-n keresztül elérhetők: https://pypi.org/project/customerinsights/

[!INCLUDE[footer-include](../includes/footer-banner.md)]
