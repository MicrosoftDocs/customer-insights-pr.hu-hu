---
ms.openlocfilehash: a67714de5aae80a0080c0e631ae6f8986eb2a003
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9611127"
---
- **Betanítási modell teljesítménye**: Az A, B vagy C fokozatok jelzik a előrejelzés teljesítményét, és segíthetnek a kimeneti entitásban tárolt eredmények használatára vonatkozó döntés meghozatalában.

  Az osztályzatot a következő szabályok határozzák meg:
  - **A** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint a viszonyítási alapérték, ami a legalább 10%.
  - **B** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint 10%, ami nagyobb, mint a viszonyítási alapérték.
  - **C**, ha a modell pontosan megjósolta az összes előrejelzés kevesebb mint 50%-át, vagy ha a pontos előrejelzések százalékos aránya a lemorzsolódott ügyfelek számára kisebb, mint az alapérték.
  - **Az alapkonfiguráció** a modell előrejelzés időablak bemenetét veszi fel (például egy év), és különböző időtöredékeket hoz létre úgy, hogy elosztja azt 2-vel, amíg el nem éri az egy hónapot vagy annál rövidebb időt. Ezen töredékek segítségével üzleti szabályokat hozhat létre azon ügyfeleknek, akik nem vásároltak ebben az időkeretben. Ezek az ügyfelek lemorzsolódónak vannak tekintve. Alapmodellként azt az időalapú üzleti szabályt választjuk alapmodellként, amely a legnagyobb mértékben képes megjósolni, hogy kik várhatók a lemorzsolódásra.

- **Lemorzsolódási valószínűség (ügyfelek száma)**: Ügyfelek csoportjai a lemorzsolódás előrejelzett kockázata alapján. [Igény szerint magas lemorzsolódási kockázattal rendelkező ügyfelek](../prediction-based-segment.md) szegmenseit is létrehozhatja. Az ilyen szegmensek segítségével felmérheti, hogy a szegmens tagsága esetén hol legyen a lezárás.

- **Legbefolyásosabb tényezők**: Az előrejelzés létrehozásakor a rendszer számos tényezőt vesz figyelembe. A tényezők mindegyikének megvan a fontossága, az összesített előrejelzés számításaiban, melyet a modell hoz létre. Ezekkel a tényezőkkel ellenőrizheti a előrejelzés eredményeit. Vagy használja ezeket az információkat később olyan szegmensek [létrehozásához, amelyek segíthetnek befolyásolni](../prediction-based-segment.md) az ügyfelek lemorzsolódási kockázatát.