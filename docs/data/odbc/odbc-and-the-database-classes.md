---
title: ODBC 和資料庫類別
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 6511aab9bb048882fe9c3398dd17f769eb16220c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320069"
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和資料庫類別

MFC ODBC 資料庫類封裝了您通常在[CDatabase](../../mfc/reference/cdatabase-class.md)和[CRecordset](../../mfc/reference/crecordset-class.md)類的成員函數中編寫的 ODBC API 函數調用。 例如,複雜的 ODBC 調用序列、返回的記錄綁定到存儲位置、處理錯誤條件以及其他操作由資料庫類為您管理。 因此,您可以使用更簡單的類介面通過記錄集物件操作記錄。

> [!NOTE]
> ODBC 資料來源可透過 MFC ODBC 類別(如本主題所述)或透過 MFC 資料存取物件 (DAO) 類別存取。

儘管資料庫類封裝了ODBC功能,但它們不提供ODBC API函數的一對一映射。 資料庫類提供更高級別的抽象,以 Microsoft Access 和 Microsoft Visual Basic 中找到的數據訪問物件建模。 有關詳細資訊,請參閱[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 基礎知識](../../data/odbc/odbc-basics.md)
