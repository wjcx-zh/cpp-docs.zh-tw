---
title: DAO 類別
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 7ae85cbeb7790cadb8c26dfbdb7a5163dbcd47c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373509"
---
# <a name="dao-classes"></a>DAO 類別

DAO 與 Access 資料庫一起使用,並通過 Office 2013 支援。 DAO 3.6 是最終版本,它被視為過時版本。

這些類與其他應用程式框架類配合使用,以便輕鬆存取資料存取物件 (DAO) 資料庫,這些資料庫使用與 Microsoft Visual Basic 和 Microsoft Access 相同的資料庫引擎。 DAO 類別還可以存取開放資料庫連線 (ODBC) 驅動程式可用的各種資料庫。

使用 DAO 資料庫的程式將至少`CDaoDatabase`具有一`CDaoRecordset`個物件和一個物件。

> [!NOTE]
> 視覺化C++環境和精靈不再支援DAO(儘管包含DAO類,您仍可以使用它們)。 Microsoft 建議您將 ODBC 用於新的 MFC 專案。 您只應在維護現有應用程式時使用 DAO。

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
從登錄到註銷管理受密碼保護的命名資料庫會話。 大多數程式使用預設工作區。

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
到資料庫的連接,通過該資料庫可以對數據進行操作。

[CDao 記錄集](../mfc/reference/cdaorecordset-class.md)<br/>
表示選取自資料來源的資料錄集。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
在控制項中顯示資料庫記錄的檢視。

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
表示查詢定義,通常保存在資料庫中。

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
表示儲存的基底資料表或附加資料表定義。

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
表示 DAO 類產生的異常條件。

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。 您通常不會直接使用此類。

## <a name="related-classes"></a>相關類

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封裝二進位大型物件 (BLOB) 的儲存句柄,如點陣圖。 `CLongBinary`對象用於管理存儲在資料庫表中的大型數據物件。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE 自動化類型**貨幣**的包裝器,一種定點算術類型,在小數點之前有 15 位元數位,後為 4 位。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE 自動化型**態 DATE**的包裝器 。 表示日期和時間值。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE 自動化型**態 VARIANT**的包裝器 。 **VARIANT**中的數據可以以多種格式存儲。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)
