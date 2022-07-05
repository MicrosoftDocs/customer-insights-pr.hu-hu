---
title: Customer Insights API-k használata
description: Az API-k használata és a korlátozások megismerése.
ms.date: 05/10/2021
ms.reviewer: wimohabb
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
searchScope:
- ci-system-api-usage
- customerInsights
ms.openlocfilehash: 8e8bd590d3bba9dc7b1644b6ff42b9fc53237ca9
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9054067"
---
# <a name="work-with-customer-insights-apis"></a>Customer Insights API-k használata

Dynamics 365 Customer Insights API-kat biztosít saját alkalmazások elkészítéséhez a Customer Insight-ban szereplő adatai alapján.

> [!IMPORTANT]
> Az API-k részletes ismertetése a [Customer Insights API-k segédeletében](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) található. További információkat tartalmaznak a műveletekről, a paraméterekről és a válaszokról.

Ez a cikk azt ismerteti, hogyan férhet hozzá a Customer Insights API-khoz, hogyan hozhat létre Azure-alkalmazásregisztrációt, és hogyan kezdheti el használni az ügyfélkódtárakat.

## <a name="get-started-trying-the-customer-insights-apis"></a>Ismerkedés a Customer Insights API-k kipróbálásával

1. [Jelentkezzen be](https://home.ci.ai.dynamics.com) a Customer Insights szolgáltatásba. Ha még nincs előfizetése, [iratkozzon fel a Customer Insights próbaverziójára](https://aka.ms/tryci).

1. Ha engedélyezni szeretné az API-kat a Customer Insights-környezetben, lépjen a Rendszergazdai **biztonság oldalra** > **·**. Ehhez rendszergazdai engedélyekre van szükség.

1. Nyissa meg az **API-k** lapot, és jelölje be az **Engedélyezés** gombot.    
 
   Az API-k engedélyezésekor a rendszer elsődleges és másodlagos előfizetési kulcsot hoz létre az API-kérésekben használt példányhoz. A kulcsokat az Elsődleges **újragenerálás vagy** a **Másodlagos** újragenerálása a Rendszergazdai **biztonsági** > **API-kban** > **lehetőség** kiválasztásával hozhatja létre újra.

<!--  :::image type="content" source="media/enable-apis.gif" alt-text="Enable Customer Insights APIs."::: -->

1. Az **API-k kipróbálásához** válassza az [API-k kipróbálása](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances) lehetőséget.

1. Válasszon egy API-műveletet, és válassza a **Kipróbálásá** lehetőséget.

1. Az oldalsó táblában, állítsa az értéket az **Engedélyezés** legördüló menüben **implicit**-re. Az `Authorization` fejlécet egy tulajdonosi tokennel adták hozzá. Az előfizetési kulcsot a rendszer automatikusan kitölti.
  
1. Tetszés szerint hozzáadhatja az összes szükséges lekérdezési paramétert.

1. Görgessen az oldalsó panel aljára, és válassza a **Küldés** lehetőséget.

A HTTP-válasz hamarosan az alábbiakban jelenik meg.

<!--   :::image type="content" source="media/try-apis.gif" alt-text="How to test the APIs."::: -->

## <a name="create-a-new-app-registration-in-the-azure-portal"></a>Hozzon létre egy új alkalmazásregisztrációt az Azure Portalon

Ezek a lépések segítenek a Customer Insights API-k használatának megkezdésében egy Azure-alkalmazásban, delegált engedélyek használatával. Győződjön meg róla, hogy először töltse ki az [Első lépések szakaszt](#get-started-trying-the-customer-insights-apis).

1. Jelentkezzen be az [Azure portálba](https://portal.azure.com) weboldalára azzal a fiókkal, amely hozzáfér a Customer Insights adatokhoz.

1. A bal oldalon válassza az **Alkalmazásregisztrációk** lehetőséget.

1. Válassza az **Új regisztráció** lehetőséget, adja meg az alkalmazás nevét és a fiók típusát.

   Ha szeretne, megadhat egy átirányítási URL-címet. http://localhost elegendő az alkalmazások helyi számítógépen történő fejlesztéséhez.

1. Az új alkalmazás regisztrálásával nyissa meg az **API-engedélyeket**.

1. Válassza az Engedély hozzáadása lehetőséget **, majd válassza a Dynamics 365 AI for Customer Insights** lehetőséget **az oldalsó ablaktáblán.**

1. Az **Engedély típusa** parancshoz válassza a **Delegált engedélyek** lehetőséget, majd válassza ki a **Felhasználó megszemélyesítés** engedélyt.

1. Jelölje be az **Engedélyek hozzáadása** lehetőséget. Ha felhasználói bejelentkezés nélkül kell elérnie az API-t, tekintse át a [Kiszolgálók közötti alkalmazásengedélyek](#server-to-server-application-permissions) szakaszt.

1. Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.

Használhatja az alkalmazás/ügyfélazonosítót az alkalmazásregisztrációhoz a Microsoft hitelesítési függvénytárral (MSAL), hogy megszerezze a tulajdonosi jogkivonatot, amelyet elküldhet a kéréssel az API-nak.

<!-- :::image type="content" source="media/grant-admin-consent.gif" alt-text="How to grant admin consent."::: -->

Az MSAL-lel kapcsolatos további információkért tekintse át a [Microsoft hitelesítési függvénytár (MSAL) áttekintése](/azure/active-directory/develop/msal-overview).

Az Azure-ban történő alkalmazásregisztrációval kapcsolatos további információkért lásd [Alkalmazás regisztrálása](/graph/auth-register-app-v2).

Az API-k ügyfélkódtárainkban való használatával kapcsolatos információkért lásd: [Customer Insights ügyfélkódtárak](#customer-insights-client-libraries).

### <a name="server-to-server-application-permissions"></a>Kiszolgálók közötti alkalmazásengedélyek

Az [alkalmazásregisztráció című szakasz](#create-a-new-app-registration-in-the-azure-portal) ismerteti, hogyan lehet olyan alkalmazást regisztrálni, amelyhez a felhasználónak be kell jelentkeznie a hitelesítéshez. Megtudhatja, hogyan hozhat létre olyan alkalmazásregisztrációt, amely nem igényel felhasználói beavatkozást, és futtatható egy kiszolgálón.

1. Az Azure portál alkalmazásregisztrációja után nyissa meg az **API-engedélyeket**.

1. Válassza az **Engedély hozzáadása** lehetőséget. 

1. Lépjen a **Szervezetem által használt API-k** lapra, és válassza ki a lista **Dynamics 365 AI for Customer Insights** elemét. 

1. Az **Engedély típusa** parancshoz válassza az **Alkalmazásengedélyek** lehetőséget, majd válassza ki a **CustomerInsights.Api.All** engedélyt.

1. Jelölje be az **Engedélyek hozzáadása** lehetőséget.

1. Az alkalmazás regisztrálásához lépjen vissza az **API-engedélyekhez**.

1. Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.

 <!--  :::image type="content" source="media/grant-admin-consent.gif" alt-text="How to grant admin consent."::: -->

1. Következtetésképp hozzá kell adnunk az alkalmazásregisztráció nevét felhasználóként a Customer Insightsban.  
   
   Nyissa meg a Customer Insightst, lépjen a Rendszergazdai biztonság elemre **, és válassza a Felhasználó** > **hozzáadása lehetőséget**.**·**

1. Keresse meg az alkalmazásregisztrációjának nevét, jelölje ki a keresési eredmények között, és válassza a **Mentés** lehetőséget.

## <a name="sample-queries"></a>Mintalekérdezések

Összeállítottuk az OData-mintalekérdezések rövid listáját az API-kkal való együttműködéshez: [OData-lekérdezési példák](odata-examples.md).

## <a name="customer-insights-client-libraries"></a>Customer Insights ügyféloldali tárak

Ez a szakasz segítséget nyújt a Customer Insights API-k számára elérhető ügyféloldali függvénytárak használatba vételéhez. Minden függvénytár-forráskód és mintaalkalmazás megtalálható a [Customer Insights GitHub oldalon](https://github.com/microsoft/Dynamics365-CustomerInsights-Client-Libraries). 

### <a name="c-nuget"></a>C# NuGet

Ismerje meg a C# ügyféloldali függvénytárak használatának első lépéseit a NuGet.org webhelyről. A NuGet csomaggal kapcsolatos további információkért lásd: [Microsoft.Dynamics.CustomerInsights.Api](https://www.nuget.org/packages/Microsoft.Dynamics.CustomerInsights.Api/). A csomag jelenleg a netstandard2.0 és a netcoreapp2.0 keretrendszert célozza meg.

#### <a name="add-the-c-client-library-to-a-c-project"></a>C# ügyféloldali függvénytár hozzáadása C#-projekthez

1. A Visual Studio szolgáltatásban nyissa meg a **NuGet csomagkezelő** elemet a projekthez.

1. Keresse meg a **Microsoft.Dynamics.CustomerInsights.Api**.

1. Válassza a **Telepítés** lehetőséget a csomag projekthez való hozzáadásához.
 
   Másik lehetőségként futtassa ezt a parancsot a **NuGet csomagkezelő konzolon**: `Install-Package -Id Microsoft.Dynamics.CustomerInsights.Api -Source nuget.org -ProjectName <project name> [-Version <version>]`

 <!--  :::image type="content" source="media/visual-studio-nuget-package.gif" alt-text="Add NuGet package to Visual Studio project."::: -->

#### <a name="use-the-c-client-library"></a>A C# ügyféloldali függvénytár használata

1. Használja a [Microsoft hitelesítési függvénytárat (MSAL)](/azure/active-directory/develop/msal-overview), és használja a `AccessToken` meglévő [Azure alkalmazásregisztrációt](#create-a-new-app-registration-in-the-azure-portal).

1. A jogkivonat sikeres hitelesítése és megszerzése után hozzon létre egy újat, vagy használjon egy meglévőt`HttpClient`, ha a **DefaultRequestHeaders "Authorization"** beállítása **Bearer "hozzáférési token"** és **Ocp-Apim-Subscription-Key** az előfizetési kulcsra [**van állítva a** Customer Insights-környezetből](#get-started-trying-the-customer-insights-apis).   
 
   Szükség esetén állítsa vissza az **Engedélyezés** fejlécet. Ha például a token lejárt.

1. Adja át ezt a `HttpClient` elemet a `CustomerInsights` ügyfél felépítéséhez.

<!--   :::image type="content" source="media/httpclient-sample.png" alt-text="Sample of httpclient."::: -->

1. Indítson hívást a klienssel a „bővítmény módszerekhez”, például `GetAllInstancesAsync`. Ha az alapul szolgáló `Microsoft.Rest.HttpOperationResponse` elem elérését részesíti előnyben, használja a "http-üzenetek módszereit", például `GetAllInstancesWithHttpMessagesAsync`.

1. A válasz valószínűleg `object` típusú lesz, mert a módszer többféle típust képes visszaadni (például `IList<InstanceInfo>` és `ApiErrorResult`). A visszatérési típus ellenőrzéséhez használja az adott művelet API-részletek oldalán [megadott](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) választípusokban található objektumokat.    
   
   Ha a kérésre vonatkozóan további információra van szükség, akkor a **http-üzenetek módszereit** használhatja a nyers válasz objektum eléréséhez.

### <a name="nodejs-package"></a>NodeJS-csomag

Használja a NodeJS-ügyféltárakat, amelyek az NPM-en keresztül elérhetők: https://www.npmjs.com/package/@microsoft/customerinsights

### <a name="python-package"></a>Python-csomag

Használja a Python-ügyféltárakat, amelyek az PyPi-n keresztül elérhetők: https://pypi.org/project/customerinsights/

[!INCLUDE [footer-include](includes/footer-banner.md)]
