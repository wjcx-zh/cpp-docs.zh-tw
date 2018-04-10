---
title: 資料錄集： AddNew、 Edit 和 Delete 的運作方式 (ODBC) |Microsoft 文件
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
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dbbf224797bd7d2eed2b085a6a7dd8eb1865de1c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明如何`AddNew`，**編輯**，和**刪除**類別成員函式`CRecordset`運作。 涵蓋的主題包括：  
  
-   [加入資料錄的方式運作](#_core_adding_a_record)  
  
-   [加入資料錄的可見性](#_core_visibility_of_added_records)  
  
-   [編輯資料錄的運作方式](#_core_editing_an_existing_record)  
  
-   [刪除資料錄的方式運作](#_core_deleting_a_record)  
  
> [!NOTE]
>  本主題適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 做為程式庫，您可能想要讀取[資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)，用來描述 RFX 在更新作業中的對應角色。  
  
##  <a name="_core_adding_a_record"></a>加入資料錄  

 將新的記錄加入至資料錄集需要呼叫資料錄集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成員函式，設定新的記錄欄位資料成員的值，然後呼叫[更新](../../mfc/reference/crecordset-class.md#update)来寫入的成員函式資料來源記錄。  
  
 呼叫的前提`AddNew`，資料錄集必須不已經開啟為唯讀。 `CanUpdate`和`CanAppend`成員函式可讓您判斷這些條件。  
  
 當您呼叫`AddNew`:  
  
-   編輯緩衝區中的記錄會儲存，因此可以還原其內容，如果在作業取消。  
  
-   欄位資料成員都會標記，因此可以稍後在它們偵測到變更。 欄位資料成員也會標記為清除 （未變更） 並設為 Null。  
  
 在您呼叫後`AddNew`、 編輯緩衝區代表新增、 清空記錄，備妥可先填入這些值。 若要這樣做，您手動設定的值指派給它們。 而不是指定欄位的值是實際資料，您可以呼叫`SetFieldNull`指定 Null 值。  
  
 若要認可您的變更，請呼叫**更新**。 當您呼叫**更新**新記錄：  
  
-   如果您的 ODBC 驅動程式支援**:: SQLSetPos** ODBC API 函式，MFC 會使用函式在資料來源上加入記錄。 與**:: SQLSetPos**，MFC 可以更有效率地將記錄，因為沒有建構及處理 SQL 陳述式。  
  
-   如果**:: SQLSetPos**不能使用，MFC 會進行下列作業：  
  
    1.  如果偵測不到任何變更，**更新**不做任何動作，並傳回 0。  
  
    2.  如有變更，**更新**建構 SQL**插入**陳述式。 表示所有已變更的欄位資料成員的資料行會列在**插入**陳述式。 若要強制包含的資料行，請呼叫[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成員函式：  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **更新**認可新的記錄 —**插入**陳述式執行和記錄已認可至資料來源 （和資料錄集，如果不是快照集） 的資料表，除非交易正在進行中。  
  
    4.  預存的記錄會還原至編輯緩衝區。 前記錄`AddNew`呼叫是目前無論再次**插入**成功地執行陳述式。  
  
    > [!TIP]
    >  完整控制的新記錄，執行下列方法： 設定的任何欄位，將會有值，並明確地設定所有的欄位也會藉由呼叫保留 Null 值`SetFieldNull`欄位和參數的指標與**，則為 TRUE** （預設值）。 如果您想要確保資料不會寫入資料來源，呼叫`SetFieldDirty`欄位和參數的指標與**FALSE**，且切勿修改欄位的值。 若要判斷欄位是否可為 Null，請呼叫`IsFieldNullable`。  
  
    > [!TIP]
    >  若要偵測資料錄集的資料成員的值變更時，MFC 會使用**PSEUDO_NULL**適用於每個您可以儲存在資料錄集的資料類型值。 如果您必須明確將欄位設定為**PSEUDO_NULL**值和欄位發生的狀況已標記為 Null，您必須也呼叫`SetFieldNull`，第一個參數中的欄位的位址傳遞和**FALSE**第二個參數中。  
  
##  <a name="_core_visibility_of_added_records"></a>加入資料錄的可見性  
 何時加入一筆記錄都可以看到資料錄集的？ 加入的資料錄有時顯示，有時也看不見，視兩件事而定：  
  
-   驅動程式都可以。  
  
-   架構可以利用。  
  
 如果您的 ODBC 驅動程式支援**:: SQLSetPos** ODBC API 函式，MFC 會使用函式加入記錄。 與**:: SQLSetPos**，加入記錄會顯示任何可更新的 MFC 資料錄集。 不支援此函式，加入記錄不會顯示，您必須呼叫**Requery**看到它們。 使用**:: SQLSetPos**也會更有效率。  
  
##  <a name="_core_editing_an_existing_record"></a>編輯現有的記錄  
 編輯資料錄集中的現有記錄包含捲動至資料錄，呼叫資料錄集的[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式，設定新的記錄欄位資料成員的值，然後呼叫[更新](../../mfc/reference/crecordset-class.md#update)成員函式，將已變更的記錄寫入資料來源。  
  
 呼叫的前提**編輯**，資料錄集必須是可更新，以及上一筆記錄。 `CanUpdate`和`IsDeleted`成員函式可讓您判斷這些條件。 目前的記錄也必須已經有尚未刪除，而且必須有記錄中資料錄集 (兩者`IsBOF`和`IsEOF`傳回 0)。  
  
 當您呼叫**編輯**，編輯緩衝區 （目前的記錄） 中的記錄會儲存。 預存的資料錄值稍後用來偵測是否已變更的任何欄位。  
  
 在您呼叫後**編輯**，編輯緩衝區仍代表目前的記錄，但現在已準備好接受變更的欄位資料成員。 若要變更記錄，您可以手動設定任何您想要編輯的欄位資料成員的值。 而不是指定欄位的值是實際資料，您可以呼叫`SetFieldNull`指定 Null 值。 若要認可變更，請呼叫**更新**。  
  
> [!TIP]
>  若要利用`AddNew`或**編輯**模式，請呼叫**移動**搭配參數**AFX_MOVE_REFRESH**。  
  
 呼叫的前提**更新**、 資料錄集必須為空白，且必須尚未刪除為目前的記錄。 `IsBOF``IsEOF`，和`IsDeleted`所有應該會傳回 0。  
  
 當您呼叫**更新**已編輯的記錄：  
  
-   如果您的 ODBC 驅動程式支援**:: SQLSetPos** ODBC API 函式，MFC 會使用函式來更新資料來源上的記錄。 與**:: SQLSetPos**，驅動程式會比較您的編輯緩衝區，以更新伺服器上的記錄，如果兩個不同的伺服器上對應的記錄。 與**:: SQLSetPos**，MFC 可以更有效率地更新的記錄，因為沒有建構及處理 SQL 陳述式。  
  
     -或-  
  
-   如果**:: SQLSetPos**不能使用，MFC 會進行下列作業：  
  
    1.  如果不已有任何變更，**更新**不做任何動作，並傳回 0。  
  
    2.  如有變更，**更新**建構 SQL**更新**陳述式。 列出的資料行**更新**陳述式會根據已變更的欄位資料成員。  
  
    3.  **更新**認可的變更 — 執行**更新**陳述式，並在資料來源，則變更記錄，但未認可的交易如果正在進行中 (請參閱[交易： 執行中的交易資料錄集 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)異動如何影響更新的相關資訊)。 ODBC 會保留一份記錄，其索引也會變更。  
  
    4.  程序不同`AddNew`、**編輯**程序不會還原預存的記錄。 編輯記錄會保留在目前的記錄的位置。  
  
    > [!CAUTION]
    >  當您準備好要呼叫來更新資料錄集**更新**，小心資料錄集，包含構成資料表的主索引鍵的所有資料行 （或所有資料行的任何唯一索引的資料表，或足夠的資料行唯一識別資料列）。 在某些情況下，此架構可以使用選取資料錄集中的資料行來識別您要更新的資料表中的記錄。 沒有所有必要的資料行，可能會在資料表中更新多筆記錄。 在此情況下，架構就會擲回例外狀況呼叫時**更新**。  
  
    > [!TIP]
    >  如果您呼叫`AddNew`或**編輯**之後之前，但您之前在呼叫其中一個函式呼叫**更新**，編輯緩衝區重新整理的預存的記錄，取代中的新增或編輯資料錄進度。 此行為可讓您進行中止`AddNew`或**編輯**並開始新的： 如果您判斷在進行記錄錯誤，只需呼叫**編輯**或`AddNew`一次。  
  
##  <a name="_core_deleting_a_record"></a>刪除記錄  
 捲動至資料錄，然後呼叫資料錄集的資料錄集中刪除資料錄的牽涉到[刪除](../../mfc/reference/crecordset-class.md#delete)成員函式。 不同於`AddNew`和**編輯**，**刪除**不需要符合呼叫**更新**。  
  
 呼叫的前提**刪除**，必須是可更新的資料錄集，而且它必須是記錄上。 `CanUpdate`， `IsBOF`， `IsEOF`，和`IsDeleted`成員函式可讓您判斷這些條件。  
  
 當您呼叫**刪除**:  
  
-   如果您的 ODBC 驅動程式支援**:: SQLSetPos** ODBC API 函式，MFC 會使用函式刪除資料來源上的記錄。 使用**:: SQLSetPos**通常比使用 SQL 更有效率。  
  
     -或-  
  
-   如果**:: SQLSetPos**不能使用，MFC 會進行下列作業：  
  
    1.  編輯緩衝區中目前的記錄不會備份在`AddNew`和**編輯**。  
  
    2.  **刪除**建構 SQL**刪除**移除記錄的陳述式。  
  
         編輯緩衝區中目前的記錄不會儲存為在`AddNew`和**編輯**。  
  
    3.  **刪除**認可刪除 — 執行**刪除**陳述式。 記錄會標示為已刪除資料來源上，如果記錄快照集，在 ODBC 中。  
  
    4.  已刪除的記錄值仍位於欄位資料成員的資料錄集，但是標示 Null 和資料錄集的欄位資料成員`IsDeleted`成員函式會傳回非零值。  
  
    > [!NOTE]
    >  之後刪除記錄，您應該捲動到另一筆記錄，到重新與新的記錄資料的編輯緩衝區填滿。 它會呼叫錯誤**刪除**一次或呼叫**編輯**。  
  
 在更新作業中使用的 SQL 陳述式的相關資訊，請參閱[SQL](../../data/odbc/sql.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 更新的詳細資訊 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)