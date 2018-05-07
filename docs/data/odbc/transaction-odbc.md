---
title: 異動 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3acd47746d3a920b679fb5509c34e5978ad43eed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-odbc"></a>異動 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 交易是群組，或批次，一系列的更新方式[資料來源](../../data/odbc/data-source-odbc.md)，讓所有已認可一次，或如果您回復交易，不會認可。 如果您未使用交易，就無法認可自動而不是認可視資料來源的變更。  
  
> [!NOTE]
>  並非所有 ODBC 資料庫驅動程式都支援交易。 呼叫`CanTransact`成員函式的程式[CDatabase](../../mfc/reference/cdatabase-class.md)或[CRecordset](../../mfc/reference/crecordset-class.md)物件來判斷您的驅動程式是否支援給定的資料庫交易。 請注意，`CanTransact`不會告訴您是否由資料來源提供完整的交易支援。 您也必須呼叫`CDatabase::GetCursorCommitBehavior`和`CDatabase::GetCursorRollbackBehavior`之後**CommitTrans**和**復原**來檢查交易的效果，在開啟`CRecordset`物件。  
  
 呼叫`AddNew`和**編輯**的成員函式`CRecordset`物件的影響的資料來源，當您呼叫立即**更新**。 **刪除**呼叫也會立即生效。 相反地，您可以使用交易組成的多次呼叫`AddNew`，**編輯**，**更新**，和**刪除**，它會執行，但未認可之前您呼叫**CommitTrans**明確。 藉由建立交易，您可以執行一系列的這類呼叫，同時保留其復原的能力。 如果重要的資源無法使用，或某個其他狀況會防止標記為已完成整個交易，您可以回復而不是認可交易。 在此情況下，屬於交易的變更都不會影響資料來源。  
  
> [!NOTE]
>  目前類別`CRecordset`不支援更新資料來源，如果您已實作大量資料列擷取。 這表示您不能呼叫`AddNew`，**編輯**，**刪除**，或**更新**。 不過，您可以撰寫自己的函式來執行更新，然後呼叫這些函式中指定的交易。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  除了影響您的資料錄集，異動會影響 SQL 陳述式，只要您使用 ODBC 直接執行**HDBC**聯您`CDatabase`物件或 ODBC **HSTMT**根據**HDBC**。  
  
 當您有必須同時更新多筆記錄時，交易是特別有用。 在此情況下，您會想要避免半完成交易，例如，如果最後的更新之前，所擲回例外狀況可能會發生。 將這類更新分組到某交易內可以回復 （復原） 所做的變更，並傳回回到交易前的狀態記錄。 例如，如果銀行轉帳從帳戶 A 到 B 帳戶，同時提款從以及存錢至 B 必須成功，才能正確處理款項或整筆交易就算失敗。  
  
 資料庫類別中，在您執行的是透過交易`CDatabase`物件。 A`CDatabase`物件都代表資料來源連接，以及一或多個資料錄集相關聯的`CDatabase`操作資料錄集成員函式透過資料庫的資料表上的物件。  
  
> [!NOTE]
>  只有一個層級的交易支援。 您無法巢狀交易也不在交易可以跨越多個資料庫物件。  
  
 下列主題提供如何執行交易的詳細資訊：  
  
-   [異動：在一個資料錄集內執行異動 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [異動：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>另請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)