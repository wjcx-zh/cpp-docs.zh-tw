---
title: "資料錄集： 鎖定資料錄 (ODBC) |Microsoft 文件"
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
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76d7ab2df01e485ffff70120609227b9fbae6ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-locking-records-odbc"></a>資料錄集：鎖定資料錄 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明：  
  
-   [何種記錄鎖定可用](#_core_record.2d.locking_modes)。  
  
-   [如何鎖定資料錄集中的記錄，在更新期間](#_core_locking_records_in_your_recordset)。  
  
 當您使用資料錄集更新資料來源上的記錄時，您的應用程式可以鎖定記錄，所以沒有其他使用者可以同時更新記錄。 兩個使用者同時更新一筆記錄的狀態是未定義，除非系統可確保兩位使用者不能同時更新資料錄。  
  
> [!NOTE]
>  本主題適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果您已實作大量資料列擷取，資訊的某些部分不適用。 例如，您不能呼叫**編輯**和**更新**成員函式。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_record.2d.locking_modes"></a>記錄鎖定模式  
 資料庫類別提供兩個[記錄鎖定模式](../../mfc/reference/crecordset-class.md#setlockingmode):  
  
-   開放式鎖定 （預設值）  
  
-   封閉式鎖定  
  
 更新一筆記錄，就會發生在三個步驟：  
  
1.  您開始作業，藉由呼叫[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式。  
  
2.  您變更目前的記錄的適當欄位。  
  
3.  結束作業，並正常地認可更新 — 藉由呼叫[更新](../../mfc/reference/crecordset-class.md#update)成員函式。  
  
 開放式鎖定鎖定只有在資料來源上的資料錄**更新**呼叫。 如果您使用開放式鎖定在多使用者環境時，應用程式應該要處理**更新**失敗狀況。 封閉式鎖定鎖定資料錄，只要您呼叫**編輯**並不會釋放它直到您呼叫**更新**(失敗表示透過`CDBException`機制，不是由值為**FALSE**傳回**更新**)。 封閉式鎖定有潛在的效能降低，其他使用者的影響，因為並行存取相同的記錄可能要等到完成您的應用程式的**更新**程序。  
  
##  <a name="_core_locking_records_in_your_recordset"></a>鎖定資料錄集中的記錄  
 如果您想要變更資料錄集物件的[鎖定模式](#_core_record.2d.locking_modes)預設值，您必須變更模式才能呼叫**編輯**。  
  
#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>若要變更目前的鎖定模式，以您的資料錄集  
  
1.  呼叫[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成員函式，指定**CRecordset::pessimistic**或**CRecordset::optimistic**。  
  
 新的鎖定模式會持續有效，直到您再次變更或關閉資料錄集。  
  
> [!NOTE]
>  目前相對較少的 ODBC 驅動程式支援封閉式鎖定。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)