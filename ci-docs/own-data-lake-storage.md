---
title: Azure Data Lake Storage Saját Gen2-fiók használata
author: mukeshpo
description: További információ a Customer Insights-adatok tárolására a saját Azure Data Lake Storage fiók használatára vonatkozó követelményekről.
ms.author: mukeshpo
ms.date: 06/08/2022
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
ms.reviewer: mhart
ms.openlocfilehash: d2ff49c324c5c5c28213f362ff330d441fcb6052
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9246204"
---
# <a name="use-your-own-azure-data-lake-storage-gen2-account"></a>Azure Data Lake Storage Saját Gen2-fiók használata

Dynamics 365 Customer Insights lehetőséget ad arra, hogy az összes adatot a Gen2-ben [Azure Data Lake Storage tárolja](/azure/storage/blobs/data-lake-storage-introduction).

Az adatok Data Lake Storage-ba való mentésével elfogadja, hogy az adatokat a rendszer az adott Azure Storage-fiókhoz tartozó megfelelő földrajzi helyre továbbítja és ott tárolja. További információ: [Microsoft Adatvédelmi központ](https://www.microsoft.com/trust-center).

A Customer Insights [rendszergazdái környezeteket](create-environment.md) hozhatnak létre, és [megadhatják az adattárolási lehetőséget](create-environment.md#step-2-configure-data-storage) a folyamat során.

## <a name="prerequisites-to-use-your-storage-account"></a>A tárfiók használatának előfeltételei

- Azure Data Lake Storage a fiókoknak ugyanabban az Azure-régióban kell lenniük, amelyet a Customer Insights környezet létrehozásakor kiválasztott. A Customer Insights-környezet régióját az Admin **System** > **About** > **alatt** ellenőrizheti.
- Data Lake Storage Gen2-nek kell lennie, és engedélyeznie [kell](/azure/storage/blobs/create-data-lake-storage-account) hierarchikus névteret. A Gen1-tárfiókok nem támogatottak.
- A tárfiókon egy megnevezett `customerinsights` tárolónak kell lennie. Létre kell hoznia, mielőtt a saját Data Lake Storage-ját használná a Customer Insights szolgáltatásban. A Customer Insights környezetet beállító rendszergazdának szüksége van a Storage Blob Data közreműködő vagy Storage Blob Data Owner szerepkörre a tárfiókon vagy a `customerinsights` tárolón. További információ az engedélyek tárfiókban való hozzárendeléséről: [Tárfiók](/azure/storage/common/storage-account-create?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&tabs=azure-portal) létrehozása.

## <a name="connect-customer-insights-with-your-storage-account"></a>A Customer Insights összekapcsolása a tárfiókkal

Új környezet létrehozásakor győződjön meg arról, hogy a Data Lake Storage-fiók létezik, és minden előfeltétel teljesül.

1. A környezet létrehozása során az Adattárolás lépésben állítsa a **Kimeneti adatok** mentése beállítást **Gen2-re** **Azure Data Lake Storage.**
1. Válassza ki, hogyan csatlakoztassa a **tárhelyet**. Választhat az erőforrás-alapú és az előfizetés-alapú hitelesítési lehetőség közül. További információ: [Csatlakozás fiókhoz Azure Data Lake Storage egy Azure-szolgáltatásnévvel](connect-service-principal.md).
   - Azure-előfizetés **esetén** válassza ki a **tárolót tartalmazó** előfizetést **,** erőforráscsoportot **és** Storage-fiókot`customerinsights`.
   - A Fiókkulcs **mezőben** adja meg a **Data Lake Storage-fiók fióknevét** és **fiókkulcsát**. Ennek a hitelesítési módszernek a használata azt jelenti, hogy értesítést kap, ha a szervezet elforgatja a kulcsokat. A környezet konfigurációját [az elforgatáskor frissítenie kell](manage-environments.md#edit-an-existing-environment) az új kulccsal.
1. Válassza ki, hogy az Azure Private Link használatával szeretne-e csatlakozni a tárfiókhoz, és [kétlépéses folyamattal private link](security-overview.md#set-up-an-azure-private-link) hozza létre a kapcsolatot.

Amikor a rendszer feldolgozza az adatbetöltést, a rendszer létrehozza a megfelelő mappákat a tárfiókban. Az adatfájlok és a *model.json* fájlok a folyamat neve alapján jönnek létre, és kerülnek a mappákba.

Ha a Customer Insights több környezetét hozza létre, és úgy dönt, hogy az ilyen környezetek kimeneti entitásokat menti a tárfiókba, akkor a Customer Insights külön mappákat hoz létre az egyes környezetekhez, amelyek a `ci_environmentID` értékkel találhatók a tárolóban.
