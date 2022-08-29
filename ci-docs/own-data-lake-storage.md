---
title: Azure Data Lake Storage Saját Gen2-fiók használata
author: mukeshpo
description: További információ a Customer Insights-adatok tárolására a saját Azure Data Lake Storage fiók használatára vonatkozó követelményekről.
ms.author: mukeshpo
ms.date: 08/15/2022
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
ms.reviewer: mhart
ms.openlocfilehash: 5e4b9348f06d4e5e10b4499ad86b38c9d52da1f5
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304384"
---
# <a name="use-your-own-azure-data-lake-storage-gen2-account"></a>Azure Data Lake Storage Saját Gen2-fiók használata

Dynamics 365 Customer Insights lehetőséget ad arra, hogy az összes adatot a Gen2-ben [Azure Data Lake Storage tárolja](/azure/storage/blobs/data-lake-storage-introduction). Az adatok Data Lake Storage-ba való mentésével elfogadja, hogy az adatokat a rendszer az adott Azure Storage-fiókhoz tartozó megfelelő földrajzi helyre továbbítja és ott tárolja. További információ: [Microsoft Adatvédelmi központ](https://www.microsoft.com/trust-center).

A Customer Insights [rendszergazdái környezeteket](create-environment.md) hozhatnak létre, és [megadhatják az adattárolási lehetőséget](create-environment.md#step-2-configure-data-storage) a folyamat során.

## <a name="prerequisites"></a>Előfeltételek

- Azure Data Lake Storage a fiókoknak ugyanabban az Azure-régióban kell lenniük, amelyet a Customer Insights környezet létrehozásakor kiválasztott. A környezet régiójának megismeréséhez nyissa meg a Felügyeleti **rendszer** > **névjegye** > **a** Customer Insightsban.
- A Data Lake Storage fióknak Gen2-nek kell lennie. Az Azure Data Lake Gen1-tárfiókok nem támogatottak.
- A Data Lake Storage-fiókban engedélyezni [kell](/azure/storage/blobs/data-lake-storage-namespace) hierarchikus névteret.
- A tárfiókon egy megnevezett `customerinsights` tárolónak kell lennie. Hozza létre, mielőtt a saját Data Lake Storage-ját használná a Customer Insightsban.
- A Customer Insights környezetet beállító rendszergazdának szüksége van a Storage Blob Data közreműködő vagy Storage Blob Data Owner szerepkörre a tárfiókon vagy a `customerinsights` tárolón. További információ az engedélyek tárfiókban való hozzárendeléséről: [Tárfiók](/azure/storage/common/storage-account-create?toc=%2Fazure%2Fstorage%2Fblobs%2Ftoc.json&tabs=azure-portal) létrehozása.

## <a name="connect-customer-insights-with-your-storage-account"></a>A Customer Insights összekapcsolása a tárfiókkal

Új környezet létrehozásakor győződjön meg arról, hogy a Data Lake Storage-fiók létezik, és minden előfeltétel teljesül.

1. A környezet létrehozása során az Adattárolás lépésben állítsa a **Kimeneti adatok** mentése beállítást **Gen2-re** **Azure Data Lake Storage.**
1. Válassza ki, hogyan csatlakoztassa a **tárhelyet**. Választhat az erőforrás-alapú és az előfizetés-alapú hitelesítési lehetőség közül. További információ: [Csatlakozás fiókhoz Azure Data Lake Storage egy Azure-szolgáltatásnévvel](connect-service-principal.md).
   - Azure-előfizetés **esetén** válassza ki a **tárolót tartalmazó** előfizetést **,** erőforráscsoportot **és** Storage-fiókot`customerinsights`.
   - A Fiókkulcs **mezőben** adja meg a **Data Lake Storage-fiók fióknevét** és **fiókkulcsát**. Ennek a hitelesítési módszernek a használata azt jelenti, hogy értesítést kap, ha a szervezet elforgatja a kulcsokat. A környezet konfigurációját [az elforgatáskor frissítenie kell](manage-environments.md#edit-an-existing-environment) az új kulccsal.
1. Válassza ki, hogy az Azure Private Link használatával szeretne-e csatlakozni a tárfiókhoz, és [létre szeretné-e hozni a kapcsolatot a Private Link](security-overview.md#set-up-an-azure-private-link).

Amikor a rendszer feldolgozza az adatbetöltést, a rendszer létrehozza a megfelelő mappákat a tárfiókban. Az adatfájlok és a model.json fájlok a folyamat neve alapján jönnek létre, és kerülnek a mappákba.

Ha a Customer Insights több környezetét hozza létre, és úgy dönt, hogy az ilyen környezetek kimeneti entitásokat menti a tárfiókba, akkor a Customer Insights külön mappákat hoz létre az egyes környezetekhez, amelyek a `ci_environmentID` értékkel találhatók a tárolóban.
