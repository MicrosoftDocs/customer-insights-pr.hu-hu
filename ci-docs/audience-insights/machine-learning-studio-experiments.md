---
title: Machine Learning Studio (klasszikus) kísérletek
description: Használjon Machine Learning Studio (klasszikus) modelleket a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 12/03/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: ameetj
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: b979dd177b7c6de1971c02a69748006d041e4d2c3e49a3639dba03212bd7acf9
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7033726"
---
# <a name="use-models-based-on-azure-machine-learning-studio-classic"></a>Azure Machine Learning Studio (klasszikus) modelleken alapuló modellek használata

A Dynamics 365 Customer Insights egyesített adatok a forrása a gépi tanulás modellek létrehozásának, amelyek további üzleti ismereteket hozhatnak létre. A Customer Insights integrál a Machine Learning Studióval (klasszikus) a saját egyéni modelljei használatával. Annak megtekintéséhez, hogy az Azure Machine Learningben kifeljesztett modellek hogyan vannak integrálva a Customer Insights szolgáltatással, tekintse meg az [Azure Machine Learning-kísérletek](azure-machine-learning-experiments.md).

## <a name="prerequisites"></a>Előfeltételek

- A Customer Insights szolgáltatás elérése
- Aktív Azure Enterprise-előfizetés
- [Egyesített ügyfélprofilok](data-unification.md)
- [Entitás exportálása az Azure Blob Storage tárhelyre](export-azure-blob-storage.md) – beállítás

## <a name="set-up-machine-learning-studio-classic"></a>Machine Learning Studio (klasszikus) beállítása

Első lépésként létre kell hoznia egy munkaterületet, és meg kell nyitnia a Machine Learning Studio (klasszikus) alkalmazást.

