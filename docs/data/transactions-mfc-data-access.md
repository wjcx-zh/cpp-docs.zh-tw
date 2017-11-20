---
title: "交易 （MFC 資料存取） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 655c8e2cc900aa369055e5f1b9975e02c1a8ac88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="transactions--mfc-data-access"></a>交易 (MFC 資料存取)
異動的概念是特別開發來處理一些情況，其中資料庫的結果狀態取決於一系列的作業是否全部成功。 之所以如此，是因為後續的作業可能會修改之前作業的結果。 在這種情況下，如果任何一個作業失敗，產生的狀態可能會不確定。  
  
 若要解決這個問題，交易會將一系列的作業組成群組，以確保最後結果的完整性。 除非所有作業成功且受到認可 (寫入至資料庫)，否則整個交易會失敗。 取消交易就稱之為復原。 復原可以回復所做的變更，並會讓資料庫回到交易前的狀態。  
  
 例如，在自動化銀行交易中，如果您從帳戶 A 傳輸金錢到 B 帳戶，從 A 提款以及存錢至 B 必須同時成功，才能正確處理款項，否則整筆交易就算失敗。  
  
 異動必須有 ACID 屬性，其代表以下：  
  
-   **不可部分完成性**交易是不可部分完成的工作單位，並只能執行一次，所有工作都是或全都都是。  
  
-   **一致性**： 異動會保留資料，將一個一致的資料狀態轉換成另一個一致的資料狀態的一致性。 由異動繫結程序的資料必會保留語意。  
  
-   **隔離**交易是隔離的單位，每個個別且獨立發生並行交易。 異動絕不應該看見其他異動的中繼階段。  
  
-   **持久性**交易是復原的單位。 如果異動成功，即使系統當機或被關閉，其更新都會被保存。 如果交易失敗，系統會停留在認可此交易之前的狀態。  
  
 您可以在 OLE DB 支援交易 (請參閱[支援 OLE DB 中的交易](../data/oledb/supporting-transactions-in-ole-db.md)) 或 ODBC (請參閱[異動 (ODBC)](../data/odbc/transaction-odbc.md))。  
  
 分散式的異動是更新分散式資料的異動，也就是一個以上的網路電腦系統上的資料。 如果您想要透過分散式系統支援交易，您應該使用 ADO.NET，而不是 OLE DB 交易支援。  
  
## <a name="see-also"></a>另請參閱  
 [資料存取程式設計 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)