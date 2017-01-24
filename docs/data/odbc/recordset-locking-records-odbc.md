---
title: "資料錄集：鎖定資料錄 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料 [C++], 鎖定"
  - "鎖定 [C++], 資料錄集"
  - "ODBC 資料錄集 [C++], 鎖定資料錄"
  - "開放式鎖定"
  - "開放式鎖定, ODBC"
  - "ODBC 中的封閉式鎖定"
  - "資料錄集 [C++], 鎖定資料錄"
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：鎖定資料錄 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明：  
  
-   [可用的鎖定資料錄類型](#_core_record.2d.locking_modes)  
  
-   [如何在更新時鎖定資料錄集的資料錄](#_core_locking_records_in_your_recordset)  
  
 當您使用資料錄集來更新資料來源上的資料錄時，您的應用程式可鎖定資料錄，因此沒有其他使用者可以在同時間內更新該資料錄。  除非系統能保證兩個使用者不能同時更新一筆資料錄，否則並未定義兩個使用者同時更新的資料錄狀態。  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  若您已經實作大量資料列擷取，某些資訊便不適用。  例如，您不能呼叫 **Edit** 和 **Update** 成員函式。  如需關於大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_record.2d.locking_modes"></a> 資料錄鎖定模式  
 資料庫類別提供兩種[資料錄鎖定模式](../Topic/CRecordset::SetLockingMode.md)：  
  
-   開放式鎖定 \(預設\)  
  
-   封閉式鎖定  
  
 更新資料錄的三個步驟：  
  
1.  呼叫 [Edit](../Topic/CRecordset::Edit.md) 成員函式，開始進行作業。  
  
2.  變更目前資料錄的適當欄位。  
  
3.  結束作業，並正常地認可此更新 \(藉由呼叫 [Update](../Topic/CRecordset::Update.md) 成員函式\)。  
  
 開放式鎖定只會在呼叫 **Update** 時才鎖定資料來源上的資料錄。  若您在一個多使用者環境中使用開放式鎖定，應用程式應該可以處理 **Update** 的失敗狀況。  封閉式鎖定 \(Pessimistic Locking\) 會在呼叫 **Edit** 時立即鎖定資料錄，要等到呼叫 **Update** \(失敗是透過 `CDBException` 機制指定，而不是透過 **Update** 傳回的 **FALSE** 值\) 後才釋放資料錄。  封閉式鎖定對於其他使用者具有潛在性的效能負面影響，因為相同資料錄的同步存取可能須等到您的應用程式 **Update** 處理程序完成後才能進行。  
  
##  <a name="_core_locking_records_in_your_recordset"></a> 鎖定您的資料錄集中的資料錄  
 如果想要變更資料錄集物件預設的[鎖定模式](#_core_record.2d.locking_modes)，就必須在呼叫 **Edit** 之前先變更模式。  
  
#### 若要變更您的資料錄集目前的鎖定模式  
  
1.  呼叫 [SetLockingMode](../Topic/CRecordset::SetLockingMode.md) 成員函式，指定 **CRecordset::pessimistic** 或 **CRecordset::optimistic**。  
  
 新的鎖定模式會持續生效，直到您再次為其變更或是關閉資料錄集。  
  
> [!NOTE]
>  目前只有少數 ODBC 驅動程式支援封閉式鎖定。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：執行聯結 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [資料錄集：加入、更新和刪除資料錄 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)