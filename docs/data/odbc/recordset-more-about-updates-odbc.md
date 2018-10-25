---
title: 資料錄集： 了解更新 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 187971adef984ab35299970ce23cb4332c9fb070
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053444"
---
# <a name="recordset-more-about-updates-odbc"></a>資料錄集：更多更新的詳細資訊 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明：

- [其他作業，例如交易、 如何影響更新](#_core_how_transactions_affect_updates)。

- [您的更新和其他使用者的](#_core_your_updates_and_the_updates_of_other_users)。

- [深入了解的 Update 和 Delete 的成員函式](#_core_more_about_update_and_delete)。

> [!NOTE]
>  本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果您已實作大量資料列擷取，部分資訊不適用。 例如，您不能呼叫`AddNew`， `Edit`， `Delete`，和`Update`成員函式; 不過，您可以在其中執行的交易。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="_core_how_other_operations_affect_updates"></a> 其他作業如何影響更新

更新會影響交易作用中的更新時完成的交易之前關閉資料錄集並捲動完成交易之前。

###  <a name="_core_how_transactions_affect_updates"></a> 異動如何影響更新

除了了解如何`AddNew`， `Edit`，並`Delete`工作，請務必了解如何`BeginTrans`， `CommitTrans`，和`Rollback`的成員函式[CDatabase](../../mfc/reference/cdatabase-class.md)搭配更新函式[CRecordset](../../mfc/reference/crecordset-class.md)。

根據預設，呼叫`AddNew`並`Edit`影響的資料來源，當您呼叫立即`Update`。 `Delete` 呼叫會立即生效。 但是，您可以設定交易，並執行這類呼叫的批次。 更新不是永久的除非您認可它們。 如果您改變心意，您可以回復而不是認可交易。

如需有關交易的詳細資訊，請參閱[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。

###  <a name="_core_how_closing_the_recordset_affects_updates"></a> 如何關閉資料錄集影響更新

如果您關閉資料錄集，或其相關聯`CDatabase`物件，並將進行中交易 (您不呼叫[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback))，則會復原交易備份會自動 （除非您的資料庫後端是 Microsoft Jet 資料庫引擎）。

> [!CAUTION]
>  如果您使用 Microsoft Jet database engine，關閉資料錄集在明確交易不會導致發行的任何已修改的資料列或明確的交易認可或回復之前所放置的鎖定。 建議，您永遠都開啟和關閉資料錄集之內或之外的明確的 Jet 交易。

###  <a name="_core_how_scrolling_affects_updates"></a> 捲動如何影響更新

當您[資料錄集： 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)集中的資料錄，編輯緩衝區會填入新的目前資料錄 （上一筆記錄不儲存第一次）。 您可以捲動會跳過先前刪除的記錄。 如果您捲動之後`AddNew`或是`Edit`呼叫，而不需呼叫`Update`， `CommitTrans`，或`Rollback`首先，任何變更都會遺失 （與您無警告），新的記錄功能導入編輯緩衝區。 編輯緩衝區會填入捲動到哪一個記錄、 預存的資料錄已釋放，且不會變更資料來源上。 這同時適用於`AddNew`和`Edit`。

##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> 您的更新和其他使用者的更新

當您使用資料錄集更新資料時，您的更新會影響其他使用者。 同樣地，其他使用者資料錄集的存留期間的更新會影響您。

在多使用者環境中，其他使用者可以開啟包含一些您已選取資料錄集中的記錄相同的資料錄集。 在擷取前一筆記錄的變更會反映在您的資料錄集。 動態集在每次您捲動到它時，都會擷取一筆記錄，因為動態集反映變更每個您捲動到 一筆記錄的時間。 快照集在第一次您捲動，所以快照集反映只有在您一開始捲動至記錄之前發生的變更時，都會擷取的記錄。

在您開啟資料錄集後，其他使用者所加入的記錄不會顯示在資料錄集除非您重新查詢。 如果您的資料錄集是動態集，編輯現有的記錄，其他使用者顯示在動態集時您捲動到 受影響的記錄。 如果資料錄集是快照集，直到您重新查詢快照集，不要顯示編輯。 如果您想要查看記錄新增或刪除您的快照集或在動態集，其他使用者所加入的記錄中的其他使用者呼叫[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)重建資料錄集。 （請注意，刪除其他使用者的顯示在動態集）。您也可能會呼叫`Requery`若要查看記錄您新增，但若要看到您的刪除動作。

> [!TIP]
>  若要強制整個快照集一次的快取，請呼叫`MoveLast`立即開啟快照集之後。 然後呼叫`MoveFirst`若要開始使用的記錄。 `MoveLast` 相當於捲動透過所有記錄，但它全部一次擷取它們。 不過請注意，這可以降低效能，而且可能不需要部分驅動程式。

對其他使用者更新的影響是類似於對您的影響。

##  <a name="_core_more_about_update_and_delete"></a> 更新與刪除的詳細資訊

本章節提供可協助您使用的其他資訊`Update`和`Delete`。

### <a name="update-success-and-failure"></a>更新成功和失敗

如果`Update`成功，`AddNew`或`Edit`模式結束。 若要開始`AddNew`或是`Edit`再次模式中，呼叫`AddNew`或`Edit`。

如果`Update`失敗 （會傳回 FALSE 或擲回例外狀況），您仍握有`AddNew`或`Edit`模式中，根據哪一個函式最後呼叫。 接著，您可以執行下列其中一項：

- 修改的欄位資料成員，然後再試`Update`一次。

- 呼叫`AddNew`設為 Null 的欄位資料成員，設定欄位資料成員的值，然後呼叫`Update`一次。

- 呼叫`Edit`若要重新載入資料錄集的第一個呼叫之前的值`AddNew`或是`Edit`、 設定欄位資料成員的值，然後呼叫`Update`一次。 成功之後`Update`呼叫 (除了之後`AddNew`呼叫)，欄位資料成員保留在新的值。

- 呼叫`Move`(包括`Move`AFX_MOVE_REFRESH，或者為 0 的參數)，可排清任何變更，並結束任何`AddNew`或`Edit`作用中的模式。

### <a name="update-and-delete"></a>Update 和 Delete

本節同時適用於`Update`和`Delete`。

在 `Update`或`Delete`作業，應該更新只能有一個記錄。 該記錄是目前的記錄，其對應至資料錄集的欄位中的資料值。 如果基於某些原因沒有記錄會受到影響，或多筆記錄會受到影響時，會擲回例外狀況包含下列其中一種**RETCODE**值：

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

擲回這些例外狀況時，您仍握有`AddNew`或是`Edit`您還在您呼叫時的狀態`Update`或`Delete`。 以下是最常見的案例中，您會看到這些例外狀況。 您應該會看到：

- AFX_SQL_ERROR_NO_ROWS_AFFECTED，當您使用開放式鎖定的模式，而且其他使用者已修改的記錄方式，可防止架構用來識別要更新或刪除正確的記錄。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED，當您正在更新資料表沒有主索引鍵或唯一索引，且您沒有足夠的資料行中資料錄集來唯一識別資料表的資料列。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[例外狀況：資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)