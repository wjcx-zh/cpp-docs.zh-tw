---
title: DAO 類別
ms.date: 09/17/2019
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: cdd3fd9a733df73d36441693d049724878219df5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303399"
---
# <a name="dao-classes"></a>DAO 類別

DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。

這些類別會與其他應用程式架構類別搭配使用，讓資料存取物件（DAO）資料庫的存取變得更容易，而這會使用與 Microsoft Visual Basic 和 Microsoft Access 相同的資料庫引擎。 DAO 類別也可以存取各種資料庫，讓開放式資料庫連接（ODBC）驅動程式可供使用。

使用 DAO 資料庫的程式至少會有一個 `CDaoDatabase` 物件和一個 `CDaoRecordset` 物件。

> [!NOTE]
>  視覺C++環境和嚮導不再支援 dao （雖然包含 dao 類別，但您仍然可以使用它們）。 Microsoft 建議您將 ODBC 用於新的 MFC 專案。 您應該只在維護現有的應用程式時使用 DAO。

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
從登入到登出來管理已命名、受密碼保護的資料庫會話。 大部分的程式都會使用預設工作區。

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
可供您用來運算元據的資料庫連接。

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
表示選取自資料來源的資料錄集。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
在控制項中顯示資料庫記錄的檢視。

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
代表查詢定義，通常會儲存在資料庫中。

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
表示儲存的基底資料表或附加資料表定義。

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
表示從 DAO 類別所產生的例外狀況條件。

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。 您通常不會直接使用這個類別。

## <a name="related-classes"></a>相關類別

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
封裝二進位大型物件（BLOB）（例如點陣圖）之儲存體的控制碼。 `CLongBinary` 物件是用來管理儲存在資料庫資料表中的大型資料物件。

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
OLE automation 型別**貨幣**的包裝函式、固定點算術型別，小數點前15位數和後4位數。

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
OLE automation 類型**DATE**的包裝函式。 表示日期和時間值。

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
OLE automation 類型**VARIANT**的包裝函式。 **VARIANT**s 中的資料可以用許多格式儲存。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
