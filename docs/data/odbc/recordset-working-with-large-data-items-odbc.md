---
title: 資料錄集： 使用大型的資料項目 (ODBC) |Microsoft Docs
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
ms.openlocfilehash: d52e9623cb47576d0804dbae364eee2e3563574b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077219"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>資料錄集：使用大型的資料項目 (ODBC)

本主題適用於 MFC ODBC 類別和 MFC DAO 類別。  
  
> [!NOTE]
>  如果您使用 MFC DAO 類別時，管理您的大型資料項目，與類別[CByteArray](../../mfc/reference/cbytearray-class.md)而不是類別[CLongBinary](../../mfc/reference/clongbinary-class.md)。 如果您使用 MFC ODBC 類別具有大量資料列擷取，使用`CLongBinary`而非`CByteArray`。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
假設您的資料庫可以儲存大量的資料，例如點陣圖 （員工照片、 對應、 圖片的產品、 OLE 物件等）。 這類資料通常稱為二進位大型物件 （或 BLOB） 因為：  
  
- 每個欄位值很大。  
  
- 不同於數字和其他簡單資料型別，它有沒有可預測的大小。  
  
- 資料是程式的從您的觀點來看不規則的。  
  
本主題說明的支援的資料庫類別提供用於處理這類物件。  
  
##  <a name="_core_managing_large_objects"></a> 管理大型物件  

資料錄集有兩種方式可解決特殊的困難度管理二進位大型物件。 您可以使用類別[CByteArray](../../mfc/reference/cbytearray-class.md)或您可以使用類別[CLongBinary](../../mfc/reference/clongbinary-class.md)。 一般情況下，`CByteArray`是慣用的方式來管理大型二進位資料。  
  
`CByteArray` 需要更多的額外負荷比`CLongBinary`但更有能力，如中所述[CByteArray 類別](#_core_the_cbytearray_class)。 `CLongBinary` 簡短中所述[CLongBinary 類別](#_core_the_clongbinary_class)。  
  
如需使用詳細資訊`CByteArray`若要使用大型的資料項目，請參閱[技術附註 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_cbytearray_class"></a> CByteArray 類別  

`CByteArray` 是其中一個 MFC 集合類別。 A`CByteArray`物件會儲存為動態的位元組陣列，視所能成長的陣列。 類別會提供快速存取，藉由索引使用與內建的 c + + 陣列。 `CByteArray` 物件可以序列化和傾印供診斷之用。 類別提供成員函式取得和設定指定的位元組、 插入和附加位元組，以及移除一個位元組或所有位元組。 這些功能讓剖析更容易的二進位資料。 比方說，如果二進位物件是一個 OLE 物件，您可能要逐步執行一些標頭位元組，連線到實際的物件。  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a> 資料錄集中使用 CByteArray  

藉由提供您的資料錄集的欄位資料成員的型別`CByteArray`，提供固定的基底，從中[RFX](../../data/odbc/record-field-exchange-rfx.md)可以管理的傳輸，這類物件的資料錄集和資料來源之間，以及透過您可以操作物件內的資料。 RFX 擷取的資料，需要特定的站台，您需要存取基礎資料的方法。  
  
如需使用詳細資訊`CByteArray`若要使用大型的資料項目，請參閱[技術附註 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)。  
  
##  <a name="_core_the_clongbinary_class"></a> CLongBinary 類別  

A [CLongBinary](../../mfc/reference/clongbinary-class.md)物件是簡單的殼層周圍`HGLOBAL`控制代碼，以在堆積上配置的儲存體的區塊。 繫結包含二進位大型物件的資料表資料行時，會配置 RFX`HGLOBAL`時，它必須將資料傳送到資料錄集，並將控制代碼，以處理`CLongBinary`資料錄集欄位。  
  
接著使用`HGLOBAL`處理， `m_hData`，來處理資料本身，像任何處理資料，在其上運作。 這正是[CByteArray](../../mfc/reference/cbytearray-class.md)新增功能。  
  
> [!CAUTION]
>  CLongBinary 物件不能做為函式呼叫中的參數。 此外，實作，它會呼叫`::SQLGetData`，一定是可捲動的快照集的捲動效能會變慢。 這也可能是，則為 true 時使用`::SQLGetData`呼叫自己，以擷取動態結構描述資料行。  
  
## <a name="see-also"></a>另請參閱  

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：取得 SUM 和其他彙總結果 (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)