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
ms.openlocfilehash: 4c436764649a1aa418e12300809482b45224dd46
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403838"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>動態集的 ODBC 驅動程式需求

在 MFC 的 ODBC 資料庫類別中，動態集是具有動態屬性的記錄集;它們會以特定方式與資料來源保持同步。 MFC 動態集（但不是順向記錄集）需要具有層級 2 API 一致性的 ODBC 驅動程式。 如果[資料來源](../../data/odbc/data-source-odbc.md)的驅動程式符合層級 1 API 集，您仍然可以同時使用可更新和唯讀的快照集和順向記錄集，而不是動態集。 不過，層級1的驅動程式可以支援可延伸提取和索引鍵集驅動資料指標的動態集。

在 ODBC 術語中，動態集和快照稱為「資料指標」。 資料指標是一種機制，用來追蹤其在記錄集中的位置。 如需有關動態集之驅動程式需求的詳細資訊，請參閱[動態集](../../data/odbc/dynaset.md)。 如需資料指標的詳細資訊，請參閱[開放式資料庫連接（ODBC）](/sql/odbc/microsoft-open-database-connectivity-odbc)檔。

> [!NOTE]
> 對於可更新的記錄集，您的 ODBC 驅動程式必須支援定位的 update 語句或 `::SQLSetPos` ODBC API 函式。 如果兩者都受到支援，MFC 會使用 `::SQLSetPos` 來提升效率。 或者，針對快照集，您可以使用資料指標程式庫，以提供可更新快照集集（靜態資料指標和定位 update 語句）的必要支援。

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)
