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
ms.openlocfilehash: abd5f817ad321241df2d8565bd6bf346c0792088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366968"
---
# <a name="recordset-locking-records-odbc"></a>資料錄集：鎖定資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題將說明：

- [可用的紀錄鎖定類型](#_core_record.2d.locking_modes)。

- [如何在更新期間鎖定紀錄集中的紀錄](#_core_locking_records_in_your_recordset)。

當您使用記錄集更新數據來源上的記錄時,應用程式可以鎖定該記錄,以便其他使用者無法同時更新記錄。 除非系統可以保證兩個使用者不能同時更新記錄,否則兩個用戶同時更新的記錄的狀態未定義。

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果已實現批量行提取,則某些資訊不適用。 例如,不能調用和`Edit``Update`成員函數。 有關批量行提取的詳細資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>記錄鎖定模式

資料庫類別提供兩[種紀錄鎖定模式](../../mfc/reference/crecordset-class.md#setlockingmode):

- 樂觀鎖定(預設值)

- 悲觀鎖定

更新記錄分三個步驟進行:

1. 通過調用[「編輯](../../mfc/reference/crecordset-class.md#edit)」成員函數開始操作。

1. 更改目前記錄的相應欄位。

1. 通過調用[Update](../../mfc/reference/crecordset-class.md#update)成員函數,結束操作(通常提交更新)。

樂觀鎖定僅在`Update`調用期間鎖定數據源上的記錄。 如果在多用戶環境中使用樂觀鎖定,則應用程式應處理`Update`故障情況。 悲觀鎖定`Edit`在調用時立即鎖定記錄,並且在調`Update`用 之前不會釋放它(`CDBException`故障通過 機制指示`Update`,而不是由返回的 FALSE 值指示)。 悲觀鎖定對其他使用者可能具有性能損失,因為對同一記錄的併發訪問可能必須等到應用程式`Update`的進程完成。

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>在紀錄集中鎖定記錄

如果要從預設值更改記錄集物件的[鎖定模式](#_core_record.2d.locking_modes),則必須在`Edit`調用 之前更改該模式。

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>變更記錄集的目前鎖定模式

1. 呼叫[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成員函數`CRecordset::pessimistic``CRecordset::optimistic`,指定或 。

新的鎖定模式保持有效,直到您再次更改它或關閉記錄集。

> [!NOTE]
> 目前支援悲觀鎖定的ODBC驅動程式相對較少。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
