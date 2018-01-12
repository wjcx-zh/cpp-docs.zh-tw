---
title: "資料錄集： 資料錄集更新資料錄的方式 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e38f2e62e9aa7b01680e9b2fd1e4a540ee552c3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>資料錄集：資料錄集更新資料錄的方式 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 選取記錄資料來源的能力，除了資料錄集可以 （選擇性） 更新或刪除選取的記錄或新增新的記錄。 三個因素決定資料錄集的可更新性： 連接的資料來源是否可更新，您指定當您建立資料錄集物件，並建立 SQL 的選項。  
  
> [!NOTE]
>  所在的 SQL 程式`CRecordset`物件基礎可能會影響資料錄集的可更新性。 例如，如果您的 SQL 包含聯結或**GROUP BY**子句，MFC 所設的可更新性**FALSE**。  
  
> [!NOTE]
>  本主題適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 本主題說明：  
  
-   [您在資料錄集更新角色](#_core_your_role_in_recordset_updating)和架構會做為您。  
  
-   [資料錄集為編輯緩衝區](#_core_the_edit_buffer)和[動態集和快照集之間的差異](#_core_dynasets_and_snapshots)。  
  
 [資料錄集： 如何 AddNew、 Edit 和刪除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)描述從資料錄集的觀點來看這些函式的動作。  
  
 [資料錄集： 更多有關更新 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)資料錄集更新劇本完成異動如何影響更新、 如何關閉資料錄集，或捲動影響正在進行更新，以及您的更新與其他更新之間的互動方式的說明使用者。  
  
##  <a name="_core_your_role_in_recordset_updating"></a>您在資料錄集更新的角色  
 下表顯示您的角色中加入、 編輯或刪除記錄，以及架構會做為您要使用資料錄集。  
  
### <a name="recordset-updating-you-and-the-framework"></a>資料錄集更新： 您與架構  
  
|您|架構|  
|---------|-------------------|  
|判斷是否可更新的 （或可附加的） 資料來源。|提供[CDatabase](../../mfc/reference/cdatabase-class.md)測試資料來源的可更新性或 appendability 成員函式。|  
|開啟可更新資料錄集 （任何類型）。||  
|判斷資料錄集藉由呼叫是否可以更新`CRecordset`更新函式，例如`CanUpdate`或`CanAppend`。||  
|呼叫成員函式來加入、 編輯和刪除資料錄的資料錄集。|管理您的資料錄集物件和資料來源之間交換資料的機制。|  
|（選擇性） 使用交易來控制更新程序。|提供`CDatabase`成員函式來支援交易。|  
  
 如需有關交易的詳細資訊，請參閱[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="_core_the_edit_buffer"></a>編輯緩衝區  
 起來，做為包含一筆記錄的編輯緩衝區的資料錄集的欄位資料成員 — 目前的記錄。 更新作業會使用這個緩衝區來處理目前的記錄。  
  
-   當您新增一筆記錄時，編輯緩衝區用來建立新的記錄。 當您完成新增記錄時，先前為目前的記錄會變成目前一次。  
  
-   當您更新 （編輯） 記錄，編輯緩衝區用於資料錄集的欄位資料成員設定為新的值。 當您完成更新時，更新的記錄是目前仍。  
  
 當您呼叫[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[編輯](../../mfc/reference/crecordset-class.md#edit)，因此可以視需要稍後還原儲存目前的記錄。 當您呼叫[刪除](../../mfc/reference/crecordset-class.md#delete)不會儲存目前的記錄，但是會標示為已刪除，您必須捲動至另一筆記錄。  
  
> [!NOTE]
>  編輯緩衝區不需要基底位址在刪除資料錄。 當您刪除目前的記錄時，記錄會標示為已刪除，且資料錄集 」 不位於記錄 」 直到您捲動到不同的記錄。  
  
##  <a name="_core_dynasets_and_snapshots"></a>動態集和快照集  
 [動態集](../../data/odbc/dynaset.md)重新整理資料錄的內容，當您捲動記錄。 [快照集](../../data/odbc/snapshot.md)是靜態的記錄，因此除非您呼叫不重新整理資料錄的內容[Requery](../../mfc/reference/crecordset-class.md#requery)。 若要使用動態集的所有功能，您必須使用的 ODBC 驅動程式符合 ODBC API 支援的正確層級。 如需詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和[動態](../../data/odbc/dynaset.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)