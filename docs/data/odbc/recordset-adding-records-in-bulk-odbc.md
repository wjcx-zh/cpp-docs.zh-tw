---
title: "資料錄集： 加入大量 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 251d2fa4b7c28c1458fdc5643c9b17c53ba1b0ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>資料錄集：加入大量資料錄 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 MFC [CRecordset](../../mfc/reference/crecordset-class.md)類別具有的全新最佳化功能，當您新增新記錄大量資料表，因此可以提升效率。  
  
> [!NOTE]
>  本主題適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 這個新選項**dwOptions**參數[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)成員函式， **optimizeBulkAdd**，可改善效能，當您新增多筆記錄連續而不需呼叫**Requery**或**關閉**。 只會在第一個已變更的欄位**更新**呼叫都標示為中途的後續`AddNew` /**更新**呼叫。  
  
 如果您使用資料庫類別若要善用**:: SQLSetPos** ODBC API 函式加入、 編輯和刪除資料錄，此最佳化是不必要的。  
  
 如果載入 ODBC 資料指標程式庫或 ODBC 驅動程式不支援新增、 編輯和刪除透過**:: SQLSetPos**，此最佳化改善大量增加效能。 若要開啟此最佳化，將**dwOptions**中的參數**開啟**呼叫下資料錄集：  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 加入、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)