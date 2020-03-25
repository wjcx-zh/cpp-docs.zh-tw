---
title: 異動 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 49fc0e244dd4f63bd7a69d963ff2a9fbc00ddb6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212598"
---
# <a name="transaction-odbc"></a>異動 (ODBC)

本主題適用於 MFC ODBC 類別。

交易是將一系列的更新分組或批次至[資料來源](../../data/odbc/data-source-odbc.md)的方式，如此一來，就會一次認可全部，或在您回復交易時不認可任何內容。 如果您不使用交易，對資料來源所做的變更會自動認可，而不是視需要進行認可。

> [!NOTE]
>  並非所有的 ODBC 資料庫驅動程式都支援交易。 呼叫[CDatabase](../../mfc/reference/cdatabase-class.md)或[CRecordset](../../mfc/reference/crecordset-class.md)物件的 `CanTransact` 成員函式，判斷您的驅動程式是否支援給定資料庫的交易。 請注意，`CanTransact` 不會告訴您資料來源是否提供完整的交易支援。 您也必須呼叫 `CDatabase::GetCursorCommitBehavior`，然後在 `CommitTrans` 和 `Rollback` 之後，`CDatabase::GetCursorRollbackBehavior` 檢查交易對開啟的 `CRecordset` 物件的影響。

呼叫 `Update`時，對 `CRecordset` 物件的 `AddNew` 和 `Edit` 成員函式的呼叫會立即影響資料來源。 `Delete` 呼叫也會立即生效。 相反地，您可以使用包含多個 `AddNew`、`Edit`、`Update`和 `Delete`呼叫的交易，這些作業會執行但不會認可，直到您明確呼叫 `CommitTrans` 為止。 藉由建立交易，您可以執行一系列這類呼叫，同時保留回復的能力。 如果重要的資源無法使用，或某個其他條件導致整個交易無法完成，您可以回復交易，而不是認可它。 在此情況下，任何屬於交易的變更都不會影響資料來源。

> [!NOTE]
>  目前，如果您已執行大量資料列提取，類別 `CRecordset` 不支援對資料來源的更新。 這表示您無法對 `AddNew`、`Edit`、`Delete`或 `Update`進行呼叫。 不過，您可以撰寫自己的函式來執行更新，然後在指定的交易內呼叫這些函式。 如需大量資料列提取的詳細資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!NOTE]
>  除了影響記錄集之外，交易也會影響您直接執行的 SQL 語句，只要您使用與 `CDatabase` 物件相關聯的 ODBC **HDBC** ，或是根據該**HDBC**的 odbc **HSTMT** 。

當您有多個必須同時更新的記錄時，交易特別有用。 在此情況下，您會想要避免一半完成的交易，例如，如果在上次更新之前擲回例外狀況，就可能會發生這種情況。 將這類更新分組到交易中，可讓您從變更中復原（回復），並將記錄傳回至 pretransaction 狀態。 例如，如果銀行將 money 從帳戶 A 轉移至帳戶 B，則提款從 A 到 B 的存款都必須成功地處理資金，否則整個交易必須失敗。

在資料庫類別中，您可以透過 `CDatabase` 物件來執行交易。 `CDatabase` 物件代表資料來源的連接，以及與該 `CDatabase` 物件相關聯的一或多個記錄集，會透過記錄集成員函式在資料庫的資料表上運作。

> [!NOTE]
>  僅支援一個層級的交易。 您不能將交易和交易延伸到多個資料庫物件。

下列主題提供有關如何執行交易的詳細資訊：

- [異動：在一個資料錄集內執行異動 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [異動：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
