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
ms.openlocfilehash: d4e80816a131c997e9f5bfaa34f025394b05a358
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212858"
---
# <a name="recordset-locking-records-odbc"></a>資料錄集：鎖定資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題將說明：

- [可用的記錄鎖定類型](#_core_record.2d.locking_modes)。

- [如何在更新期間鎖定您的記錄集內的記錄](#_core_locking_records_in_your_recordset)。

當您使用記錄集來更新資料來源上的記錄時，您的應用程式可以鎖定記錄，讓其他使用者都無法同時更新記錄。 兩個使用者同時更新的記錄狀態是未定義的，除非系統可以保證兩個使用者無法同時更新記錄。

> [!NOTE]
>  本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果您已執行大量資料列提取，部分資訊將不適用。 例如，您無法呼叫 `Edit` 和 `Update` 成員函式。 如需大量資料列提取的詳細資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>記錄鎖定模式

資料庫類別提供兩種[記錄鎖定模式](../../mfc/reference/crecordset-class.md#setlockingmode)：

- 開放式鎖定（預設值）

- 封閉式鎖定

更新記錄會以三個步驟執行：

1. 您可以藉由呼叫[Edit](../../mfc/reference/crecordset-class.md#edit)成員函式來開始作業。

1. 您可以變更目前記錄的適當欄位。

1. 您會藉由呼叫[update](../../mfc/reference/crecordset-class.md#update)成員函式來結束作業（通常會認可更新）。

開放式鎖定只會在 `Update` 呼叫期間鎖定資料來源上的記錄。 如果您在多使用者環境中使用開放式鎖定，應用程式應該會處理 `Update` 失敗狀況。 封閉式鎖定會在您呼叫 `Edit` 時立即鎖定記錄，而且在您呼叫 `Update` 之前，不會釋放它（失敗是透過 `CDBException` 機制指出，而不是由 `Update`傳回的 FALSE 值）。 封閉式鎖定會對其他使用者造成潛在的效能負面影響，因為對相同記錄的平行存取可能必須等到應用程式的 `Update` 進程完成。

##  <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>鎖定記錄集中的記錄

如果您想要從預設值變更記錄集物件的[鎖定模式](#_core_record.2d.locking_modes)，您必須在呼叫 `Edit`之前變更模式。

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>變更記錄集的目前鎖定模式

1. 呼叫[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成員函式，並指定 `CRecordset::pessimistic` 或 `CRecordset::optimistic`。

新的鎖定模式會持續有效，直到您再次變更或關閉記錄集為止。

> [!NOTE]
>  相對較少的 ODBC 驅動程式目前支援封閉式鎖定。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
