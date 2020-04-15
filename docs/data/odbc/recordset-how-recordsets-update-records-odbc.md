---
title: 資料錄集：資料錄集更新資料錄的方式 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: 03fb696c1fadd834962d37c8e75b5f8910af819e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366972"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>資料錄集：資料錄集更新資料錄的方式 (ODBC)

本主題適用於 MFC ODBC 類別。

除了從數據源中選擇記錄的能力外,記錄集還可以(可選)更新或刪除所選記錄或添加新記錄。 三個因素決定了記錄集的可更新性:連接的資料來源是否可更新、創建記錄集物件時指定的選項以及創建的 SQL。

> [!NOTE]
> `CRecordset`對象基於的 SQL 可能會影響記錄集的可更新性。 例如,如果您的 SQL 包含聯接或 GROUP **BY**子句,MFC 會將可更新性設置為 FALSE。

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果使用批量行提取,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

本主題將說明：

- [您在記錄集更新中的角色](#_core_your_role_in_recordset_updating)以及框架為您做什麼。

- [紀錄集為編輯緩衝區](#_core_the_edit_buffer)以及[動態集和快照之間的差異](#_core_dynasets_and_snapshots)。

[記錄集:如何](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)從記錄集的角度描述這些函數的操作。"

[記錄集:有關更新的詳細資訊 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)通過解釋事務如何影響更新、關閉記錄集或滾動如何影響正在進行的更新以及更新如何與其他使用者的更新交互來完成記錄集更新故事。

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>您在紀錄集更新中的角色

下表顯示了您在使用記錄集添加、編輯或刪除記錄中的角色,以及框架為您執行的作用。

### <a name="recordset-updating-you-and-the-framework"></a>記錄集更新:您和框架

|您|架構|
|---------|-------------------|
|確定數據源是可更新的(或可追加的)。|提供[CDatabase](../../mfc/reference/cdatabase-class.md)成員函數,用於測試數據源的可更新性或可追加性。|
|打開可上升的記錄集(任何類型的)。||
|通過調用`CRecordset`更新函數(`CanUpdate`如`CanAppend`或 )確定記錄集是否可更新。||
|調用記錄集成員函數以添加、編輯和刪除記錄。|管理記錄集對象和數據源之間交換數據的機制。|
|或者,使用事務來控制更新過程。|提供`CDatabase`成員功能以支援事務。|

有關交易記錄的詳細資訊,請參閱事務[(ODBC)](../../data/odbc/transaction-odbc.md)。

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>編輯緩衝區

綜合而言,記錄集的欄位數據成員用作包含一條記錄 (當前記錄)的編輯緩衝區。 更新操作使用此緩衝區對當前記錄進行操作。

- 添加記錄時,編輯緩衝區用於生成新記錄。 完成添加記錄後,以前當前的記錄將再次變為當前。

- 更新(編輯)記錄時,編輯緩衝區用於將記錄集的欄位數據成員設置為新值。 更新完成後,更新的記錄仍然是最新的。

當您調用[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[Edit](../../mfc/reference/crecordset-class.md#edit)時,將儲存當前記錄,以便以後可以根據需要還原該記錄。 當您調用[Delete](../../mfc/reference/crecordset-class.md#delete)時,不會儲存當前記錄,但標記為已刪除,您必須滾動到其他記錄。

> [!NOTE]
> 編輯緩衝區在記錄刪除中不扮演任何角色。 刪除當前記錄時,記錄將標記為已刪除,並且記錄集在滾動到其他記錄之前"不在記錄上"。

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>動態集和快照

當您滾動到記錄時,[動態集](../../data/odbc/dynaset.md)會刷新記錄的內容。 [快照](../../data/odbc/snapshot.md)是記錄的靜態表示形式,因此除非調用[Requery](../../mfc/reference/crecordset-class.md#requery),否則不會刷新記錄的內容。 要使用動態集的所有功能,您必須使用符合正確等級的 ODBC API 支援的 ODBC 驅動程式。 有關詳細資訊,請參閱[ODBC](../../data/odbc/odbc-basics.md)和[Dynaset](../../data/odbc/dynaset.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
