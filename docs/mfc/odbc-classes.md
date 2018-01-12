---
title: "ODBC 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.data
dev_langs: C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33fcc3453d36a2567330f60cec73383f842210c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-classes"></a>ODBC 類別
這些類別會搭配其他應用程式架構類別以便讓您輕鬆存取各種不同的資料庫的開放式資料庫連接 (ODBC) 驅動程式可用。  
  
 使用 ODBC 資料庫的程式必須至少有`CDatabase`物件和`CRecordset`物件。  
  
 [CDatabase](../mfc/reference/cdatabase-class.md)  
 封裝資料來源，透過它您可以操作的資料來源的連接。  
  
 [CRecordset](../mfc/reference/crecordset-class.md)  
 封裝一組選取自資料來源的記錄。 資料錄集啟用捲動記錄記錄、 更新資料錄 （新增、 編輯和刪除資料錄）、 利用篩選條件，限定選取項目排序選取範圍，並取得參數化資訊的選取項目，或在執行階段計算。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供表單直接連接至資料錄集物件的檢視。 對話方塊資料交換 (DDX) 機制交換資料，資料錄集之間的資料錄檢視控制項。 像所有表單檢視中，資料錄檢視根據對話方塊範本資源。 資料錄檢視也支援在記錄間移動資料錄集中、 更新的記錄，並關閉相關聯的資料錄集資料錄檢視關閉時。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 所產生的資料存取的失敗處理例外狀況。 這個類別會有相同的用途，做為其他例外狀況類別，例外狀況處理機制的類別庫中。  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 提供支援資料錄欄位交換 (RFX)，欄位資料成員和參數的資料錄集物件和資料來源上的對應資料表資料行的資料成員之間交換資料的內容資訊。 相當於類別[CDataExchange](../mfc/reference/cdataexchange-class.md)，用類似的對話方塊資料交換 (DDX)。  
  
## <a name="related-classes"></a>相關的類別  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 封裝的控制代碼到儲存體二進位大型物件 (BLOB)，例如點陣圖。 `CLongBinary`物件可用來管理儲存在資料庫資料表的大型資料物件。  
  
 [CDBVariant](../mfc/reference/cdbvariant-class.md)  
 可讓您儲存的值，而不需擔心值的資料類型。 `CDBVariant`會追蹤目前的值等位中儲存的資料類型。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

