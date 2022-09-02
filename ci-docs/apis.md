---
title: Customer Insights API-k használata
description: Az API-k használata és a korlátozások megismerése.
ms.date: 08/31/2022
ms.reviewer: wimohabb
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
searchScope:
- ci-system-api-usage
- customerInsights
ms.openlocfilehash: f499bff4a6ac07a88ff0f773b9cee77dc74989e8
ms.sourcegitcommit: 624b27bb65a0de1970dc1ac436643b493f0a31cf
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/31/2022
ms.locfileid: "9387343"
---
# <a name="work-with-customer-insights-apis"></a>Customer Insights API-k használata

Dynamics 365 Customer Insights API-kat biztosít saját alkalmazások elkészítéséhez a Customer Insight-ban szereplő adatai alapján.

> [!IMPORTANT]
> Az API-k részletes ismertetése a [Customer Insights API-k segédeletében](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) található. További információkat tartalmaznak a műveletekről, a paraméterekről és a válaszokról.

Próbálja ki a Customer Insights API-kat, hozzon létre egy Azure-alkalmazásregisztrációt, és kezdje el használni az ügyfélkódtárakat.

## <a name="get-started-trying-the-customer-insights-apis"></a>Ismerkedés a Customer Insights API-k kipróbálásával

Engedélyezze a Customer Insights API-kat, és próbálja ki őket. A Customer Insights rendszergazdájának engedélyeznie kell az API-hozzáférést a Customer Insights szolgáltatáshoz. A hozzáférés engedélyezése után bármely felhasználó használhatja az API-t az előfizetési kulccsal.

