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
ms.openlocfilehash: 578b3b39d90b3beb80dbd201d4982fee30dc6bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212871"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>資料錄集：資料錄集更新資料錄的方式 (ODBC)

本主題適用於 MFC ODBC 類別。

除了能夠從資料來源選取記錄之外，記錄集可以（選擇性）更新或刪除選取的記錄或加入新的記錄。 有三個因素會決定記錄集的可更新性：是否可以更新連接的資料來源、建立記錄集物件時所指定的選項，以及所建立的 SQL。

> [!NOTE]
>  您的 `CRecordset` 物件所依據的 SQL 可能會影響記錄集的可更新性。 例如，如果您的 SQL 包含 join 或**GROUP by**子句，MFC 會將可更新性設定為 FALSE。

> [!NOTE]
>  本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果您使用大量資料列提取，請參閱[記錄集：提取大量的記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

本主題將說明：

- [您在記錄集內更新的角色](#_core_your_role_in_recordset_updating)，以及架構為您提供的功能。

- [記錄集作為編輯緩衝區](#_core_the_edit_buffer)，以及[動態集與快照之間的差異](#_core_dynasets_and_snapshots)。

[記錄集： AddNew、Edit 和 Delete Work （ODBC）如何](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)從記錄集的觀點來描述這些函式的動作。

[記錄集：有關更新的詳細資訊（ODBC）](../../data/odbc/recordset-more-about-updates-odbc.md)藉由說明交易如何影響更新、關閉記錄集或滾動對進行中的更新，以及更新與其他使用者的更新互動的方式，完成記錄集更新的故事。

##  <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>您在記錄集更新中的角色

下表顯示您在使用記錄集來新增、編輯或刪除記錄時的角色，以及架構為您提供的功能。

### <a name="recordset-updating-you-and-the-framework"></a>記錄集更新：您和架構

|您|架構|
|---------|-------------------|
|判斷資料來源是否可更新（或可附加）。|提供[CDatabase](../../mfc/reference/cdatabase-class.md)成員函式，以測試資料來源的可更新性或 appendability。|
|開啟可更新的記錄集（屬於任何類型）。||
|藉由呼叫 `CRecordset` 的更新函數（例如 `CanUpdate` 或 `CanAppend`），判斷記錄集是否可更新。||
|通話記錄集成員函式來加入、編輯和刪除記錄。|管理您的記錄集物件與資料來源之間交換資料的機制。|
|（選擇性）使用交易來控制更新程式。|提供 `CDatabase` 成員函式以支援交易。|

如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)。

##  <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>編輯緩衝區

總之，記錄集的欄位資料成員可作為編輯緩衝區，其中包含一筆記錄，也就是目前的記錄。 更新作業會使用這個緩衝區來操作目前的記錄。

- 當您新增記錄時，會使用編輯緩衝區來建立新的記錄。 當您完成新增記錄時，先前目前的記錄會再次變成「最新」。

- 當您更新（編輯）記錄時，會使用編輯緩衝區將記錄集的欄位資料成員設定為新的值。 當您完成更新時，更新的記錄仍然是最新的。

當您呼叫[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[Edit](../../mfc/reference/crecordset-class.md#edit)時，會儲存目前的記錄，以便稍後視需要進行還原。 當您呼叫[Delete](../../mfc/reference/crecordset-class.md#delete)時，不會儲存目前的記錄，但會標示為已刪除，而且您必須滾動到另一筆記錄。

> [!NOTE]
>  編輯緩衝區在刪除記錄時不會扮演任何角色。 當您刪除目前的記錄時，記錄會標示為已刪除，而記錄集是「不在記錄」上，直到您滾動到不同的記錄為止。

##  <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>動態集和快照

當您滾動到記錄時，[動態集](../../data/odbc/dynaset.md)會重新整理記錄的內容。 [快照](../../data/odbc/snapshot.md)集是記錄的靜態標記法，因此除非您呼叫重新[查詢](../../mfc/reference/crecordset-class.md#requery)，否則不會重新整理記錄的內容。 若要使用動態集的所有功能，您必須使用符合正確 ODBC API 支援層級的 ODBC 驅動程式。 如需詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和[動態集](../../data/odbc/dynaset.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
