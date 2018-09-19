---
title: 異動 (ODBC) |Microsoft Docs
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
ms.openlocfilehash: f142b4602ad1a9605987bc71e477e977902dccac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090265"
---
# <a name="transaction-odbc"></a>異動 (ODBC)

本主題適用於 MFC ODBC 類別。  
  
交易是群組，或批次，一系列的更新方式[資料來源](../../data/odbc/data-source-odbc.md)，讓所有都是一次認可或回復交易時不認可任何。 如果您未使用交易，對資料來源的變更會自動而不是隨選上認可的認可。  
  
> [!NOTE]
>  並非所有的 ODBC 資料庫驅動程式支援交易。 呼叫`CanTransact`成員函式您[CDatabase](../../mfc/reference/cdatabase-class.md)或是[CRecordset](../../mfc/reference/crecordset-class.md)物件，以判斷您的驅動程式是否支援給定的資料庫交易。 請注意，`CanTransact`不會告訴您資料來源是否提供完整的交易支援。 您還必須呼叫`CDatabase::GetCursorCommitBehavior`並`CDatabase::GetCursorRollbackBehavior`之後`CommitTrans`並`Rollback`檢查開啟的交易影響`CRecordset`物件。  
  
呼叫`AddNew`並`Edit`成員函式`CRecordset`物件的資料來源，當您呼叫立即的影響`Update`。 `Delete` 呼叫也會立即生效。 相反地，您可以使用多個呼叫所組成的交易`AddNew`， `Edit`， `Update`，以及`Delete`，這會執行，但尚未認可，直到您呼叫`CommitTrans`明確。 藉由建立交易，您可以執行一系列的這類呼叫，同時保留其復原的能力。 如果重要的資源無法使用，或某些其他條件會阻止完成整個交易，您可以回復而不是認可交易。 在此情況下，屬於交易的變更都不會影響資料來源。  
  
> [!NOTE]
>  目前，類別`CRecordset`不支援更新資料來源，如果您已實作大量資料列擷取。 這表示您不能呼叫`AddNew`， `Edit`， `Delete`，或`Update`。 不過，您可以撰寫自己的函式來執行更新，然後呼叫這些函式中指定的交易。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  除了會影響您的資料錄集，異動會影響 SQL 陳述式直接執行，只要您使用 ODBC **HDBC**聯您`CDatabase`物件或 ODBC **HSTMT**根據可**HDBC**。  
  
當您有必須同時更新多筆記錄時，交易將會特別有用。 在此情況下，您會想要避免半完成的交易，例如，如果在進行最後的更新之前擲回例外狀況可能會發生。 將這類更新分組到某交易可讓復原 （復原） 所做的變更，並回到交易前的狀態傳回的記錄。 比方說，如果銀行轉帳從帳戶 A 到 B 帳戶，同時並 deposit B 提款必須成功，才能正確處理款項或整個交易必須失敗。  
  
資料庫類別中，在您執行的是透過交易`CDatabase`物件。 A`CDatabase`物件都代表資料來源連接，並與它相關的一或多個資料錄集`CDatabase`物件操作資料錄集成員函式透過資料庫的資料表。  
  
> [!NOTE]
>  只有一個層級的交易支援。 您無法巢狀交易或交易可以跨越多個資料庫物件。  
  
下列主題提供如何執行交易的詳細資訊：  
  
- [異動：在一個資料錄集內執行異動 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
- [異動：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>另請參閱  

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)