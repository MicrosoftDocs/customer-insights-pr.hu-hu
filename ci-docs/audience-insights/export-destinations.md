---
title: Adatok exportálása a Customer Insightsból
description: Exportálások kezelése az adatok megosztásához.
ms.date: 11/01/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: overview
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 05485fc7def3d699d5179bcaa005ceb57024f840
ms.sourcegitcommit: bb1ca84bc38e81fb2ff2961c457384b7beb5b5fa
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2022
ms.locfileid: "7977970"
---
# <a name="exports-preview-overview"></a>Exportálások (előzetes verzió) áttekintése

Az **Exportálások** lap megjeleníti az összes konfigurált exportálást. Az exportálások meghatározott adatokat osztanak meg különböző alkalmazásokkal. Magukban foglalhatják az ügyfélprofilokat, entitásokat, sémákat és a leképezések részleteit. Mindegyik exportáláshoz szükség van egy [rendszergazda kapcsolatra, beállításra, hogy kezelhesse a hitelesítést és a hozzáférést](connections.md).

Az exportálási lap megtekintéséhez menjen az **Adatok** > **Exportpálások** lehetőségre. Minden felhasználói szerepkör megtekintheti a konfigurált exportálást. A parancssáv keresőmezőjében keresse meg az exportot a nevük, a kapcsolatnevük vagy a kapcsolattípusuk alapján.

## <a name="export-types"></a>Exporttípusok

Az exportálásnak két fő típusa van:  

- A **Kimenő adatok exportálása** lehetővé teszi a közönségstatisztikákban elérhető bármely típusú entitás exportálását. Az exportáláshoz kiválasztott entitásokat a rendszer az összes adatmezővel, metaadatmal, sémával és leképezési részlettel exportálja. 
- A **Szegmensexportálások** segítségével szegmensentitásokat exportálhat a célközönség információkból. A szegmensek az ügyfélprofilok listáját reprezentálják. Az exportálás konfigurálásakor a célrendszertől függően válassza ki a szerepelt adatmezőket, amelyekbe az adatokat exportálja. 

### <a name="export-segments"></a>Szegmensek exportálása

**Szegmensek exportálása üzleti számlák (B-to-B) vagy egyéni ügyfelek környezetbe (B-to-C)**  
A legtöbb exportálási lehetőség támogatja mindkét típusú környezetet. A szegmensek különböző célrendszerekbe való exportálása konkrét követelményekkel jár. Általában a kapcsolatfelvételi szegmenstag, az ügyfélprofil tartalmazza a kapcsolatfelvételi adatokat. Bár ez általában az egyéni ügyfeleken (B-to-C) alapuló szegmensekre jellemző, nem feltétlenül ez az eset az üzleti számlákon (B-to-B) alapuló szegmensekre. 

**Üzleti számlák környezetének szegmensexportálása (B-to-B)**  
- Az üzleti partnerek környezetében a szegmensek a *partnerek* entitásán épülnek. A megfelelő partnerszegmensek exportálásához a célrendszernek támogatnia kell a partnerszegmenseket. Ez a [LinkedIn](export-linkedin-ads.md) esetében az az eset, amikor az exportálás definiálása során kiválasztja a **vállalat** beállítását.
- Minden más célrendszerhez a kapcsolattartói entitás mezői szükségesek. Annak biztosításához, hogy a partnerszegmensek beolvassa az adatokat a kapcsolódó kapcsolattartókból, a szegmens definíciójának a kapcsolattartó entitás projektattribútumainak kell részét vennie. További információk a [szegmensek és projektattribútumok konfigurálásról](segment-builder.md).

**Szegmensexportálás az egyes ügyfelek környezeteibe (B-to-C)**  
- Az egyéni ügyfelek környezeteihez kapcsolódó szegmensek az *egységes ügyfélprofil* entitáson alapulnak. A célrendszerek (például egy e-mail-cím) követelményeinek megfelelő minden szegmens exportálható.

**A szegmensexportálásra vonatkozó korlátozások**  
- A külső célrendszerek korlátozhatják az exportálható ügyfélprofilok számát. 
- Az egyes ügyfeleknél az exportálni kívánt szegmenstagok tényleges számát láthatja. Figyelmeztetés jelenik meg, ha egy szegmens túl nagy. 
- Az üzleti partnerek esetében egy-egy szegmensben látható a partnerek száma; az esetleg kivetített kapcsolattartók száma azonban nem fog megjelenni. Bizonyos esetekben ez ahhoz az exportált szegmenshez vezethet, amely ténylegesen több ügyfélprofilt tartalmaz, mint amit a célrendszer elfogad. A célrendszer eredményeinek túllépése kihagyja az exportálást. 

