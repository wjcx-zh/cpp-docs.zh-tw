---
title: 資料錄欄位交換： RFX 的運作方式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cf22876ee49538f9e9a162e5defe4abe693617e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037095"
---
# <a name="record-field-exchange-how-rfx-works"></a>資料錄欄位交換：RFX 的運作方式

本主題說明 RFX 程序。 這是一種進階主題涵蓋：  
  
- [RFX 和資料錄集](#_core_rfx_and_the_recordset)  
  
- [RFX 程序](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  本主題適用於衍生自類別`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，被實作大量資料錄欄位交換 (Bulk RFX)。 大量 RFX 很類似 RFX。 若要了解這些差異，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX 和資料錄集  

資料錄集物件的欄位資料成員，結合在一起，構成保留選取的資料行的一筆資料錄編輯緩衝區。 當第一次開啟資料錄集，並將要讀取第一筆記錄時，RFX 繫結 （連結） 每個選取資料行，以適當的欄位資料成員的位址。 RFX 資料錄集更新的記錄，當呼叫 ODBC API 函式能傳送 SQL**更新**或是**插入**驅動程式的陳述式。 RFX 會指定要寫入的資料行使用的欄位資料成員的了解。  
  
架構會備份編輯緩衝區在某些階段，因此如有必要，它可以還原其內容。 RFX 備份編輯緩衝區，然後再加入新的記錄，以及之前編輯現有的記錄。 它會編輯緩衝區，在某些情況下，例如，還原後`Update`呼叫下列`AddNew`。 如果您放棄最近變更的編輯緩衝區，比方說，移至另一筆記錄，然後再呼叫，不還原編輯緩衝區`Update`。  
  
除了交換資料的資料來源和資料錄集的欄位資料成員之間，RFX 管理繫結參數。 開啟資料錄集時，任何參數的資料成員會繫結的順序 」？ 」 的 SQL 陳述式中的預留位置，`CRecordset::Open`建構。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
資料錄集類別的覆寫的`DoFieldExchange`會執行所有工作，然後以兩個方向移動資料。 對話方塊資料交換 (DDX)，例如 RFX 會需要您的類別的資料成員的相關資訊。 精靈會提供所需的資訊寫入的資料錄集特定實作`DoFieldExchange`，根據欄位資料成員名稱和資料類型您使用精靈來指定。  
  
##  <a name="_core_the_record_field_exchange_process"></a> 資料錄欄位交換程序  

本章節描述 RFX 事件的順序，因為開啟資料錄集物件，並隨著您新增、 更新和刪除記錄。 資料表[序列的 RFX 作業期間的資料錄集開放](#_core_sequence_of_rfx_operations_during_recordset_open)和資料表[順序 RFX 捲動的作業期間](#_core_sequence_of_rfx_operations_during_scrolling)本主題中示範的程序作為 RFX 程序`Move`命令資料錄集，以及管理更新。 在這些程序期間[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)呼叫以執行許多不同的作業。 `m_nOperation`資料成員[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件可讓您判斷在要求的作業。 您可能會發現它很有幫助讀取[資料錄集： 如何資料錄集選取資料錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)並[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)閱讀這份資料之前。  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX： 輸入初始的繫結的資料行和參數  

中的順序顯示，當您呼叫資料錄集物件的下列 RFX 活動發生[開啟](../../mfc/reference/crecordset-class.md#open)成員函式：  
  
- 如果資料錄集具有參數的資料成員，架構會呼叫`DoFieldExchange`繫結至資料錄集的 SQL 陳述式字串中的參數預留位置的參數。 在中找到的資料型別相依參數的值表示用於每個預留位置**選取**陳述式。 發生這種情況的備妥的 SQL 陳述式之後，但會在執行之前。 陳述式準備的相關資訊，請參閱`::SQLPrepare`ODBC 中的函式*程式設計人員參考*。  
  
- 這個架構會呼叫`DoFieldExchange`第二次選取的資料行的值繫結至資料錄集中的對應欄位資料成員。 此為編輯緩衝區包含第一筆記錄的資料行建立資料錄集物件。  
  
- 資料錄集執行 SQL 陳述式和資料來源選取第一筆記錄。 資料錄的資料行載入資料錄集的欄位資料成員。  
  
下表顯示 RFX 作業的順序，當您開啟資料錄集。  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> RFX 資料錄集開啟時的作業順序  
  
|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|  
|--------------------|-------------------------------|-----------------------------|  
|1.開啟資料錄集。|||  
||2.建立 SQL 陳述式。||  
|||3.傳送 SQL。|  
||4.繫結參數的資料成員。||  
||5.將欄位資料成員的繫結至資料行。||  
|||6.ODBC 會移動，並填入資料。|  
||7.C + + 的修復資料。||  
  
資料錄集以供快速查詢相同的 SQL 陳述式使用 ODBC 的備妥的執行。 如需備妥的執行的詳細資訊，請參閱 ODBC SDK*程式設計人員參考*MSDN Library 中。  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX： 捲動  

當您從一個資料錄捲動到另一個時，架構會呼叫`DoFieldExchange`來取代先前儲存在新資料錄的值的欄位資料成員的值。  
  
下表顯示 RFX 作業的順序，當使用者將記錄記錄。  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> 捲動期間 RFX 作業的順序  
  
|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|  
|--------------------|-------------------------------|-----------------------------|  
|1.呼叫`MoveNext`或其中一個其他移動函式。|||  
|||2.ODBC 會移動，並填入資料。|  
||3.C + + 的修復資料。||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX： 加入新資料錄和編輯現有的記錄  

如果您加入新的記錄，以建立新的資料錄的內容編輯緩衝區表示資料錄集。 與加入資料錄、 編輯記錄包含變更資料錄集的欄位資料成員的值。 RFX 的觀點而言，順序如下所示：  
  
1. 資料錄集的呼叫[AddNew](../../mfc/reference/crecordset-class.md#addnew)或是[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式會導致 RFX 儲存目前的編輯緩衝區，以便稍後還原。  
  
1. `AddNew` 或`Edit`準備編輯緩衝區中的欄位，如此 RFX 可以偵測已變更的欄位資料成員。  
  
     新的記錄不的任何先前的值比較新的因為`AddNew`PSEUDO_NULL 值來設定每個欄位資料成員的值。 稍後，當您呼叫`Update`，RFX 比較 PSEUDO_NULL 值的每個資料成員的值。 如果沒有差異，已設定的資料成員。 (PSEUDO_NULL 不相同，則為 true 的 Null 值的記錄資料行，也不是其中之一為 NULL 的 c + + 相同。)  
  
     不同於`Update`呼叫`AddNew`，則`Update`呼叫`Edit`比較更新與先前儲存的值，而不是使用 PSEUDO_NULL 的值。 其差異在於`AddNew`不含先前儲存的值進行比較。  
  
1. 您想要編輯其值或您想要填滿新資料錄時，直接設定欄位資料成員的值。 這可能包括呼叫`SetFieldNull`。  
  
1. 您呼叫[更新](../../mfc/reference/crecordset-class.md#update)步驟 2 中所述，為已變更的欄位資料成員，會檢查 (請參閱表格[順序 RFX 捲動的作業期間](#_core_sequence_of_rfx_operations_during_scrolling))。 如果沒有任何已變更，`Update`會傳回 0。 如果某些欄位資料成員已變更，`Update`準備及執行 SQL**插入**陳述式包含在記錄中的所有更新欄位的值。  
  
1. 針對`AddNew`，`Update`結束時，會還原先前儲存的值之前為目前的記錄`AddNew`呼叫。 針對`Edit`，留在原處，新的已編輯的值。  
  
下表顯示 RFX 作業的順序，當您加入新的記錄，或編輯現有的記錄。  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>RFX AddNew 和編輯期間的作業順序  
  
|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|  
|--------------------|-------------------------------|-----------------------------|  
|1.呼叫`AddNew`或`Edit`。|||  
||2.備份編輯緩衝區。||  
||3.針對`AddNew`、 標示為 「 全新方式 」 的欄位資料成員和 Null。||  
|4.指派值給資料錄集的欄位資料成員。|||  
|5.呼叫 `Update`。|||  
||6.檢查已變更的欄位。||  
||7.建置 SQL**插入**陳述式`AddNew`或是**更新**陳述式`Edit`。||  
|||8.傳送 SQL。|  
||9.針對`AddNew`，還原其備份內容的編輯緩衝區。 針對`Edit`，刪除備份。||  
  
### <a name="rfx-deleting-existing-records"></a>RFX： 刪除現有的記錄  

當您刪除記錄時，RFX 會設定為 NULL 的所有欄位提醒您刪除該記錄，您必須將它移出。 您不需要任何其他 RFX 順序資訊。  
  
## <a name="see-also"></a>另請參閱  

[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[巨集、 全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)