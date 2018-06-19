---
title: DAO 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f43595ca5f688372a70999231ceebec5282cd3b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348917"
---
# <a name="dao-classes"></a>DAO 類別
這些類別會搭配其他應用程式架構類別讓您輕鬆存取資料存取物件 (DAO) 資料庫，使用相同的資料庫引擎與 Microsoft Visual Basic 和 Microsoft Access。 DAO 類別也可以存取各種不同的資料庫的開放式資料庫連接 (ODBC) 驅動程式可用。  
  
 使用 DAO 資料庫的程式必須至少有`CDaoDatabase`物件和`CDaoRecordset`物件。  
  
> [!NOTE]
>  Visual c + + 環境和精靈不會再支援 DAO，（雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 建議您針對新的 MFC 專案，使用 ODBC。 您只應該使用 DAO 中維護現有應用程式。  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 從登入到登出來管理受密碼保護的具名資料庫工作階段。 大部分程式會使用預設工作區。  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 透過此您可以在資料操作資料庫的連接。  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 表示選取自資料來源的資料錄集。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 在控制項中顯示資料庫記錄的檢視。  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 表示查詢定義，通常是已儲存於資料庫中。  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 表示儲存的基底資料表或附加資料表定義。  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 表示 DAO 類別所引發的例外狀況。  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。 您通常不會直接使用這個類別。  
  
## <a name="related-classes"></a>相關的類別  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 封裝的控制代碼到儲存體二進位大型物件 (BLOB)，例如點陣圖。 `CLongBinary` 物件可用來管理儲存在資料庫資料表的大型資料物件。  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 OLE automation 類型包裝函式**貨幣**，定點算術類型，則有小數點前面的 15 位數之後, 有 4 位數。  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 OLE automation 類型包裝函式**日期**。 表示日期和時間值。  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 OLE automation 類型包裝函式**VARIANT**。 中的資料**VARIANT**s 可以許多種格式儲存。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../mfc/class-library-overview.md)

