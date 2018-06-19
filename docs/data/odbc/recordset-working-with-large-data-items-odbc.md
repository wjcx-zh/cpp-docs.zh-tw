---
title: 資料錄集： 使用大型的資料項目 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6845d2e3c1b1eac31486200a0f610037d4774626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091731"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>資料錄集：使用大型的資料項目 (ODBC)
本主題適用於 MFC ODBC 類別和 MFC DAO 類別。  
  
> [!NOTE]
>  如果您使用 MFC DAO 類別時，管理大型資料項目與類別[CByteArray](../../mfc/reference/cbytearray-class.md)而不是類別[CLongBinary](../../mfc/reference/clongbinary-class.md)。 如果您使用 MFC ODBC 類別具有大量資料列擷取，使用`CLongBinary`而不是`CByteArray`。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 假設您的資料庫可以儲存大量資料，例如點陣圖 （員工照片、 地圖、 圖片的產品，OLE 物件，以及等等）。 這類資料通常稱為二進位大型物件 （或 BLOB） 因為：  
  
-   每個欄位的值很大。  
  
-   不同於數字和其他簡單資料類型，它有無法預期大小。  
  
-   資料是程式的從您的觀點來看不規則的。  
  
 本主題說明使用這類物件的資料庫類別提供的支援。  
  
##  <a name="_core_managing_large_objects"></a> 管理大型物件  
 資料錄集有兩種方式可解決管理二進位大型物件的特殊困難。 您可以使用類別[CByteArray](../../mfc/reference/cbytearray-class.md)或您可以使用類別[CLongBinary](../../mfc/reference/clongbinary-class.md)。 一般情況下，`CByteArray`是管理大型二進位資料的慣用的方法。  
  
 `CByteArray` 需要更多成本負擔比`CLongBinary`更適用中, 所述但[CByteArray 類別](#_core_the_cbytearray_class)。 `CLongBinary` 在簡短描述[CLongBinary 類別](#_core_the_clongbinary_class)。  
  
 如需使用`CByteArray`來處理大型資料的項目，請參閱[技術附註 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_cbytearray_class"></a> CByteArray 類別  
 `CByteArray` 是其中一個 MFC 集合類別。 A`CByteArray`物件會儲存為動態的位元組陣列，視所能成長的陣列。 類別會提供快速存取，藉由索引與內建 c + + 陣列。 `CByteArray` 物件可以序列化和傾印用於診斷目的。 類別提供成員函式取得和設定指定的位元組、 插入和附加位元組，以及移除一個位元組或所有位元組。 這些功能進行剖析更容易的二進位資料。 比方說，如果二進位物件是 OLE 物件，您可能必須以存取實際物件的某些標頭位元組檢閱。  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a> 使用 CByteArray 中資料錄集  
 類型，提供您的資料錄集的欄位資料成員`CByteArray`，提供固定的基底從中[RFX](../../data/odbc/record-field-exchange-rfx.md)可以管理的傳輸，這類物件的資料錄集之間的資料來源，並透過您可以操作物件內的資料。 RFX 擷取資料，需要特定的站台，您需要存取基礎資料的方法。  
  
 如需使用`CByteArray`來處理大型資料的項目，請參閱[技術附註 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_clongbinary_class"></a> CLongBinary 類別  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md)物件是簡單的殼層周圍`HGLOBAL`控制代碼儲存在堆積上配置的區塊。 當它將繫結包含二進位大型物件的資料表資料行時，RFX 會配置`HGLOBAL`時它需要將資料傳送至資料錄集，並將控制代碼，以處理`CLongBinary`資料錄集的欄位。  
  
 接著，您使用`HGLOBAL`處理， `m_hData`，以使用與資料本身，像任何處理資料，在其上運作。 這是 where [CByteArray](../../mfc/reference/cbytearray-class.md)新增功能。  
  
> [!CAUTION]
>  CLongBinary 物件不能做為函式呼叫中的參數。 此外，他們的實作，其會呼叫 **:: SQLGetData**、 一定是可捲動的快照集的捲動效能會變慢。 這可能也會為 true 時使用 **:: SQLGetData**自行擷取動態結構描述資料行呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 取得 Sum 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)