1. Lépjen a [https://www.portal.azure.com](https://www.portal.azure.com/) alkalmazáshoz, és jelentkezzen be.

1. Válassza az **Erőforrás létrehozása** lehetőséget.

1. Keresse meg a **Machine Learning Studio munkaterületet**, és válassza a **Létrehozás** lehetőséget.

1. Adja meg a [munkaterület létrehozásához](/azure/machine-learning/studio/create-workspace) szükséges adatokat. Válassza ki a **Webszolgáltatási csomag tarifacsomag** az importálni kívánt adatok mennyiségétől függően. A legjobb teljesítmény érdekében válassza ki a földrajzilag legközelebb eső **Helyet**.

1. Az erőforrás létrehozása után megjelenik a Machine Learning Studio munkaterület irányítópultja. Válassza a **Machine Learning Studio indítása** lehetőséget.

   ![Az Azure Machine Learning Studio felhasználói felülete.](media/azure-machine-learning-studio.png)

## <a name="work-with-azure-machine-learning-studio"></a>Az Azure Machine Learning Studio használata

Ezután létrehozhat egy új kísérletet, vagy importálhat egy meglévő kísérlet sablont a mintakatalógusból. Három szabványos esetre vonatkozóan vannak mintakísérletek:

- [Ügyfél-lemorzsolódás előrejelzése](#churn-analysis)

- [Ügyfélélettartam értéke](#customer-lifetime-value-prediction)

- [Termék ajánlása vagy a következő legjobb művelet](#productrecommendation-or-next-best-action)

1. Ha új kísérletet hoz létre, vagy a katalógusból használ kísérleti sablont használ, akkor be kell állítania az **Adatimportálás** tulajdonságait. Használja az interaktív élményt, vagy közvetlenül adja meg az adatokat tartalmazó Azure Blob Storage eléréséhez használható adatokat.  

   ![Azure Machine Learning Studio kísérlet.](media/azure-machine-learning-studio-experiment.png)

1. Most már létrehozhat egy egyéni feldolgozási folyamatot az adatok tisztításához és előfeldolgozásához, a funkciók kinyeréséhez és egy megfelelő modell betanításához.

1. Tesztelje és optimalizálja a modell teljesítményét.

1. Ha elégedett a modell minőségével, válassza a **Webszolgáltatás beállítása** > **Prediktív webszolgáltatás** lehetőséget. Ezzel a lehetőséggel a betanított modellt és a jellemzőkre bontó csővezetéket importálja a tanítási kísérletből a prediktív kiszolgálásba. A prediktív szolgáltatás egy másik bemeneti adatkészletet is fogadhat a tanítási kísérletben használt sémával előrejelzések készítéséhez.

   ![Prediktív webszolgáltatás beállítása.](media/predictive-webservice-control.png)

1. Ha a prediktív webszolgáltatási kísérlet sikeres, akkor az automatikus ütemezéshez üzembe helyezheti azt. Ha azt szeretné, hogy a webszolgáltatás működjön együtt a Customer Insights alkalmazással, válassza **Webszolgáltatás központi telepítése** > **Webszolgáltatás [új] előzetes verzió központi telepítése** lehetőséget. [További információk webszolgáltatás telepítéséről](/azure/machine-learning/studio/deploy-a-machine-learning-web-service).

   ![Prediktív webszolgáltatás telepítése.](media/predictive-webservice-deploy.png)

## <a name="sample-models-from-the-gallery"></a>Mintamodellek a galériából

A cikkben található modellekhez a Contoso Hotel kitalált forgatókönyvét használjuk. A Contoso Hotel következő adatokat gyűjti:

- A hotelben tartózkodás tevékenységből álló CRM-adatok. A adatkészlet információkat tartalmaz az egyes regisztrált ügyfelek tartózkodásának dátumairól. Tartalmaz továbbá információkat a helyfoglalásokról, a szobatípusokről, a tartózkodás részleteiről stb. Az adatok négy évet ölelnek fel, 2014. január és 2018. január között.
- A szálloda vendégeinek ügyfélprofiljai. Ezek a profilok az egyes ügyfelekre vonatkozó információkat tartalmaznak, beleértve a nevüket, a születési nevet, a lakcímet, a nemet és a telefonszámot.
- A szálloda szolgáltatásainak használata, többek között a fürdő, a mosoda, a Wi-Fi vagy a futár. Ez az információ minden regisztrált ügyfélhez naplózva van. Általában a szolgáltatások használata a tartózkodáshoz van kapcsolva. Bizonyos esetekben a szolgáltatásokat az ügyfelek használhatják anélkül, hogy a szállodában tartózkodnának.

## <a name="churn-analysis"></a>Lemorzsolódási analízis

A lemorzsolódás elemzése a különböző üzleti területekre vonatkozik. Ebben a példában a szolgáltatáshoz kapcsolódó lemorzsolódást tekintjük meg, amely kifejezetten a fent ismertetett szállodai szolgáltatások kontextusában. Ez egy működő példája egy teljes körű modell folyamatnak, amely kiindulási pontként használható bármely más típusú lemorzsolódási modellhez.

### <a name="definition-of-churn"></a>A lemorzsolódás meghatározása

A lemorzsolódás meghatározása az esettől függően változhat. Ebben a példában egy olyan vendégnek, aki az elmúlt évben nem járt a szállodában lemorzsolódónak kell lennie.  

A kísérlet sablont importálhatja a katalógusból. Első lépésként ügyeljen arra, hogy az Azure Blob Storage szolgáltatásból importálja a **Hotelben tartózkodás tevékenységeit**, az **Ügyféladatokat** és a **Szolgáltatáshasználat adatait** az Azure Blob Storage tárhelyről.

   ![Adatok importálása a lemorzsolódási modellhez.](media/import-data-azure-blob-storage.png)

### <a name="featurization"></a>Jellegzetességek megadása

A lemorzsolódás meghatározása alapján először azonosítani kell a címkét befolyásoló nyers funkciókat. Ezt követően ezeket a nyers funkciókat a gépi tanulás modellekkel használható numerikus függvényekké dolgozzuk fel. A Customer Insightsban adatintegráció történik, így összekapcsolhatja ezeket a táblákat az *Ügyfélazonosító* segítségével.

   ![Importált adatok egyesítése.](media/join-imported-data.png)

A modell kiépítésének jellemzőkre bontása a lemorzsolódás elemzéséhez kicsit trükkös lehet. Ez az adat egy időfüggvény új szállodai tevékenységgel, amelyet napi rendszerességgel rögzítettek. A jellemzőkre bontás során statikus funkciókat szeretnénk létrehozni a dinamikus adatokból. Ebben az esetben a szállodai tevékenységből több jellemzőt is létrehozunk egy év csúszó ablakával. Kiterjesztjük a kategorikus jellemzőket is, mint a szoba típusa vagy a foglalás típusa különálló jellemzőkké one-hot kódolással.  

A jellemzők végső listája:

| **Szám**  | **Original_Column**          | **Származtatott jellemzők**                                                                                                                      |
|-------------|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 1           | Szoba típusa                    | RoomTypeLargeCount, RoomTypeSmallCount                                                                                                    |
| 2           | Foglalás típusa                 | BookingTypeOnlineCount, BookingTypePhoneCallCount                                                                                         |
| 3           | Utazási kategória              | TravelCategoryBusinessCount, TravelCategoryLeisureCount                                                                                   |
| 4           | Elköltött pénz                | TotalDollarSpent                                                                                                                          |
| 5           | Bejelentkezés és kijelentkezés dátuma  | StayDayCount, StayDayCount2016, StayDayCount2015, StayDayCount2014, StayCount, StayCount2016. StayCount2015, StayCount2014                |
| 6           | Szolgáltatáshasználat                | UsageTenure, ConciergeUsage, CourierUsage, DryCleaningUsage, GymUsage, PhoneUsage, RestaurantUsage, SpaUsage, TelevisionUsage, WifiUsage  |

### <a name="model-selection"></a>Modellválasztás

Most ki kell választani a használandó optimális algoritmust. Ebben az esetben a legtöbb jellemző a kategorikus jellemzőkön alapul. A döntési fa alapú modelek általában jól működnek. Ha csak numerikus jellemzők vannak, a neurális hálózatok jobb választást jelenthetnek. A Support Vector Machine (SVM) is jó jelölt az ilyen helyzetekben; ugyanakkor jelenetős mennyiségű finomhangolás szükséges a legjobb teljesítményhez. Úgy döntünk, hogy **Kétosztályos erősített döntési fát** használunk első modellként, amit a **kétszintű SVM** követ második modellként. Az Azure Machine Learning Studio lehetővé teszi, hogy A/B tesztelést végezzen, ezért érdemes egy helyett két modellel kezdeni a kezdést.

A következő kép bemutatja a modell tanítási és értékelési folyamatát az Azure Machine Learning Studio alkalmazásból:

![Az Azure Machine Learning Studio lemorzsolódási modellje.](media/azure-machine-learning-model.png)

Mi is alkalmazzuk a **Permutációs tulajdonság fontossága** technikát, ami fontos szempontja a modell optimalizálása. A beépített modellek nem tudnak betekintést kapni a végső előrejelzés adott jellemzőire gyakorolt hatásra. A jellemzők fontossága a kalkulátor egyéni algoritmus segítségével számítja ki az egyes jellemzők hatását egy adott modell kimenetelére. A jellemző fontossága a +1 és -1 közötti normalizált. A negatív hatás azt jelenti, hogy a kapcsolódó jellemző nem intuitív módon befolyásolja az eredményt, és el kell távolítani a modellből. A pozitív hatás azt jelzi, hogy a funkció nagy mértékben hozzájárul a előrejelzéshez. Ezek az értékek nem korrelációs együtthatók, mivel ezek eltérő mérőszámok. További információkért lásd:[Permutációs tulajdonság fontossága](/azure/machine-learning/studio-module-reference/permutation-feature-importance).

A teljes [lemorzsolódási kísérlet az Azure AI Gallery-ben érhető el](https://gallery.azure.ai/Experiment/Hotel-Churn-Predictive-Exp).

## <a name="customer-lifetime-value-prediction"></a>Ügyfélélettartam érték előrejelzése

Az ügyfélélettartam-érték (CLTV) kiszámítása az egyik olyan kulcsfontosságú mérőszám, amelyet egy vállalat az ügyfelek értékelése és szegmentálása céljából használhat. A szállodai üzlet szempontjából fontos, hogy megismerjék ügyfeleiket. A jó ügyfeleket alkotó tényezők megértése például alapvető fontosságú információ. Ez segíti a szállodai menedzsmentet, hogy milyen szolgáltatásokra kell összpontosítaniuk, és, hogyan tehetik elégedetté jól fizető ügyfeleiket. Ezek a döntések közvetlen hatással lehetnek az értékesítésre és a bevételekre.  

### <a name="definition-of-cltv"></a>A CLTV definíciója

Ebben a példában egy ügyfél CLTV-jét abban az összegben határozzuk meg amelyet az ügyfél várhatóan a következő 365 napban el fog költeni. Az elmúlt három év adatait használjuk az összes ügyfél számára, hogy megjósoljuk ezt az értéket.

### <a name="featurization"></a>Jellegzetességek megadása

Ebben az esetben a jellemzőkre bontás nagyon hasonlít a lemorzsolódásnál látottakra. A címkék és a várható értékek azonban eltérnek a fenti meghatározástól.

### <a name="model-selection"></a>Modellválasztás

A CLTV előrejelzése egy regressziós probléma, mivel a becsült érték egy pozitív, folytonos változó. A szolgáltatás tulajdonságai alapján az egyik algoritmus a **Súlyozott döntésifa-regresszió**, a másik a **Neurális hálózati regresszió**, amit használunk a modell tanításához.

## <a name="product-recommendation-or-next-best-action"></a>Termék ajánlása vagy a Következő legjobb művelet

A termékajánlást szállodai környezetben úgy értelmezzük, hogy a hitel ügyfeleinek kínált szolgáltatásokat ajánlják. A cél a megfelelő szolgáltatások kiválasztása az ügyfelek számára, hogy a használatuk maximáli szintű legyen. Hasonló a videó streaming szolgáltatás felhasználóinál alkalmazott videókra vonatkozó ajánlásokhoz.

### <a name="definition-of-product-recommendation-or-next-best-action"></a>Termék ajánlása vagy a Következő legjobb művelet definiálása

A célt úgy határozjuk meg, hogy a lehető legnagyobb értékű szolgáltatáshasználatot érjük el, úgy, hogy a számukra leginkább megfelelő szolgáltatásokat nyújtjuk a szállodai ügyfeleknek az érdeklődésük alapján.

### <a name="featurization"></a>Jellegzetességek megadása

A lemorzsolódás modelljéhez hasonlóan egyestíjük a szálloda ServiceCustomerID és CustomerID entitásait, hogy konzisztens módon hozzunk létre ajánlásokat CustomerID alapján.

![Az ajánlási modell jellemzőkre bontása.](media/azure-machine-learning-model-featurization.png)

Az adatok három különböző entitásból származnak és a jellemzők ezekből vannak származtatva. Az ajánlás problematikájához kapcsolódó jellemzőkre bontás más mint az lemorzsolódási és CLTV forgatókönyvek esetében. Az ajánlási modellnek három jellemzőcsoport formájában van szüksége bemeneti adatokra.

### <a name="model-selection"></a>Modellválasztás

A termékeket vagy szolgáltatásokat a **Matchbox-ajánló betanítása** algoritmusával jósoljuk meg az ajánlási modell betanításához.

![Termékjavaslat-algoritmus.](media/azure-machine-learning-model-recommendation-algorithm.png)

A **Matchbox-ajánló betanítása** három bemenete a betanítási szolgáltatás használati adatait, az ügyfél leírását (nem kötelező) és a szolgáltatás leírását kéri be. A modelleket három különböző módon lehet pontozni. Az egyik a modell értékelése, ahol a Normalizált diszkontált kumulatív nyereséget (NDCG) pontszám lesz kiszámítva az értékelt elemek rangsorolásához. Ebben a kísérletben az NDCG pontszáma 0,97. A másik két lehetőség a modell pontozása a teljes ajánlott szolgáltatáskatalóguson, vagy csak olyan elemek pontozása, amelyeket a felhasználók korábban még nem használtak.

A teljes szolgáltatási katalógusra vonatkozó ajánlások eloszlása alapján megfigyelhető, hogy a telefon, a Wi-Fi és a futár a legfelső szintű szolgáltatás, amelyet érdemes ajánlani. Ez összhangban áll azzal, amit találtunk a szolgáltatásifogyasztási-adatok eloszlásakor:

![Javaslati modell kimenete.](media/azure-machine-learning-model-output.png)

A teljes [termékajánlási kísérlet elérhető az Azure AI Gallery-ben.](https://gallery.azure.ai/Experiment/Recommendation-4)

## <a name="integrate-custom-models"></a>Egyéni modellek integrálása

Ahhoz, hogy ezeket az előrejelzéseket használni lehessen a Customer Insights alkalmazásban, az ügyfelek azonosítói mellett **exportálnia** kell az előrejelzéseket is. [Exportálja őket ugyanabba az Azure Blob Storage helyre](/azure/storage/common/storage-import-export-data-from-blobs), ahova a forrásadatokat exportálta. A prediktív webszolgáltatás rendszeresen futtatható, és a pontszámokat frissítheti.

Az egyéni modell által létrehozott adatok segítségével tovább bővítheti az ügyféladatokat. További tudnivalókat az [Egyéni gépi tanulás modellek](custom-models.md) című rész tartalmaz.


[!INCLUDE[footer-include](../includes/footer-banner.md)]