## <a name="set-up-a-new-export"></a>Új exportálás beállítása  
Az exportálás beállításához vagy szerkesztéséhez elérhető kapcsolatokra van szüksége. A kapcsolatok a [felhasználói szerepkörtől](permissions.md) függnek:
- A **rendszergazdák** minden kapcsolathoz rendelkeznek hozzáféréssel. Az exportálás beállításakor új kapcsolatokat is létrehozhatnak.
- A **közreműködő** adott kapcsolatokhoz férhetnek hozzá. Ezek a rendszergazdáktól függnek, a kapcsolatok konfigurálásához és megosztásához. Az exportlista megmutatja, hogy a közreműködők szerkeszthetik-e vagy csak megtekinthetik-e az exportálást **Az Ön engedélyei** oszlopban. További tájékoztatásért menjen a [Munkatársak engedélyezése az exportáláshoz használható kapcsolat](connections.md#allow-contributors-to-use-a-connection-for-exports) oldalra.
- A **Megtekintők** csak a meglévő exportálásokat tekinthetik meg, de nem hozhatják létre azokat.

### <a name="define-a-new-export"></a>Új exportálás definiálása

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. Az **Exportálás beállítása** ablaktáblában válassza ki a használni kívánt kapcsolatot. A [Kapcsolatokat](connections.md) a rendszergazdák kezelik. 

1. Adja meg a szükséges adatokat, majd az exportálás létrehozásához válassza a **Mentés** lehetőséget.

### <a name="define-a-new-export-based-on-an-existing-export"></a>Új exportálás definiálása meglévő export alapján

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Az exportálásáokat tartalmazó listán jelölje ki a duplikálni kívánt exportálást.

1. Válassza a **Duplikált elem létrehozása** lehetőséget a prancssávon az **Exportálás beállítása** panel megnyitásához, amely tartalmazza a kiválasztott exportálás részleteit.

1. Tekintse át és adaptálja át az exportálást, és válassza a **Mentés** lehetőséget új exportálás létrehozásához.

### <a name="edit-an-export"></a>Egy exportálás szerkesztése

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Az exportálásokat tartalmazó listán jelölje ki a szerkeszteni kívánt exportálást.

1. Válassza a parancssávon a **Szerkesztés** parancsot.

1. Módosítsa a frissíteni kívánt értékeket, majd válassza a **Mentés** lehetőséget.

## <a name="view-exports-and-export-details"></a>Exportálás és exportálás részleteinek megtekintése

Az exportálási célhelyek a létrehozása után az **Adatok** > **Exportálások** listán jelennek meg. Minden felhasználó láthatja, hogy mely adatok lettek megosztva, és hogy milyen állapotúak.

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. A szerkesztési engedélyekkel nem rendelkező felhasználók a **Nézet** lehetőséget választják a **Szerkesztés** helyett az exportálás részleteinek megtekintéséhez.

1. Az oldalsó ablaktáblán megjelenik egy exportálás konfigurációja. Az értékek a szerkesztési jogosultságok nélkül nem módosíthatók. Az exportálások lapra való visszatéréshez válassza a **Bezárás** lehetőséget.

## <a name="schedule-and-run-exports"></a>Exportálás ütemezése ás futtatása

Minden konfigurált exportálás egy frissítési ütemezéssel rendelkezik. A frissítés során a rendszer új vagy frissített adatokat keres, amelyek szerepeljenek az exportálásban. Alapértelmezés szerint az exportálás minden [ütemezett rendszerfrissítés](system.md#schedule-tab) részeként fut. Testreszabhatja a frissítési ütemezést, vagy ki is kapcsolhatja az exportálás manuális futtatásához.

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

Az exportálási ütemezések a környezet állapotától függenek. Ha folyamatban vannak frissítések [függőségeken](system.md#refresh-processes) ,amikor egy ütemezett exportálást el kell indítani, a rendszer először befejezi a frissítéseket, majd futtatja az exportálást. A **Frissítve** oszlopban láthatja, hogy mikor frissült utoljára egy exportálás.

### <a name="schedule-exports"></a>Exportálások ütemezése

Egyéni frissítési ütemezéseket az egyes exportálásokhoz és egyszerre több exportáláshoz is definiálhat. A jelenleg meghatározott ütemezés az exportlista **Ütemezés** oszlopában található. Az ütemterv módosításának engedélye megegyezik az [exportálások szerkesztése és definiálása](export-destinations.md#set-up-a-new-export) folyamattal. 

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza ki az exportálni kívánt ütemezést.

1. Válassza a parancssávon az **Ütemezés** lehetőséget.

1. Az **Exportálás ütemezése** ablaktáblában állítsa be az **Ütemezési futtatása** lehetőséget **Be** értékre az exportálás automatikus futtatásához. Állítsa **Ki** értékre manuálisan frissítéshez.

1. Az automatikusan frissített exporthoz válasszon egy **Ismétlődés** értéket, és adja meg annak részleteit. A definiált idő az ismétlődés minden esetére vonatkozik. Ez az az idő, amikor az exportálásnak frissülnie kell.

1. A módosítások alkalmazása és aktiválása a **Mentés** lehetőséget.

Több exportálás ütemezésének szerkesztésekor az **Ütemezés megtartása vagy felülbírálása** alatt válasszon:
- **Egyéni ütemezések megtartása**: A kiválasztott export korábban meghatározott ütemezésének fenntartása, és csak annak letiltása vagy engedélyezése.
- **Új ütemezés definiálása az összes kiválasztott exportáláshoz**: A kijelölt exportálás meglévő ütemezésének felülírása.

### <a name="run-exports-on-demand"></a>Exportálások futtatása igény szerint

Ütemezett frissítésre való várakozás nélküli adatexportáláshoz menjen az **Adatok** > **Exportálások** lehetőségre.

- Az összes exportálás futtatásához válassza az **Összes futtatása** lehetőséget. Ez a művelet csak olyan exportot futtat, amelyekhez aktív ütemezéssel rendelkezik.
- Egyetlen exportálás futtatásához jelölje ki azt a listában, és válassza a **Futtatás** lehetőséget a parancssávon. Így futtathat az exportálást aktív ütemezés nélkül. 

## <a name="remove-an-export"></a>Exportálás eltávolítása

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Jelölje ki az eltávolítandó exportálást.

1. A parancssávon válassza az **Eltávolítás** lehetőséget.

1. Erősítse meg az eltávolítást az **Eltávolítás** lehetőség választásával a megerősítő képernyőn.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
