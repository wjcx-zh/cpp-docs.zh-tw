---
title: 動態集的 ODBC 驅動程式需求
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: c612e8ea91882a6e744a8f47afe0decbeba85358
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367207"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>動態集的 ODBC 驅動程式需求

在 MFC ODBC 資料庫類中,動態集是具有動態屬性的記錄集;它們在某些方面與數據源保持同步。 MFC 動態集(但不只轉發記錄集)需要具有 2 級 API 一致性的 ODBC 驅動程式。 如果[資料源](../../data/odbc/data-source-odbc.md)的驅動程式符合 1 級 API 集,您仍可以使用可更新和唯讀快照和僅轉發記錄集,但不能使用動態集。 但是,如果級別 1 驅動程式支援擴展提取和鍵集驅動的遊標,則可以支援動態集。

在 ODBC 術語中,動態集和快照稱為游標。 游標是用於跟蹤其在記錄集中的位置的機制。 有關發電機集的驅動程式要求的詳細資訊,請參閱[動態集](../../data/odbc/dynaset.md)。 有關游標的詳細資訊,請參閱 MSDN 文檔中[的開放資料庫連接 (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) SDK。

> [!NOTE]
> 對於可更新的記錄集,您的 ODBC 驅動程式必須支援定位更新語`::SQLSetPos`句或 ODBC API 功能。 如果兩者都支援,MFC`::SQLSetPos`用於提高效率。 或者,對於快照,可以使用遊標庫,該庫為可更新快照(靜態游標和定位更新語句)提供所需的支援。

## <a name="see-also"></a>另請參閱

[ODBC 基礎知識](../../data/odbc/odbc-basics.md)
