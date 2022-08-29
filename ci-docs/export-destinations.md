---
title: Exportálások (előzetes verzió) áttekintése
description: Exportálások kezelése az adatok megosztásához.
ms.date: 08/12/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: overview
author: pkieffer
ms.author: philk
manager: shellyha
searchScope:
- ci-export
- ci-connections
- customerInsights
ms.openlocfilehash: c580b6c01e1b4ac6b095733193d86ebd0b4005f2
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304062"
---
# <a name="exports-preview-overview"></a>Exportálások (előzetes verzió) áttekintése

 Az exportálás lehetővé teszi, hogy bizonyos adatokat különböző alkalmazásokkal osszon meg. Magukban foglalhatják az ügyfélprofilokat, entitásokat, sémákat és a leképezések részleteit. Mindegyik exportáláshoz szükség van egy [rendszergazda kapcsolatra, beállításra, hogy kezelhesse a hitelesítést és a hozzáférést](connections.md). Az **Exportálások** lap megjeleníti az összes konfigurált exportálást.

## <a name="export-types"></a>Exporttípusok

Az exportálásnak két fő típusa van:  

- **Az adatkivételes exportálások** lehetővé teszik a Customer Insights szolgáltatásban elérhető bármilyen típusú entitás exportálását. Az exportáláshoz kiválasztott entitásokat a rendszer az összes adatmezővel, metaadatmal, sémával és leképezési részlettel exportálja.
- **A szegmensexportálás** lehetővé teszi szegmensentitások exportálását a Customer Insights szolgáltatásból. Az egyéni fogyasztók (B-től C-ig) esetében a szegmensek az ügyfélprofilok listáját jelentik. A vállalkozások (B-től B-ig) [esetében a szegmensek a partnerek vagy kapcsolattartók listáját jelenthetik](segment-builder.md#create-a-new-segment-with-segment-builder). Az exportálás konfigurálásakor kiválaszthatja a mellékelt adatmezőket attól függően, hogy melyik célrendszerbe exportálja az adatokat.

### <a name="export-segments"></a>Szegmensek exportálása

**Szegmensek exportálása üzleti számlák (B-to-B) vagy egyéni ügyfelek környezetbe (B-to-C)**  
A legtöbb exportálási lehetőség mindkét típusú környezetet támogatja. A szegmensek különböző célrendszerekbe történő exportálásának speciális követelményei vannak. 

**Szegmensexportálás az egyes ügyfelek környezeteibe (B-to-C)**  
- Az egyéni ügyfelek környezeteihez kapcsolódó szegmensek az *egységes ügyfélprofil* entitáson alapulnak. A célrendszerek (például egy e-mail-cím) követelményeinek megfelelő minden szegmens exportálható.

**Szegmensexportálás üzleti számlák környezetében (B-től B-ig)**  
- Az üzleti számlák környezetének kontextusában lévő szegmensek a fiókentitásra *vagy a* *kapcsolattartó* entitásra épülnek. A megfelelő partnerszegmensek exportálásához a célrendszernek támogatnia kell a partnerszegmenseket. Ez a [LinkedIn](export-linkedin-ads.md) esetében az az eset, amikor az exportálás definiálása során kiválasztja a **vállalat** beállítását.
- Minden más célrendszerhez a kapcsolattartói entitás mezői szükségesek.
- Két szegmenstípussal (kapcsolattartókkal és partnerekkel) a Customer Insights automatikusan azonosítja, hogy a célrendszer alapján mely szegmenstípusok jogosultak exportálásra. Például egy olyan kapcsolatközpontú célrendszer esetében, mint a Mailchimp, a Customer Insights csak az exportálni kívánt kapcsolattartói szegmensek kiválasztását teszi lehetővé.

**A szegmensexportálásra vonatkozó korlátozások**  
- A külső célrendszerek korlátozhatják az exportálható ügyfélprofilok számát. 
- Az egyes ügyfeleknél az exportálni kívánt szegmenstagok tényleges számát láthatja. Figyelmeztetést kap, ha egy szegmens túl nagy. 
- Üzleti fiókok esetén a szegmenstől függően láthatja a partnerek vagy kapcsolattartók számát. Figyelmeztetést kap, ha a szegmens túl nagy. A célrendszer eredményeinek túllépése kihagyja az exportálást.

## <a name="set-up-a-new-export"></a>Új exportálás beállítása

Exportálás beállításához vagy szerkesztéséhez a megfelelő kapcsolatokra van szüksége. A kapcsolatok a [felhasználói szerepkörtől](permissions.md) függnek:
- A **rendszergazdák** minden kapcsolathoz rendelkeznek hozzáféréssel. Az exportálás beállításakor új kapcsolatokat is létrehozhatnak.
- A **közreműködő** adott kapcsolatokhoz férhetnek hozzá. Ezek a rendszergazdáktól függnek, a kapcsolatok konfigurálásához és megosztásához. Az exportlista megmutatja, hogy a közreműködők szerkeszthetik-e vagy csak megtekinthetik-e az exportálást **Az Ön engedélyei** oszlopban. További tájékoztatásért menjen a [Munkatársak engedélyezése az exportáláshoz használható kapcsolat](connections.md#allow-contributors-to-use-a-connection-for-exports) oldalra.
- A **Megtekintők** csak a meglévő exportálásokat tekinthetik meg, de nem hozhatják létre azokat.

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. Az Exportálás **beállítása panelen válassza ki** a használni kívánt kapcsolatot [.](connections.md)

1. Adja meg a szükséges adatokat, majd az exportálás létrehozásához válassza a **Mentés** lehetőséget. A szükséges részletekért tekintse át az adott exportálás Customer Insights dokumentációját.

## <a name="manage-existing-exports"></a>Meglévő exportálások kezelése

Az **Adatexportálások** > **lapon** megtekintheti az exportálásokat, a kapcsolat nevét, a kapcsolat típusát és állapotát. Minden felhasználói szerepkör megtekintheti a konfigurált exportálást. Az exportálások listáját bármely oszlop szerint rendezheti, vagy a keresőmező segítségével megkeresheti a kezelni kívánt exportálást.

Válasszon ki egy exportálást az elérhető műveletek megtekintéséhez.

:::image type="content" source="media/exports_showmore.png" alt-text="Az oldal exportálása lap.":::

- **Az exportálás megtekintése** vagy **szerkesztése**. A szerkesztési engedélyekkel nem rendelkező felhasználók a **Nézet** lehetőséget választják a **Szerkesztés** helyett az exportálás részleteinek megtekintéséhez.
- **Futtassa** az exportálást a legfrissebb adatok exportálásához.
- **Exportálás duplikátumának** létrehozása.
- **[Ütemezze be](#schedule-and-run-exports)** az exportálást.
- **Válassza le a kapcsolatot** az exportálás kapcsolatának eltávolításához. A leválasztás nem távolítja el a kapcsolatot, hanem inaktiválja az exportálást. A **Kapcsolat használt** oszlopban a Nincs kapcsolat felirat jelenik meg.
- **Távolítsa el** az exportálást.

## <a name="schedule-and-run-exports"></a>Exportálás ütemezése ás futtatása

Minden konfigurált exportálás egy frissítési ütemezéssel rendelkezik. A frissítés során a rendszer új vagy frissített adatokat keres, amelyek szerepeljenek az exportálásban. Alapértelmezés szerint az exportálás minden [ütemezett rendszerfrissítés](schedule-refresh.md) részeként fut. Testreszabhatja a frissítési ütemezést, vagy ki is kapcsolhatja az exportálás manuális futtatásához.

Az exportálási ütemezések a környezet állapotától függenek. Ha folyamatban vannak frissítések [függőségeken](system.md#refresh-processes) ,amikor egy ütemezett exportálást el kell indítani, a rendszer először befejezi a frissítéseket, majd futtatja az exportálást. A **Frissített** oszlop azt mutatja meg, hogy mikor frissült utoljára az exportálás.

### <a name="schedule-exports"></a>Exportálások ütemezése

Egyéni frissítési ütemezéseket határozhat meg az egyes exportálásokhoz vagy egyszerre több exportáláshoz. A jelenleg meghatározott ütemezés az exportlista **Ütemezés** oszlopában található. Az ütemezés módosításának engedélye megegyezik [az exportálások](export-destinations.md#set-up-a-new-export) szerkesztésével és meghatározásával.

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza ki az exportálni kívánt ütemezést.

1. Válassza az **Ütemezés** lehetőséget.

1. Az **Exportálás ütemezése** ablaktáblában állítsa be az **Ütemezési futtatása** lehetőséget **Be** értékre az exportálás automatikus futtatásához. Állítsa **Ki** értékre manuálisan frissítéshez.

1. Az automatikusan frissített exporthoz válasszon egy **Ismétlődés** értéket, és adja meg annak részleteit. A definiált idő az ismétlődés minden esetére vonatkozik. Ez az az idő, amikor az exportálásnak frissülnie kell.

1. Válassza a **Mentés** parancsot.

Több exportálás ütemezésének szerkesztésekor válasszon az Ütemezések **megtartása vagy felülbírálása alatt**:

- **Egyéni ütemezések megtartása: Tartsa meg a kiválasztott exportálások** korábban meghatározott ütemezését, és csak tiltsa le vagy engedélyezze őket.
- **Új ütemezés definiálása az összes kiválasztott exportáláshoz**: A kijelölt exportálás meglévő ütemezésének felülírása.

### <a name="run-exports-on-demand"></a>Exportálások futtatása igény szerint

Ütemezett frissítésre való várakozás nélküli adatexportáláshoz menjen az **Adatok** > **Exportálások** lehetőségre.

- Az összes exportálás futtatásához válassza az **Összes futtatása** lehetőséget. Csak az aktív ütemezéssel rendelkező exportálások futnak. Nem aktív exportálás futtatásához futtasson egyetlen exportálást.
- Egyetlen exportálás futtatásához jelölje ki azt a listában, és válassza a **Futtatás** lehetőséget a parancssávon.

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="segment-not-eligible-for-export"></a>Exportálásra nem jogosult szegmens

**Probléma** Az üzleti fiókok környezetén belül az exportálás a következő hibaüzenettel meghiúsul: "A következő szegmens nem jogosult erre az exportálási célhelyre: '{szegmens} neve'. Kérjük, csak a ContactProfile típusú szegmenseket válassza ki, és próbálkozzon újra."

**Az üzleti fiókok Customer Insights-környezeteinek megoldása** frissítve lett, hogy a fiókszegmensek mellett a kapcsolattartói szegmenseket is támogassa. A változás miatt a kapcsolattartási adatokat igénylő exportálások csak a kapcsolattartókon alapuló szegmensekkel működnek.

1. [Hozzon létre egy szegmenst a névjegyek](segment-builder.md) alapján, amely megfelel a korábban használt szegmensnek.

1. A kapcsolattartói szegmens futtatása után szerkessze a megfelelő exportálást, és válassza ki az új szegmenst.

1. Válassza a Mentés **lehetőséget** a konfiguráció mentéséhez, vagy **a Mentés és futtatás lehetőséget** az exportálás azonnali teszteléséhez.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]


[!INCLUDE [footer-include](includes/footer-banner.md)]
