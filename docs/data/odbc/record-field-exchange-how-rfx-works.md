---
title: "資料錄欄位交換：RFX 的運作方式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料繫結 [C++], DFX"
  - "ODBC [C++], RFX"
  - "資料錄編輯 [C++], 使用 RFX"
  - "RFX (ODBC) [C++], 繫結欄位和參數"
  - "RFX (ODBC) [C++], 更新資料錄集中的資料"
  - "捲動 [C++]"
  - "捲動 [C++], RFX"
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 資料錄欄位交換：RFX 的運作方式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題說明 RFX 處理過程。  這個進階主題包含：  
  
-   [RFX 和資料錄集](#_core_rfx_and_the_recordset)  
  
-   [RFX 處理過程](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  這個主題適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  如果您要使用大量資料列擷取，就實作大量資料錄欄位交換 \(Bulk RFX\)。  Bulk RFX 類似 RFX。  若要了解兩者間的差異，請參閱[資料錄集：擷取 大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX 和資料錄集  
 將資料錄集物件的欄位資料成員聚集在一起，組成一個編輯緩衝區，儲存一個資料錄的選定資料行。  當第一次開啟資料錄集且正要讀取第一筆資料錄，RFX 會繫結 \(關聯\) 每個所選的資料行至適當的欄位資料成員的位址。  當資料錄集更新一筆資料錄，RFX 會呼叫 ODBC API 函式以傳送一個 SQL **UPDATE** 或 **INSERT** 陳述式至驅動程式。  RFX 使用其對欄位資料成員的認知來指定要寫入的資料行。  
  
 架構會在某個階段備份編輯緩衝區，如此它可在必要時還原其內容。  RFX 會在新增一筆資料錄和編輯一筆已存在的資料錄前先備份編輯緩衝區。  它會在某些情況下還原編輯緩衝區，例如，在 `AddNew` 之後的 **Update** 呼叫後。  若您放棄一個最近變更的編輯緩衝區，則它不會還原編輯緩衝區，例如，在呼叫 **Update** 前移動至其他的資料錄。  
  
 除了在資料來源和資料錄集的欄位資料成員間交換資料外，RFX 也會管理繫結的參數。  當開啟資料錄集時，所有的參數資料成員會以 `CRecordset::Open` 建構之 SQL 陳述式內的 "?" 替代符號順序來繫結。  如需詳細資訊，請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
 您的資料錄集類別的 `DoFieldExchange` 覆寫函式會做好所有雙向移動資料的工作。  就像對話資料交換 \(DDX\)，RFX 需要您的類別的資料成員之相關資訊。  精靈會根據您指定給它的欄位資料成員名稱和資料型別，藉由寫入資料錄集特定的 `DoFieldExchange` 實作來為您提供必要的資訊。  
  
##  <a name="_core_the_record_field_exchange_process"></a> 資料錄欄位交換處理過程  
 本章節說明當開啟資料錄集及當您加入、更新和刪除資料錄時之 RFX 事件的順序。  在本主題內的[資料錄集開啟期間的 RFX 作業順序](#_core_sequence_of_rfx_operations_during_recordset_open)表和[捲動期間的 RFX 作業順序](#_core_sequence_of_rfx_operations_during_scrolling)表，說明了 RFX 在處理資料錄集的 **Move** 命令以及管理更新時的過程。  在這些處理過程中，會呼叫 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 來執行許多不同的作業。  [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 物件的 m\_nOperation 資料成員會決定要求哪個作業。  閱讀[資料錄集：資料錄集選取資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) 和[資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 可能對您有所幫助。  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX：資料行和參數的初始繫結  
 當您呼叫資料錄集物件的 [Open](../Topic/CRecordset::Open.md) 成員函式時，會依如下所示的順序發生下列 RFX 活動：  
  
-   如果資料錄集具有參數資料成員，架構會呼叫 `DoFieldExchange`，將這些參數繫結至資料錄集的 SQL 陳述式字串內之參數替代符號 \(Placeholder\)。  每個可在 **SELECT** 陳述式內找到的替代符號會使用與資料型別相關的參數值表示法。  這會發生在 SQL 陳述式已備妥但還未執行前。  如需陳述式準備的詳細資訊，請參閱《ODBC 程式設計人員參考》內的 **::SQLPrepare** 函式。  
  
-   架構會第二次呼叫 `DoFieldExchange` 以繫結選取的資料行值至相對之資料錄集內的欄位資料成員。  這會將資料錄集物件建立成一個包含第一筆資料錄的資料行之編輯緩衝區。  
  
-   資料錄集會執行 SQL 陳述式且資料來源會選擇第一筆資料錄。  資料錄的資料行會載入至資料錄集的欄位資料成員中。  
  
 下表說明當您開啟一個資料錄集時的 RFX 作業順序：  
  
### 資料錄集開啟期間的 RFX 作業順序  
  
|您的作業|DoFieldExchange 作業|資料庫\/SQL 作業|  
|----------|------------------------|-----------------|  
|1.  開啟資料錄集|||  
||2.  建置一個 SQL 陳述式||  
|||3.  傳送 SQL|  
||4.  繫結參數資料成員||  
||5.  繫結欄位資料成員至資料行||  
|||6.  ODBC 會做移動並填入資料|  
||7.  修復 C\+\+ 資料||  
  
 資料錄集使用 ODBC 的備製執行來允許相同 SQL 陳述式的快速查詢。  如需備製執行的詳細資訊，請參閱 MSDN Library 的《ODBC SDK 程式設計人員參考》。  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX：捲動  
 當您從一個資料錄捲動至另一個資料錄時，架構會呼叫 `DoFieldExchange` 以便使用新的資料錄值來取代原先儲存於欄位資料成員的值。  
  
 下表說明當使用者在資料錄間移動時的 RFX 作業順序：  
  
### 捲動期間的 RFX 作業順序  
  
|您的作業|DoFieldExchange 作業|資料庫\/SQL 作業|  
|----------|------------------------|-----------------|  
|1.  呼叫 `MoveNext` 或其他的 Move 函式|||  
|||2.  ODBC 會做移動並填入資料|  
||3.  修復 C\+\+ 資料||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX：加入新資料錄和編輯已存在的資料錄  
 如果您加入一筆新資料錄，資料錄集會像編輯緩衝區，建置新資料錄的內容。  加入資料錄、編輯資料錄時會使資料錄集的欄位資料成員的值產生變動。  由 RFX 的觀點，順序將如下所示：  
  
1.  您對資料錄集的 [AddNew](../Topic/CRecordset::AddNew.md) 或 [Edit](../Topic/CRecordset::Edit.md) 成員函式的呼叫，會造成 RFX 儲存目前的編輯緩衝區，以便稍後可進行還原。  
  
2.  `AddNew` 或 **Edit** 準備編輯緩衝區內的欄位，如此 RFX 可偵測到變動的欄位資料成員。  
  
     由於新增的資料錄沒有先前的值可和新值做比較，所以 `AddNew` 會將每個欄位資料成員的值設定成 **PSEUDO\_NULL** 值。  稍後，當您呼叫 **Update** 時，RFX 會將每個資料成員的值與 **PSEUDO\_NULL** 值做比較。  若其中有差異，則已設定資料成員 \(**PSEUDO\_NULL** 與具有真正 Null 值的資料錄資料行不同，且和 C\+\+ 的 **NULL** 也不一樣\)。  
  
     不像 **Update** 對於 `AddNew` 的呼叫，**Update** 對於 **Edit** 的呼叫會在已更新的值與先前預存的值間做比較而不是使用 **PSEUDO\_NULL**。  差別在於 `AddNew` 沒有可做比較的原先預存值。  
  
3.  您直接的設定那些您想要編輯或您想要填入新增資料錄的值之欄位資料成員值。  這可包含呼叫 `SetFieldNull`。  
  
4.  如步驟 2 中的說明，您對 [Update](../Topic/CRecordset::Update.md) 的呼叫會檢查變更的欄位資料成員 \(請參閱[捲動期間的 RFX 作業](#_core_sequence_of_rfx_operations_during_scrolling)表\)。  如果沒有任何的變更，**Update** 會傳回 0。  如果變動到某些欄位資料成員，**Update** 會準備並執行一個包含資料錄內所有已更新欄位的值之 SQL **INSERT** 陳述式。  
  
5.  對於 `AddNew`，**Update** 會以還原 `AddNew` 呼叫前原先儲存的目前資料錄值來終止。  對於 **Edit**，編輯的值仍會留在原處。  
  
 下表說明在您加入一筆資料錄或編輯一筆已存在的資料錄時的 RFX 作業順序。  
  
### AddNew 和 Edit 期間的 RFX 作業順序  
  
|您的作業|DoFieldExchange 作業|資料庫\/SQL 作業|  
|----------|------------------------|-----------------|  
|1.  呼叫 `AddNew` 或 **Edit**|||  
||2.  備份編輯緩衝區||  
||3.  對於 `AddNew`，將欄位資料成員標示為「清除」和 Null||  
|4.  指定資料錄集欄位資料成員的值|||  
|5.  呼叫 **Update**|||  
||6.  檢查變動的欄位||  
||7.  為 `AddNew` 建置 SQL **INSERT** 陳述式或為 **Edit** 建置 **UPDATE** 陳述式||  
|||8.  傳送 SQL|  
||9.  對於 `AddNew`，將編輯緩衝區還原成它的備份內容。  對於 **Edit**，刪除此備份||  
  
### RFX：刪除已存在的資料錄  
 當您刪除一筆資料錄，RFX 會將所有的欄位設為 **NULL**，做為資料錄已刪除的提醒，您必須將之移除。  您不需要任何其他的 RFX 序列資訊。  
  
## 請參閱  
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [巨集、全域函式和全域變數](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)