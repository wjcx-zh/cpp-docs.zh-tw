---
title: 資料錄集：鎖定資料錄 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: 1265899e7060527d7e586689eb4c3148eebc4080
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037285"
---
# <a name="recordset-locking-records-odbc"></a>資料錄集：鎖定資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明：

- [何種記錄鎖定可用](#_core_record.2d.locking_modes)。

- [如何鎖定資料錄集中的記錄，在更新期間](#_core_locking_records_in_your_recordset)。

當您使用資料錄集更新資料來源上的記錄時，您的應用程式可以鎖定記錄，因此沒有其他使用者可以同時更新記錄。 兩個使用者同時更新一筆記錄的狀態為未定義，除非系統可以保證兩位使用者無法同時更新一筆記錄。

> [!NOTE]
>  本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果您已實作大量資料列擷取，部分資訊不適用。 例如，您不能呼叫`Edit`和`Update`成員函式。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="_core_record.2d.locking_modes"></a> 記錄鎖定模式

資料庫類別提供兩個[記錄鎖定模式](../../mfc/reference/crecordset-class.md#setlockingmode):

- 開放式鎖定 （預設值）

- 封閉式鎖定

更新記錄，就會發生下列三個步驟：

1. 您開始作業，藉由呼叫[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式。

1. 您變更目前的資料錄的適當欄位。

1. 結束作業，並正常地認可更新，藉由呼叫[更新](../../mfc/reference/crecordset-class.md#update)成員函式。

開放式鎖定鎖定只在資料來源上的資料錄`Update`呼叫。 如果您使用開放式鎖定在多使用者環境中，應用程式應該處理`Update`失敗狀況。 封閉式鎖定鎖定的記錄，只要您呼叫`Edit`並不會釋放它直到您呼叫`Update`(透過指出失敗`CDBException`機制，不是由值為 FALSE 所傳回`Update`)。 封閉式鎖定有潛在的效能降低，其他使用者的影響，因為並行存取相同的記錄可能要等到您的應用程式完成`Update`程序。

##  <a name="_core_locking_records_in_your_recordset"></a> 鎖定資料錄集中的記錄

如果您想要變更資料錄集物件的[鎖定模式](#_core_record.2d.locking_modes)預設值，您必須變更模式才能呼叫`Edit`。

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>若要變更目前的鎖定模式，以您的資料錄集

1. 呼叫[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成員函式，指定`CRecordset::pessimistic`或`CRecordset::optimistic`。

新的鎖定模式會持續有效，直到您再次變更或關閉資料錄集。

> [!NOTE]
>  相對較少的 ODBC 驅動程式目前支援封閉式鎖定。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[資料錄集：新增、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)