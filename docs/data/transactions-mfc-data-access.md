---
title: "交易 (MFC 資料存取) | Microsoft Docs"
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
  - "資料庫 [C++], 異動"
  - "異動 [C++]"
  - "異動 [C++], 支援"
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 交易 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交易的概念是特別開發來處理一些情況，其中資料庫的結果狀態取決於一系列的作業是否全部成功。  之所以如此，是因為後續的作業可能會修改之前作業的結果。  在這種情況下，如果任何一個作業失敗，產生的狀態可能會不確定。  
  
 若要解決這個問題，交易會將一系列的作業組成群組，以確保最後結果的完整性。  除非所有作業成功且受到認可 \(寫入至資料庫\)，否則整個交易會失敗。  取消交易就稱之為復原。  復原可以回復所做的變更，並會讓資料庫回到交易前的狀態。  
  
 例如，在自動化銀行交易中，如果您從帳戶 A 傳輸金錢到 B 帳戶，從 A 提款以及存錢至 B 必須同時成功，才能正確處理款項，否則整筆交易就算失敗。  
  
 交易必須有 ACID 屬性，其代表以下：  
  
-   **不可部分完成性 \(Atomicity\)**：交易是不可部分完成的工作單位，並只能執行一次；不論工作是否全都完成，或全都沒有完成。  
  
-   **一致性 \(Consistency\)**：交易會保留資料的一致性，將某個一致的資料狀態轉換成另一個一致的資料狀態。  由交易繫結的資料必會保留語意。  
  
-   **隔離 \(Isolation\)**：交易是隔離的單位，同時發生的交易中，每個都是個別且獨立發生。  交易絕不應該看見其他交易的中繼階段。  
  
-   **持續性 \(Durability\)**：交易是復原的單位。  如果交易成功，即使系統當機或被關閉，其更新都會被保存。  如果交易失敗，系統會停留在認可此交易之前的狀態。  
  
 您可以支援 OLE DB \(請參閱[支援 OLE DB 的交易](../data/oledb/supporting-transactions-in-ole-db.md)\) 或 ODBC \(請參閱[交易 \(ODBC\)](../data/odbc/transaction-odbc.md)\) 的交易。  
  
 分散式的交易是更新分散式資料的交易，也就是一個以上的網路電腦系統上的資料。  如果您想要透過分散式系統支援交易，您應該使用 Microsoft.NET Framework，而不是 OLE DB 交易支援。  
  
## 請參閱  
 [Data Access Programming \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)