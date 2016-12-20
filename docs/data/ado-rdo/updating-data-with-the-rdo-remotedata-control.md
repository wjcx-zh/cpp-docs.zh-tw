---
title: "以 RDO RemoteData 控制項來更新資料 | Microsoft Docs"
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
  - "RDO RemoteData 控制項"
  - "RDO RemoteData 控制項, 更新資料"
  - "RemoteData 控制項"
  - "RemoteData 控制項, 更新資料"
ms.assetid: abb4175f-612e-4645-905e-c0fa918b0fd7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 以 RDO RemoteData 控制項來更新資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

RDO RemoteData 控制項資料可為唯讀或可修改。  
  
### 若要建立使用 RDO RemoteData 控制項來修改資料的應用程式  
  
1.  設定 RDO RemoteData 控制項的 **CursorDriver** 屬性。  
  
    -   伺服端指標會將傳回的資料儲存於伺服器。  
  
    -   ODBC 用戶端指標會將資料儲存於用戶端的區域儲存區。  
  
    -   用戶端批次指標會使用專為處理並行工作而設計的指標程式庫 \(Cursor Library\)。  
  
    -   在執行動作查詢 \(Action Query\) 時，將採用 No Cursor 選項，因此不需要任何指標。  
  
2.  設定 RDO RemoteData 控制項的 **LockType** 屬性。  建議採用以結果集 \(Resultset\) 選項為架構的開放式並行存取。  
  
    -   如果想要修改資料，就不應該使用唯讀的並行。  
  
    -   封閉式並行存取 \(Pessimistic Concurrency\) 會在更新時鎖定資料，防止其他使用者執行不相容資料變更的危險。  
  
    -   開放式並行存取不會鎖定資料，不過若它在認可過程中，偵測到另一個用戶已張貼不相容的狀態，RDO RemoteData 控制項將擲回一個錯誤。  
  
3.  設定 RDO RemoteData 控制項的 **ResultsetType** 屬性。  請確認 ODBC 驅動程式支援選取的選項：  
  
    -   如果選擇了 Create Static Cursor 選項，除非該指標關閉並重新開啟，才會偵測到此變更。  
  
    -   如果選擇了 Create Keyset Cursor 選項，您可隨意地在索引鍵集 \(Keyset\) 指標本身內插入、更新和刪除指標。  
  
4.  視需要設定資料繫結控制項，以允許可更新性。  請注意，某些控制項並不允許更新。  
  
 如需如何使用這些物件的詳細資訊，請參閱 RDO RemoteData 控制項的相關文件。  
  
## 請參閱  
 [RDO 資料繫結](../../data/ado-rdo/rdo-databinding.md)   
 [在 Visual C\+\+ 中使用 RDO 資料繫結](../../data/ado-rdo/using-rdo-databinding-in-visual-cpp.md)