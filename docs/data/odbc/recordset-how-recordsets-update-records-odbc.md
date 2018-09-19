---
title: 資料錄集： 資料錄集更新資料錄的方式 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dde8f13be6039ba035a382e3c284112eeb39c0ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067138"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>資料錄集：資料錄集更新資料錄的方式 (ODBC)

本主題適用於 MFC ODBC 類別。  
  
除了能夠從資料來源選取資料錄，資料錄集可以 （選擇性） 更新或刪除選取的資料錄或新增新的記錄。 三個因素會決定資料錄集的可更新性： 連接的資料來源是否可更新，您指定當您建立資料錄集物件，並建立 SQL 的選項。  
  
> [!NOTE]
>  在其上的 SQL 程式`CRecordset`物件根據可能會影響資料錄集的可更新性。 例如，如果您的 SQL 包含聯結，或是**GROUP BY**子句，MFC 就會將可更新性設定為 FALSE。  
  
> [!NOTE]
>  本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
本主題說明：  
  
- [您在資料錄集更新的角色](#_core_your_role_in_recordset_updating)和架構會為您。  
  
- [資料錄集為編輯緩衝區](#_core_the_edit_buffer)而[動態集與快照集之間的差異](#_core_dynasets_and_snapshots)。  
  
[資料錄集： 如何 AddNew、 Edit 和刪除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)描述從資料錄集的觀點來看這些函式的動作。  
  
[資料錄集： 更多有關更新 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)完成該資料錄集更新劇本解釋異動如何影響更新、 如何關閉資料錄集，或捲動會影響正在進行更新，以及如何更新您的互動的其他更新使用者。  
  
##  <a name="_core_your_role_in_recordset_updating"></a> 您在資料錄集更新的角色  

下表顯示您的角色中加入、 編輯或刪除記錄，以及架構會為您要使用資料錄集。  
  
### <a name="recordset-updating-you-and-the-framework"></a>正在更新資料錄集： 您與架構  
  
|您|架構|  
|---------|-------------------|  
|判斷資料來源是否可更新的 （或可附加的）。|供應[CDatabase](../../mfc/reference/cdatabase-class.md)來測試資料來源的可更新性或 appendability 成員函式。|  
|開啟 （的任何類型） 的可更新資料錄集。||  
|判斷資料錄集是否可更新，藉由呼叫`CRecordset`更新函式，例如`CanUpdate`或`CanAppend`。||  
|呼叫成員函式來加入、 編輯和刪除資料錄的資料錄集。|管理您的資料錄集物件和資料來源之間交換資料的機制。|  
|（選擇性） 使用交易來控制更新程序。|提供`CDatabase`成員函式來支援交易。|  
  
如需有關交易的詳細資訊，請參閱[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_the_edit_buffer"></a> 編輯緩衝區  

起來，做為包含一筆記錄的編輯緩衝區的資料錄集的欄位資料成員 — 目前的記錄。 更新作業會使用這個緩衝區，對目前的記錄。  
  
- 當您新增一筆記錄時，編輯緩衝區用來建立新的記錄。 當您完成新增記錄時，先前為目前的記錄會變成目前一次。  
  
- 當您更新 （編輯） 的記錄，編輯緩衝區會用來將資料錄集的欄位資料成員設定為新的值。 當您完成更新時，更新的記錄是目前仍。  
  
當您呼叫[AddNew](../../mfc/reference/crecordset-class.md#addnew)或是[編輯](../../mfc/reference/crecordset-class.md#edit)，目前的記錄會儲存以便稍後視需要還原。 當您呼叫[刪除](../../mfc/reference/crecordset-class.md#delete)不會儲存目前的記錄，但是會標示為已刪除，您必須捲動至另一筆記錄。  
  
> [!NOTE]
>  編輯緩衝區會扮演任何角色，在刪除資料錄。 當您刪除目前的記錄時，記錄會標示為刪除，以及資料錄集是 「 不在上一筆記錄 」，直到您捲動到不同的記錄。  
  
##  <a name="_core_dynasets_and_snapshots"></a> 動態集和快照集  

[動態集](../../data/odbc/dynaset.md)捲動至記錄時，請重新整理資料錄的內容。 [快照集](../../data/odbc/snapshot.md)是靜態的記錄，因此除非您呼叫不重新整理資料錄的內容[Requery](../../mfc/reference/crecordset-class.md#requery)。 若要使用的動態集的所有功能，您必須使用的 ODBC 驅動程式符合 ODBC API 支援的正確層級。 如需詳細資訊，請參閱 < [ODBC](../../data/odbc/odbc-basics.md)並[動態集](../../data/odbc/dynaset.md)。  
  
## <a name="see-also"></a>另請參閱  

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)