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
ms.openlocfilehash: 56629f8c5ff74aff4e0df589cda1e7b988fb5fd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376419"
---
# <a name="transaction-odbc"></a>異動 (ODBC)

本主題適用於 MFC ODBC 類別。

事務是一種對[數據源](../../data/odbc/data-source-odbc.md)的一系列更新進行分組或批處理的方法,以便在回滾事務時一次提交所有更新,或者不提交任何更新。 如果不使用事務,則會自動提交對數據源的更改,而不是按需提交。

> [!NOTE]
> 並非所有 ODBC 資料庫驅動程式都支援事務。 調用`CanTransact`[CDatabase](../../mfc/reference/cdatabase-class.md)或[CRecordset](../../mfc/reference/crecordset-class.md)物件的成員函數,以確定驅動程式是否支援給定資料庫的事務。 請注意,`CanTransact`不會告訴您資料來源是否提供完整的事務支援。 您還必須`CDatabase::GetCursorCommitBehavior`調用`CDatabase::GetCursorRollbackBehavior``CommitTrans``Rollback`和 後 ,並`CRecordset`檢查事務對打開 對象的影響。

調用`CRecordset`物件`AddNew``Edit`的 和成員函數在`Update`調用 時會立即影響數據源。 `Delete`呼叫也會立即生效。 相反`AddNew`,可以使用由對`Edit``Update``Delete`、 和 的多個調用組成的事務,這些調用在`CommitTrans`顯式調用 之前執行但不提交。 通過建立事務,您可以執行一系列此類調用,同時保持回滾這些調用的能力。 如果關鍵資源不可用或某些其他條件阻止完成整個事務,則可以回滾事務,而不是提交該事務。 在這種情況下,屬於事務的更改都不會影響數據源。

> [!NOTE]
> 目前,如果`CRecordset`已實現批量行提取,類不支援對數據源的更新。 `AddNew`這意味著您不能對`Edit`、`Delete``Update`或進行調用。 但是,您可以編寫自己的函數來執行更新,然後在給定事務中調用這些函數。 有關批量行提取的詳細資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

> [!NOTE]
> 除了`CDatabase`影響記錄集之外,事務會影響您直接執行的 SQL 語句,只要您使用與物件關聯的 ODBC **HDBC**或基於該**HDBC**的 ODBC **HSTMT。**

當您有多個必須同時更新的記錄時,事務特別有用。 在這種情況下,您希望避免半已完成的事務,例如,如果在上次更新之前引發異常,則可能發生異常。 將此類更新分組到事務中允許從更改中恢復(回滾)並將記錄返回到事務前狀態。 例如,如果銀行將資金從帳戶 A 轉移到帳戶 B,則從 A 取款和存款到 B 都必須成功正確處理資金,否則整個交易必須失敗。

在資料庫類中,通過`CDatabase`物件執行事務。 物件`CDatabase`表示與數據源的連接,與`CDatabase`該 物件關聯的一個或多個記錄集通過記錄集成員函數對資料庫的表進行操作。

> [!NOTE]
> 僅支援一個級別的事務。 不能嵌套事務,也不能跨多個資料庫物件。

以下主題提供有關如何執行事務的詳細資訊:

- [異動：在一個資料錄集內執行異動 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [異動：異動如何影響更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>另請參閱

[開放資料庫連線 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
