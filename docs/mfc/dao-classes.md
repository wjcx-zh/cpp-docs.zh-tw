---
title: DAO 類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 238aab0a1948f16a85b8ea16719b75b49f5e69c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241597"
---
# <a name="dao-classes"></a>DAO 類別

這些類別會使用相同的資料庫引擎做為 Microsoft Visual Basic 和 Microsoft Access 的資料存取物件 (DAO) 資料庫以便輕鬆存取的其他應用程式架構類別。 DAO 類別也可以存取各種不同的開放式資料庫連接 (ODBC) 驅動程式可供使用的資料庫。

供 DAO 資料庫程式也必須在至少`CDaoDatabase`物件和`CDaoRecordset`物件。

> [!NOTE]
>  視覺效果C++環境和精靈不再支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 建議您針對新的 MFC 專案，使用 ODBC。 您只應該使用 DAO，在維護現有的應用程式。

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
管理登入的具名、 受密碼保護的資料庫工作階段，以登出。 大部分程式會使用預設工作區。

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
透過這個中，您可以操作資料的資料庫的連接。

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
表示選取自資料來源的資料錄集。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
在控制項中顯示資料庫記錄的檢視。

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
表示查詢定義，通常是已儲存於資料庫中。

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
表示儲存的基底資料表或附加資料表定義。

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
表示從 DAO 類別所引發的例外狀況。

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。 您通常不會直接使用這個類別。

## <a name="related-classes"></a>相關的類別

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封裝的二進位大型物件 (BLOB)，儲存體的控制代碼，例如點陣圖。 `CLongBinary` 物件用來管理儲存在資料庫資料表中的大型資料物件。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE automation 類型包裝函式**貨幣**，定點算術類型，則 15 位數，小數點之前與之後有 4 位數。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE automation 類型包裝函式**日期**。 表示日期和時間值。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE automation 類型包裝函式**VARIANT**。 中的資料**VARIANT**s 可儲存許多格式。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