1. [Jelentkezzen be](https://home.ci.ai.dynamics.com) a Customer Insights szolgáltatásba. Ha még nincs előfizetése, [iratkozzon fel a Customer Insights próbaverziójára](https://aka.ms/tryci).

1. Lépjen a Rendszergazdai **biztonság lapra** > **·**, és válassza az **API-k** lapot.

1. Ha a környezethez való API-hozzáférés nincs beállítva, válassza az Engedélyezés **lehetőséget**.

   Az API-k engedélyezésekor a rendszer elsődleges és másodlagos előfizetési kulcsot hoz létre az API-kérésekben használt példányhoz. A kulcsok újragenerálásához válassza az ELSŐDLEGES **vagy** a **Másodlagos** újragenerálás lehetőséget az **API-k** lapon.

1. Válassza az API-k [**felfedezése lehetőséget**](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances) az API-k kipróbálásához.

1. Keressen és válasszon ki egy API-műveletet, **majd válassza a Kipróbálás lehetőséget**.

   :::image type="content" source="media/try-api.png" alt-text="Hogyan tesztelje az API-kat.":::

1. Az oldalsó táblában, állítsa az értéket az **Engedélyezés** legördüló menüben **implicit**-re. Az `Authorization` fejlécet egy tulajdonosi tokennel adták hozzá. A rendszer automatikusan kitölti az előfizetési kulcsot.
  
1. Tetszés szerint hozzáadhatja az összes szükséges lekérdezési paramétert.

1. Görgessen az oldalsó panel aljára, és válassza a **Küldés** lehetőséget.

   A HTTP-válasz a panel alján jelenik meg.

## <a name="create-a-new-app-registration-in-the-azure-portal"></a>Hozzon létre egy új alkalmazásregisztrációt az Azure Portalon

Hozzon létre egy új [alkalmazásregisztrációt](/graph/auth-register-app-v2) a Customer Insights API-k delegált engedélyekkel való használatához egy Azure-alkalmazásban.

1. Töltse ki az [Első lépések szakaszt](#get-started-trying-the-customer-insights-apis).

1. Jelentkezzen be az [Azure portálba](https://portal.azure.com) weboldalára azzal a fiókkal, amely hozzáfér a Customer Insights adatokhoz.

1. Keresse meg, majd válassza az Alkalmazásregisztrációk **lehetőséget**.

1. Válassza az **Új regisztráció** lehetőséget, adja meg az alkalmazás nevét és a fiók típusát.

   Ha szeretne, megadhat egy átirányítási URL-címet. http://localhost elegendő az alkalmazások helyi számítógépen történő fejlesztéséhez.

1. Válassza a **Regisztrálás** lehetőséget.

1. Az új alkalmazás regisztrálásával nyissa meg az **API-engedélyeket**.

1. Válassza az Engedély hozzáadása lehetőséget **, majd válassza a Dynamics 365 AI for Customer Insights** lehetőséget **az oldalsó ablaktáblán.**

1. Az **Engedély típusa** parancshoz válassza a **Delegált engedélyek** lehetőséget, majd válassza ki a **Felhasználó megszemélyesítés** engedélyt.

1. Jelölje be az **Engedélyek hozzáadása** lehetőséget.

1. Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.

1. Ha felhasználó bejelentkezése nélkül szeretne hozzáférni az API-hoz, válassza a [Kiszolgálók közötti alkalmazásengedélyek lehetőséget](#server-to-server-application-permissions).

Ehhez az alkalmazásregisztrációhoz az alkalmazásregisztrációhoz az alkalmazás-/ügyfél-azonosítót a [Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-overview) használatával beszerezheti egy tulajdonosi jogkivonat beszerzéséhez, amelyet a kéréssel együtt küldhet az API-nak.

<!-- :::image type="content" source="media/grant-admin-consent.gif" alt-text="How to grant admin consent."::: -->

Az API-k ügyfélkódtárainkban való használatával kapcsolatos információkért lásd: [Customer Insights ügyfélkódtárak](#customer-insights-client-libraries).

### <a name="server-to-server-application-permissions"></a>Kiszolgálók közötti alkalmazásengedélyek

Hozzon létre egy alkalmazásregisztrációt, amely nem igényel felhasználói beavatkozást, és futtatható egy kiszolgálón.

1. Az Azure portál alkalmazásregisztrációja után nyissa meg az **API-engedélyeket**.

1. Válassza az **Engedély hozzáadása** lehetőséget.

1. Lépjen a **Szervezetem által használt API-k** lapra, és válassza ki a lista **Dynamics 365 AI for Customer Insights** elemét.

1. Az **Engedély típusa** parancshoz válassza az **Alkalmazásengedélyek** lehetőséget, majd válassza ki a **CustomerInsights.Api.All** engedélyt.

1. Jelölje be az **Engedélyek hozzáadása** lehetőséget.

1. Az alkalmazás regisztrálásához lépjen vissza az **API-engedélyekhez**.

1. Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.

   <!--  :::image type="content" source="media/grant-admin-consent.gif" alt-text="How to grant admin consent."::: -->

1. Adja hozzá az alkalmazásregisztráció nevét felhasználóként a Customer Insights szolgáltatásban.

   1. Nyissa meg a Customer Insightst, lépjen a Rendszergazdai biztonság elemre **, és válassza a Felhasználók** > **hozzáadása lehetőséget**.**·**

   1. Keresse meg az alkalmazásregisztrációjának nevét, jelölje ki a keresési eredmények között, és válassza a **Mentés** lehetőséget.

## <a name="sample-queries"></a>Mintalekérdezések

Az API-kkal való OData-mintalekérdezések rövid listájáért lásd: [OData-lekérdezési példák](odata-examples.md).

## <a name="customer-insights-client-libraries"></a>Customer Insights ügyféloldali tárak

Ismerkedjen meg a Customer Insights API-khoz elérhető ügyfélkódtárak használatával. Minden függvénytár-forráskód és mintaalkalmazás megtalálható a [Customer Insights GitHub oldalon](https://github.com/microsoft/Dynamics365-CustomerInsights-Client-Libraries).

### <a name="c-nuget"></a>C# NuGet

Használja a .org C#-ügyfélkódtárait NuGet. A csomaggal kapcsolatos NuGet további információkért lásd: [Microsoft.Dynamics.CustomerInsights.Api](https://www.nuget.org/packages/Microsoft.Dynamics.CustomerInsights.Api/).

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

1. Indítson hívást a klienssel a „kiterjesztési módszerekhez”, például `GetAllInstancesAsync`. Ha az alapul szolgáló eszközhöz `Microsoft.Rest.HttpOperationResponse` való hozzáférés előnyben részesített, használja például a "http üzenet metódusokat", `GetAllInstancesWithHttpMessagesAsync` például .

1. A válasz valószínűleg `object` típus, mert a metódus több típust is vissza tud adni (például `IList<InstanceInfo>` és `ApiErrorResult`). A visszatérési típus ellenőrzéséhez használja az adott művelet API-részletek oldalán [megadott](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) választípusokban található objektumokat.

   Ha a kérésre vonatkozóan további információra van szükség, akkor a **http-üzenetek módszereit** használhatja a nyers válasz objektum eléréséhez.

### <a name="nodejs-package"></a>NodeJS-csomag

Használja a NodeJS-ügyféltárakat, amelyek az NPM-en keresztül elérhetők: https://www.npmjs.com/package/@microsoft/customerinsights

### <a name="python-package"></a>Python-csomag

Használja a Python-ügyféltárakat, amelyek az PyPi-n keresztül elérhetők: https://pypi.org/project/customerinsights/

[!INCLUDE [footer-include](includes/footer-banner.md)]
