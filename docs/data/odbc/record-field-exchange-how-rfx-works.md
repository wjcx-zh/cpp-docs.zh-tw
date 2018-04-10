---
title: 資料錄欄位交換： RFX 的運作方式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5eac97bb87103bd72dfd721515baf58324fc851f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-how-rfx-works"></a>資料錄欄位交換：RFX 的運作方式
本主題說明 RFX 程序。 這是進階主題涵蓋：  
  
-   [RFX 和資料錄集](#_core_rfx_and_the_recordset)  
  
-   [RFX 程序](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  本主題適用於衍生自類別`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，被實作大量資料錄欄位交換 (Bulk RFX)。 大量 RFX 與 RFX 相似。 若要了解的差異，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_rfx_and_the_recordset"></a>RFX 和資料錄集  
 資料錄集物件的欄位資料成員，同時採用兩者，構成編輯緩衝區，儲存一筆記錄的所選資料行。 當第一次開啟資料錄集，而且即將讀取第一筆記錄時，RFX 繫結 （連結） 每個會選取資料行的適當欄位資料成員的位址。 當資料錄集更新記錄時，RFX 呼叫 ODBC API 函式，將 SQL**更新**或**插入**驅動程式的陳述式。 RFX 會使用欄位資料成員了的解，指定要寫入的資料行。  
  
 架構會備份編輯緩衝區在某些階段，所以它可以還原其內容，如有必要。 RFX 備份編輯緩衝區，然後再加入新的記錄，然後再編輯現有的記錄。 它會在某些情況下，例如，編輯緩衝區還原之後**更新**呼叫下列`AddNew`。 如果您放棄最近變更的編輯緩衝區，例如，將移到另一筆記錄，然後再呼叫編輯緩衝區不還原**更新**。  
  
 除了之間交換資料的資料來源和資料錄集的欄位資料成員，RFX 管理繫結參數。 開啟資料錄集時，任何參數的資料成員會繫結的順序"？"的 SQL 陳述式中的預留位置，`CRecordset::Open`建構。 如需詳細資訊，請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
 資料錄集類別的覆寫`DoFieldExchange`所有工作，以兩個方向移動資料。 對話方塊資料交換 (DDX)，例如 RFX 需要您的類別資料成員的相關資訊。 精靈會提供所需的資訊寫入的資料錄集特定實作`DoFieldExchange`，根據欄位資料成員名稱和資料類型您使用精靈來指定。  
  
##  <a name="_core_the_record_field_exchange_process"></a>資料錄欄位交換程序  
 本章節描述 RFX 事件的順序，開啟資料錄集物件時，當您新增、 更新和刪除記錄。 資料表[順序的 RFX 作業期間資料錄集開啟](#_core_sequence_of_rfx_operations_during_recordset_open)和資料表[順序 RFX 捲動的作業期間](#_core_sequence_of_rfx_operations_during_scrolling)本主題中示範的程序作為 RFX 程序**移動**命令集，以及管理更新。 在這些程序， [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)呼叫以執行許多不同的作業。 **M_nOperation**資料成員[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件可讓您判斷哪些作業的要求。 您也許會很有幫助讀取[資料錄集： 如何資料錄集選取資料錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)閱讀這份資料之前。  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX： 初始繫結的資料行和參數  
 中的順序顯示，當您呼叫資料錄集物件的下列 RFX 活動發生[開啟](../../mfc/reference/crecordset-class.md#open)成員函式：  
  
-   如果資料錄集具有參數的資料成員，架構會呼叫`DoFieldExchange`繫結至資料錄集的 SQL 陳述式字串中參數預留位置的參數。 資料型別相關參數的值表示法用於每個預留位置中找到**選取**陳述式。 發生這種情況的 SQL 陳述式已備妥，但會在執行之前。 準備陳述式的相關資訊，請參閱**:: SQLPrepare** ODBC 中的函式*程式設計人員參考*。  
  
-   這個架構會呼叫`DoFieldExchange`將選取的資料行的值繫結至資料錄集中的對應欄位資料成員的第二個時機。 此為編輯緩衝區包含第一筆記錄的資料行建立資料錄集物件。  
  
-   資料錄集執行 SQL 陳述式和資料來源選取第一筆記錄。 資料錄的資料行載入至資料錄集的欄位資料成員。  
  
 當您開啟資料錄集時下, 表會顯示一系列的 RFX 作業。  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>RFX 資料錄集開啟時的作業順序  
  
|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|  
|--------------------|-------------------------------|-----------------------------|  
|1.開啟資料錄集。|||  
||2.建立 SQL 陳述式。||  
|||3.傳送 SQL。|  
||4.繫結的參數資料成員。||  
||5.將欄位資料成員的繫結至資料行。||  
|||6.ODBC 會移動，並填入資料。|  
||7.C + + 的修復資料。||  
  
 資料錄集使用 ODBC 的備妥的執行，以允許快速查詢相同的 SQL 陳述式。 如需備妥的執行的詳細資訊，請參閱 ODBC SDK*程式設計人員參考*MSDN Library 中。  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a>RFX： 捲動  
 當從一筆資料錄捲動到另一個時，架構會呼叫`DoFieldExchange`之前儲存在新記錄的值的欄位資料成員的值取代。  
  
 下表顯示 RFX 作業的順序，當使用者將記錄記錄。  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a>捲動期間 RFX 作業的順序  
  
|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|  
|--------------------|-------------------------------|-----------------------------|  
|1.呼叫`MoveNext`或其中一個其他移動函式。|||  
|||2.ODBC 會移動，並填入資料。|  
||3.C + + 的修復資料。||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX： 加入新的記錄與編輯現有的記錄  
 如果您加入新的記錄時，資料錄集會為編輯緩衝區來建立新記錄的內容。 與加入資料錄、 編輯記錄包含變更資料錄集的欄位資料成員的值。 從 RFX 觀點來看，順序如下所示：  
  
1.  資料錄集的呼叫[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式會導致 RFX 儲存目前的編輯緩衝區，以便稍後還原。  
  
2.  `AddNew`或**編輯**準備編輯緩衝區中的欄位，如此 RFX 可以偵測已變更的欄位資料成員。  
  
     新的記錄已經沒有先前的值比較新的因為`AddNew`設定的每個欄位資料成員值**PSEUDO_NULL**值。 稍後，當您呼叫**更新**，RFX 比較每個資料成員的值，與**PSEUDO_NULL**值。 如果有差異，已設定的資料成員。 (**PSEUDO_NULL**不具有 true 的 Null 值的記錄資料行同時也不是的其中一個 c + + 相同**NULL**。)  
  
     不同於**更新**呼叫`AddNew`、**更新**呼叫**編輯**比較更新的值與先前儲存的值，而不是使用**PSEUDO_NULL**。 其差異在於，`AddNew`不含先前儲存的值進行比較。  
  
3.  您想要編輯其值或您想要填入新的記錄時，直接設定欄位資料成員的值。 這可能包括呼叫`SetFieldNull`。  
  
4.  呼叫[更新](../../mfc/reference/crecordset-class.md#update)步驟 2 中所述，為已變更的欄位資料成員，會檢查 (請參閱表格[順序 RFX 捲動的作業期間](#_core_sequence_of_rfx_operations_during_scrolling))。 如果沒有任何已變更，**更新**傳回 0。 如果某些欄位資料成員已變更，**更新**準備及執行 SQL**插入**陳述式，其中包含記錄中的所有更新欄位的值。  
  
5.  如`AddNew`，**更新**結束時，會還原先前儲存的記錄之前的目前值`AddNew`呼叫。 如**編輯**，將會保留，編輯的值。  
  
 下表顯示 RFX 作業的順序，當您新增新的記錄，或編輯現有的記錄。  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>在 AddNew 和編輯期間 RFX 作業的順序  
  
|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|  
|--------------------|-------------------------------|-----------------------------|  
|1.呼叫`AddNew`或**編輯**。|||  
||2.備份編輯緩衝區。||  
||3.如`AddNew`、 標示為 「 清除 」 的欄位資料成員和 Null。||  
|4.將值指派給資料錄集欄位資料成員。|||  
|5.呼叫**更新**。|||  
||6.檢查已變更的欄位。||  
||7.建置 SQL**插入**陳述式`AddNew`或**更新**陳述式**編輯**。||  
|||8.傳送 SQL。|  
||9.如`AddNew`，編輯緩衝區還原到其備份內容。 如**編輯**，刪除備份。||  
  
### <a name="rfx-deleting-existing-records"></a>RFX： 刪除現有的資料錄  
 當您刪除記錄時，RFX 會將所有的欄位設定為**NULL**提醒，刪除該記錄，並且您必須關閉它。 您不需要任何其他 RFX 順序資訊。  
  
## <a name="see-also"></a>請參閱  
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [巨集、 全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)  
 [CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)