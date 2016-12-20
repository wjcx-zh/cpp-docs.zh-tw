---
title: "資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddNew 方法"
  - "資料錄集中的資料 [C++]"
  - "ODBC 資料錄集 [C++], 加入資料錄"
  - "ODBC 資料錄集 [C++], 刪除資料錄"
  - "ODBC 資料錄集 [C++], 編輯資料錄"
  - "資料錄編輯 [C++], 在資料錄集中"
  - "資料錄 [C++], 加入"
  - "資料錄 [C++], 在資料錄集中刪除"
  - "資料錄 [C++], 編輯"
  - "資料錄 [C++], 更新"
  - "資料錄集 [C++], 加入資料錄"
  - "資料錄集 [C++], 刪除資料錄"
  - "資料錄集 [C++], 編輯資料錄"
  - "資料錄集 [C++], 更新"
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明 `CRecordset` 類別的 `AddNew`、**Edit** 和 **Delete** 成員函式的運作方式。  涵蓋的主題包括：  
  
-   [加入資料錄的運作方式](#_core_adding_a_record)  
  
-   [加入資料錄的可視性](#_core_visibility_of_added_records)  
  
-   [編輯資料錄的運作方式](#_core_editing_an_existing_record)  
  
-   [刪除資料錄的運作方式](#_core_deleting_a_record)  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  如果您要使用大量資料列擷取，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 您可能想要閱覽[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)以增強這方面的知識，它說明了 RFX 在更新作業上的對應角色。  
  
##  <a name="_core_adding_a_record"></a> 加入資料錄  
 加入一筆新資料錄至資料錄集，會牽涉到呼叫資料錄集的 [AddNew](../Topic/CRecordset::AddNew.md) 成員函式、設定新資料錄的欄位資料成員值，以及呼叫 [Update](../Topic/CRecordset::Update.md) 成員函式將資料錄寫入資料來源。  
  
 呼叫 `AddNew` 的前提是資料錄集必須是未開啟的且不能是唯讀的。  `CanUpdate` 和 `CanAppend` 成員函式讓您可決定這些條件。  
  
 當您呼叫 `AddNew` 時：  
  
-   編輯緩衝區內的資料錄已經預存，因此若作業取消時仍可還原其內容。  
  
-   已經標示欄位資料成員，所以稍後可能可以到偵測它們的變更。  欄位資料成員也可標記為 Clean \(未變動的\) 和設為 Null。  
  
 在您呼叫 `AddNew` 後，編輯緩衝區會表示成一個新的、空資料錄，並準備好填入這些值。  若要達到這個目的，請手動地指定它們的值。  除了對欄位指定實質的值外，您還可呼叫 `SetFieldNull` 來指定 Null 值。  
  
 若要認可您的變動，請呼叫 **Update**。  當您為新資料錄呼叫 **Update** 時：  
  
-   若您的 ODBC 驅動程式支援 **::SQLSetPos** ODBC API 函式，MFC 會使用此函式在資料來源上加入資料錄。  使用 **::SQLSetPos**，MFC 可更有效地加入資料錄，因為它不需要建構和處理 SQL 陳述式。  
  
-   如果不能使用 **::SQLSetPos**，MFC 會執行下列動作：  
  
    1.  若沒有偵測到任何的變動，**Update** 不會做任何事並傳回 0。  
  
    2.  若有變動，**Update** 會建構一個 SQL **INSERT** 陳述式。  所有記錄變更的欄位資料成員所表示的資料行會列在 **INSERT** 陳述式內。  若要強制包括資料行，請呼叫 [SetFieldDirty](../Topic/CRecordset::SetFieldDirty.md) 成員函式。  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Update** 會認可新的資料錄 — 執行 **INSERT** 陳述式，並讓資料來源上的資料表認可該資料錄 \(以及不是快照集時的資料錄集\)，除非正在處理一筆交易。  
  
    4.  預存的資料錄會還原至編輯緩衝區。  在呼叫 `AddNew` 前已是目前資料錄的資料錄，將會再次地成為目前資料錄，不論 **INSERT** 陳述式是否有正確地執行。  
  
    > [!TIP]
    >  如需取得新資料錄的完整控制項，請執行下列方法：設定任何將會具有值的欄位值，然後藉由呼叫 `SetFieldNull` 並搭配欄位的指標和參數 **TRUE** \(預設值\)，明確設定任何將會保持為 Null 的欄位。  若您想要確保欄位不會編寫資料來源，可呼叫 `SetFieldDirty` 並搭配一個連至欄位的指標和參數 **FALSE**，且不要修改欄位的值。  若要決定一個欄位是否允許為 Null 值，可呼叫 `IsFieldNullable`。  
  
    > [!TIP]
    >  為了要偵測資料錄集資料成員何時變更值，MFC 使用可適用於每種資料型別的 **PSEUDO\_NULL** 值，您可將它儲存在資料錄集內。  若您必須明確地將欄位設為 **PSEUDO\_NULL** 值，且該欄位早已標記為 Null 時，您也必須呼叫 `SetFieldNull`，在第一個參數中傳遞欄位的位置並讓第二個參數為 **FALSE**。  
  
##  <a name="_core_visibility_of_added_records"></a> 加入資料錄的可視性  
 您何時可在資料錄集中看見所加入的資料錄？  加入的資料錄根據兩個因素而定，有時顯示，有時則不顯示：  
  
-   驅動程式的能力。  
  
-   架構的功能。  
  
 若您的 ODBC 驅動程式支援 **::SQLSetPos** ODBC API 函式，MFC 會使用此函式來加入資料錄。  使用 **::SQLSetPos**，任何可更新的 MFC 資料錄集都可看見所加入的資料錄。  若沒有支援此函式，則無法看見加入的資料錄，您必須呼叫 **Requery** 來看見它們。  使用 **::SQLSetPos** 也是更有效率的。  
  
##  <a name="_core_editing_an_existing_record"></a> 編輯一筆現有資料錄  
 在資料錄集內編輯現有資料錄會涉及到捲動至該資料錄、呼叫資料錄集的 [Edit](../Topic/CRecordset::Edit.md) 成員函式、設定新資料錄的欄位資料成員值，以及呼叫 [Update](../Topic/CRecordset::Update.md) 成員函式將變更的資料錄寫入資料來源。  
  
 呼叫 **Edit** 的前提是資料錄集必須是可更新的，且位在一筆資料錄上。  `CanUpdate` 和 `IsDeleted` 成員函式讓您可決定這些條件。  目前的資料錄也必須已刪除，且資料錄集內必須有資料錄 \(`IsBOF` 和 `IsEOF` 都會傳回 0\)。  
  
 當您呼叫 **Edit** 時，會儲存編輯緩衝區 \(目前的資料錄\) 中的資料錄。  預存的資料錄值可於稍後用來偵測是否有任何欄位變動。  
  
 在您呼叫 **Edit** 後，編輯緩衝區仍然代表目前的資料錄，但它此時已準備好接收欄位資料成員的變動。  若要變更資料錄，請手動地設定您希望編輯的任何欄位資料成員值。  除了對欄位指定實質的值外，您還可呼叫 `SetFieldNull` 來指定 Null 值。  若要認可您的變動，請呼叫 **Update**。  
  
> [!TIP]
>  若要離開 `AddNew` 或 **Edit** 模式，請以 **AFX\_MOVE\_REFRESH** 參數呼叫 **Move**。  
  
 呼叫 **Update** 的前提是資料錄集必須不是空值，且不能刪除目前的資料錄。  `IsBOF`、`IsEOF` 和 `IsDeleted` 應該都傳回 0。  
  
 當您為所編輯的資料錄呼叫 **Update** 時：  
  
-   若您的 ODBC 驅動程式支援 **::SQLSetPos** ODBC API 函式，MFC 會使用此函式來更新資料來源上的資料錄。  使用 **::SQLSetPos**，驅動程式會比較您的編輯緩衝區與伺服器上的資料錄間的一致性，若二者有差異則更新伺服器上的資料錄。  使用 **::SQLSetPos**，MFC 可更有效地更新資料錄，因為它不需要建構和處理 SQL 陳述式。  
  
     \-或\-  
  
-   如果不能使用 **::SQLSetPos**，MFC 會執行下列動作：  
  
    1.  若沒有做任何的變動，**Update** 不會做任何事並傳回 0。  
  
    2.  若有變動，**Update** 會建構一個 SQL **UPDATE** 陳述式。  列於 **UPDATE** 陳述式內的資料行是根據有變動到的欄位資料成員。  
  
    3.  **Update** 認可變更 ─ 執行 **UPDATE** 陳述式 ─ 便會變更資料來源上的資料錄，但若有交易正在處理中則不會認可變更 \(如需交易如何影響更新的詳細資訊，請參閱[交易：在一個資料錄集內執行交易 \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)\)。  ODBC 所保留的資料錄複本也會做變動。  
  
    4.  不像 `AddNew` 的處理程序，**Edit** 處理程序不會還原預存的資料錄。  編輯的資料錄仍然維持在目前資料錄的位置。  
  
    > [!CAUTION]
    >  當您呼叫 **Update** 來準備更新資料錄集時，請注意您的資料錄集包括了所有組成資料表主索引鍵的資料行 \(或資料表上任何唯一索引鍵的所有資料行，或足以識別唯一資料列的資料行\)。  在某些情況下，架構只能使用您在資料錄集內選取的資料行，以識別您的資料表需進行更新的資料錄。  資料表內的多筆資料錄不需要所有必要的資料行就可更新。  在這種情況下，架構會在您呼叫 **Update** 時擲回例外狀況。  
  
    > [!TIP]
    >  如果您在已經呼叫過 `AddNew` 或 **Edit** 其中一個函式後，又在呼叫 **Update** 之前再次呼叫它們，編輯緩衝區就會使用預存的資料錄來重新整理，取代正在處理的新資料錄或編輯資料錄。  這種行為給您一種取消 `AddNew` 或 **Edit** 並開始一個新的函式之方法：若您決定正在處理的資料錄有缺失，只要再呼叫一次 **Edit** 或 `AddNew` 即可。  
  
##  <a name="_core_deleting_a_record"></a> 刪除一筆資料錄  
 從資料錄集中刪除資料錄會涉及到捲動至該資料錄，以及呼叫資料錄集的 [Delete](../Topic/CRecordset::Delete.md) 成員函式。  不像 `AddNew` 和 **Edit**，**Delete** 並不需要配合 **Update** 呼叫。  
  
 呼叫 **Delete** 的前提是資料錄集必須是可更新的，且其必須在一筆資料錄上。  `CanUpdate`、`IsBOF`、`IsEOF` 和 `IsDeleted` 成員函式讓您可決定這些條件。  
  
 當您呼叫 **Delete** 時：  
  
-   若您的 ODBC 驅動程式支援 **::SQLSetPos** ODBC API 函式，MFC 會使用此函式來刪除資料來源上的資料錄。  使用 **::SQLSetPos** 通常比使用 SQL 更有效率。  
  
     \-或\-  
  
-   如果不能使用 **::SQLSetPos**，MFC 會執行下列動作：  
  
    1.  編輯緩衝區中的目前資料錄並不會像 `AddNew` 和 **Edit** 一樣進行備份。  
  
    2.  **Delete** 會建構移除資料錄的 SQL **DELETE** 陳述式。  
  
         編輯緩衝區內的目前資料錄不會像 `AddNew` 和 **Edit** 那樣預存。  
  
    3.  **Delete** 認可刪除動作 — 執行 **DELETE** 陳述式。  若資料錄是一個 ODBC 內的快照集，資料來源上的資料錄會標記為已刪除。  
  
    4.  已刪除的資料錄值仍然留在資料錄集的欄位資料成員內，但欄位資料成員已標記為 Null 且資料錄集的 `IsDeleted` 成員函式會傳回非零的值。  
  
    > [!NOTE]
    >  在刪除一筆資料錄後，您應該捲動至其他的資料錄，以便使用新資料錄內的資料來重填編輯緩衝區。  若再次呼叫 **Delete** 或呼叫 **Edit** 就會導致錯誤。  
  
 如需使用於更新作業的 SQL 陳述式的詳細資訊，請參閱 [SQL](../../data/odbc/sql.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：更多更新的詳細資訊 \(ODBC\)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)