---
title: Saját Azure Data Lake Storage Gen2-fiók használata
author: mukeshpo
description: Ismerje meg azokat a követelményeket, amelyek szerint a saját Azure Data Lake Storage fiókját kell használnia az Ügyfélelemzési adatok tárolására.
ms.author: mukeshpo
ms.date: 05/30/2022
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
ms.reviewer: mhart
ms.openlocfilehash: 9fcd7645e34bf310ac3a1b98a0dd9a60598b19dc
ms.sourcegitcommit: f5af5613afd9c3f2f0695e2d62d225f0b504f033
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2022
ms.locfileid: "8833946"
---
# <a name="use-your-own-azure-data-lake-storage-gen2-account"></a>Saját Azure Data Lake Storage Gen2-fiók használata

Dynamics 365 Customer Insights lehetőséget ad arra, hogy az összes adatot a Gen2-ben [Azure Data Lake Storage tárolja](/azure/storage/blobs/data-lake-storage-introduction).

Az adatok Data Lake Storage-ba történő mentésével Ön elfogadja, hogy az adatokat az adott Azure Storage-fiók megfelelő földrajzi helyére továbbítjuk és az adott Azure Storage-fiókhoz megfelelő földrajzi helyen tároljuk. További információt a Microsoft Adatvédelmi központ című témakörben [talál](https://www.microsoft.com/trust-center).

A Customer Insights rendszergazdái környezeteket hozhatnak [létre,](create-environment.md) és [megadhatják az adattárolási lehetőséget](create-environment.md#step-2-configure-data-storage) a folyamat során.

## <a name="prerequisites-to-use-your-storage-account"></a>A tárfiók használatának előfeltételei

- Azure Data Lake Storage a fiókoknak ugyanabban az Azure-régióban kell lenniük, amelyet a Customer Insights környezet létrehozásakor választott ki. A Customer Insights környezet régióját a Felügyeleti **rendszer névjegye** > **·** > **csoportban** ellenőrizheti.
- A Data Lake Storage-nak Gen2-nek kell lennie, és engedélyeznie kell [hierarchikus névteret](/azure/storage/blobs/create-data-lake-storage-account). A Gen1 tárfiókok nem támogatottak.
- Egy elnevezett `customerinsights` tárolónak léteznie kell a tárfiókban. Létre kell hoznia, mielőtt saját Data Lake Storage-t használna a Customer Insights alkalmazásban. A Customer Insights környezetet telepítő rendszergazdának szüksége van a Storage Blob Data közreműködő vagy a Storage Blob Data Owner szerepkörre a tárfiókban vagy a `customerinsights` tárolóban. Az engedély tárfiókban való hozzárendeléséről további információt a Tárfiók [létrehozása című témakörben talál](/azure/storage/common/storage-account-create?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&tabs=azure-portal).

## <a name="connect-customer-insights-with-your-storage-account"></a>Ügyfélelemzések összekapcsolása a tárfiókkal

Új környezet létrehozásakor győződjön meg arról, hogy a Data Lake Storage fiók létezik, és minden előfeltétel teljesül.

1. A környezet létrehozása során az Adattárolás **lépésben állítsa** a **Kimeneti adatok** mentése beállítást Gen2 **Azure Data Lake Storage értékre**.
1. Válassza ki, **hogyan csatlakoztassa a tárhelyet**. Választhat az erőforrás-alapú és az előfizetés-alapú hitelesítési lehetőség között. További információt a Csatlakozás fiókhoz egy [Azure Service Principal Azure Data Lake Storage használatával című témakörben talál](connect-service-principal.md).
   - Azure-előfizetés **esetén** válassza ki a **tárolót tartalmazó** Előfizetés **,** Erőforráscsoport **és** Tárfiókot`customerinsights`.
   - A Fiók kulcshoz **adja** meg a **Fiók nevét** és a **Data Lake Storage fiók Fiókkulcsát**. Ezzel a hitelesítési módszerrel a rendszer tájékoztatást kap arról, hogy a szervezet elforgatja-e a kulcsokat. Elforgatáskor frissítenie kell [a környezet konfigurációját](manage-environments.md#edit-an-existing-environment) az új kulccsal.

Amikor a rendszerfolyamatok, például az adatbetöltés befejeződött, a rendszer létrehozza a megfelelő mappákat a tárfiókban. Az adatfájlok és a *model.json* fájlok a folyamat neve alapján jönnek létre, és kerülnek a mappákba.

Ha a Customer Insights több környezetét hozza létre, és úgy dönt, hogy az ilyen környezetek kimeneti entitásokat menti a tárfiókba, akkor a Customer Insights külön mappákat hoz létre az egyes környezetekhez, amelyek a `ci_environmentID` értékkel találhatók a tárolóban.
