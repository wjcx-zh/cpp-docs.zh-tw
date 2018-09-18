---
title: 資料錄集： AddNew、 Edit 和 Delete 運作方式 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4f15e593300c45cf5bbc24b85eacee107dafca58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052227"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)

本主題適用於 MFC ODBC 類別。  
  
本主題說明如何`AddNew`， `Edit`，並`Delete`類別成員函式`CRecordset`運作。 涵蓋的主題包括：  
  
- [加入資料錄的方式運作](#_core_adding_a_record)  
  
- [加入資料錄的可見性](#_core_visibility_of_added_records)  
  
- [編輯記錄的運作方式](#_core_editing_an_existing_record)  
  
- [刪除資料錄的方式運作](#_core_deleting_a_record)  
  
> [!NOTE]
>  本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
項目，您可能想要閱讀[資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)，其中描述 RFX 更新作業中的對應角色。  
  
##  <a name="_core_adding_a_record"></a> 新增記錄  

將新記錄新增至資料錄集需要呼叫資料錄集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成員函式，設定新的記錄欄位資料成員值，然後呼叫[更新](../../mfc/reference/crecordset-class.md#update)来寫入的成員函式資料來源記錄。  
  
為呼叫的前置條件`AddNew`，資料錄集必須未開啟為唯讀。 `CanUpdate`和`CanAppend`成員函式可讓您判斷這些條件。  
  
當您呼叫`AddNew`:  
  
- 儲存編輯緩衝區中的記錄，以便在作業取消時，就可以還原其內容。  
  
- 因此可以稍後在其中偵測變更，就會標示的欄位資料成員。 欄位資料成員也會標記為清除 （未變更） 並設為 Null。  
  
在您呼叫後`AddNew`、 編輯緩衝區表示新的、 空的記錄，準備好要被填入值。 若要這樣做，您手動設定的值指派給他們。 除了指定欄位的值是實際的資料，您可以呼叫`SetFieldNull`指定 Null 值。  
  
若要認可變更，請呼叫`Update`。 當您呼叫`Update`新記錄：  
  
- 如果您的 ODBC 驅動程式支援`::SQLSetPos`ODBC API 函式，MFC 會使用函式在資料來源上加入記錄。 使用`::SQLSetPos`，MFC 可以更有效率地將記錄，因為它並沒有建構來處理 SQL 陳述式。  
  
- 如果`::SQLSetPos`無法使用，MFC 會進行下列作業：  
  
    1.  如果偵測不到任何變更，`Update`不執行任何動作且會傳回 0。  
  
    2.  如果有變更，`Update`建構 SQL**插入**陳述式。 代表所有已變更的欄位資料成員的資料行所示**插入**陳述式。 若要強制包含的資料行，請呼叫[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成員函式：  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  `Update` 認可新的記錄 —**插入**陳述式，並記錄會認可到資料來源 （和資料錄集，如果不是快照集） 上的資料表，除非交易正在進行中。  
  
    4.  預存的記錄會還原至編輯緩衝區。 之前為目前的資料錄`AddNew`呼叫是目前不論再次**插入**成功地執行陳述式。  
  
    > [!TIP]
    >  新記錄的完整控制權，需要下列方法： 設定的任何欄位，會有值，然後明確地設定會保持為 Null，藉由呼叫的任何欄位值`SetFieldNull`欄位和參數的指標，則為 TRUE （預設值）。 如果您想要確保欄位不會寫入資料來源，而呼叫`SetFieldDirty`指標的欄位和參數為 FALSE，並不會修改該欄位的值。 若要判斷欄位是否可為 Null，請呼叫`IsFieldNullable`。  
  
    > [!TIP]
    >  若要偵測值的資料錄集的資料成員變更時，MFC 會使用 PSEUDO_NULL 值適用於每個您可以儲存在資料錄集的資料類型。 如果您必須明確設定為 PSEUDO_NULL 值的欄位和欄位發生已標記為 Null，您還必須呼叫`SetFieldNull`，第二個參數中傳遞的位址欄位的第一個參數和 FALSE。  
  
##  <a name="_core_visibility_of_added_records"></a> 加入資料錄的可見性  

何時會加入一筆記錄顯示您的資料錄集？ 新增的記錄有時顯示，有時並不可見的取決於兩件事：  
  
- 支援的驅動程式。  
  
- 何種架構可以利用。  
  
如果您的 ODBC 驅動程式支援`::SQLSetPos`ODBC API 函式，MFC 會使用函式新增記錄。 使用`::SQLSetPos`，加入記錄會顯示任何可更新的 MFC 資料錄集。 如果不支援此函式，新增記錄不會顯示，而且您必須呼叫`Requery`若要查看它們。 使用`::SQLSetPos`也會更有效率。  
  
##  <a name="_core_editing_an_existing_record"></a> 編輯現有的記錄  

向下捲動到 筆記錄，並呼叫資料錄集的編輯中資料錄集的現有記錄涉及[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式，設定新的記錄欄位資料成員值，並呼叫[更新](../../mfc/reference/crecordset-class.md#update)成員函式已變更的記錄寫入至資料來源。  
  
為呼叫的前置條件`Edit`，資料錄集必須是可更新與上一筆記錄。 `CanUpdate`和`IsDeleted`成員函式可讓您判斷這些條件。 目前的記錄也必須已經有尚未刪除，而且必須有記錄在資料錄集 (兩者`IsBOF`和`IsEOF`傳回 0)。  
  
當您呼叫`Edit`，編輯緩衝區 （目前的記錄） 中的記錄會儲存。 預存的資料錄值稍後會用來偵測是否已變更的任何欄位。  
  
在您呼叫後`Edit`，編輯緩衝區仍代表目前的記錄，但現在已準備好接受變更的欄位資料成員。 若要變更記錄，您可以手動設定任何您想要編輯的欄位資料成員的值。 除了指定欄位的值是實際的資料，您可以呼叫`SetFieldNull`指定 Null 值。 若要認可您的變更，請呼叫`Update`。  
  
> [!TIP]
>  若要如何利用`AddNew`或是`Edit`模式中，呼叫`Move`搭配參數*AFX_MOVE_REFRESH*。  
  
為呼叫的前置條件`Update`、 資料錄集必須為空白，且必須尚未刪除目前的記錄。 `IsBOF``IsEOF`，和`IsDeleted`所有應該會傳回 0。  
  
當您呼叫`Update`已編輯的記錄：  
  
- 如果您的 ODBC 驅動程式支援`::SQLSetPos`ODBC API 函式，MFC 會使用函式來更新資料來源上的記錄。 使用`::SQLSetPos`，驅動程式會比較您的編輯緩衝區與更新的伺服器上的記錄，如果兩個不同的伺服器上對應的記錄。 使用`::SQLSetPos`，MFC 可以更有效率地更新的記錄，因為它並沒有建構來處理 SQL 陳述式。  
  
     -或-  
  
- 如果`::SQLSetPos`無法使用，MFC 會進行下列作業：  
  
    1.  如果不已有任何變更，`Update`不執行任何動作且會傳回 0。  
  
    2.  如果有變更，`Update`建構 SQL**更新**陳述式。 列出的資料行**更新**陳述式會根據已變更的欄位資料成員。  
  
    3.  `Update` 認可的變更 — 執行**更新**陳述式，並記錄變更資料來源，但未認可的交易如果正在進行中 (請參閱[交易： 執行異動中的資料錄集 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)如需有關交易如何影響更新資訊)。 ODBC 會保留一份記錄，也會變更。  
  
    4.  不同的程序`AddNew`，則`Edit`程序不會還原儲存的記錄。 已編輯的記錄會保留在位置中，為目前的記錄。  
  
    > [!CAUTION]
    >  當您準備好要呼叫來更新資料錄集`Update`，處理資料錄集，包含組成資料表 （或所有資料表，任何唯一索引或足夠的資料行可唯一識別資料列的資料行） 的主索引鍵的所有資料行。 在某些情況下，架構就可以使用只選取您的資料錄集中的資料行來識別您要更新的資料表中的記錄。 沒有所有必要的資料行，可能會在資料表中更新多筆記錄。 在此情況下，架構就會擲回例外狀況呼叫`Update`。  
  
    > [!TIP]
    >  如果您呼叫`AddNew`或是`Edit`之前，但您之前在呼叫其中一個函式之後呼叫`Update`，編輯緩衝區會重新整理的預存的記錄，取代進行中的新的或修改的記錄。 此行為可讓您用來在中止`AddNew`或`Edit`，並開始新的： 如果您判斷在進行記錄錯誤，只要呼叫`Edit`或`AddNew`一次。  
  
##  <a name="_core_deleting_a_record"></a> 刪除記錄  

向下捲動到 筆記錄，然後呼叫資料錄集的刪除記錄集的資料錄涉及[刪除](../../mfc/reference/crecordset-class.md#delete)成員函式。 不同於`AddNew`並`Edit`，`Delete`不需要呼叫`Update`。  
  
為呼叫的前置條件`Delete`、 資料錄集必須能夠更新，而且它必須是上一筆記錄。 `CanUpdate`， `IsBOF`， `IsEOF`，和`IsDeleted`成員函式可讓您判斷這些條件。  
  
當您呼叫`Delete`:  
  
- 如果您的 ODBC 驅動程式支援`::SQLSetPos`ODBC API 函式，MFC 會使用函式刪除資料來源上的記錄。 使用`::SQLSetPos`通常更有效率，比使用 SQL。  
  
     -或-  
  
- 如果`::SQLSetPos`無法使用，MFC 會進行下列作業：  
  
    1.  編輯緩衝區中目前的記錄不會備份示`AddNew`和`Edit`。  
  
    2.  `Delete` 建構 SQL**刪除**移除記錄的陳述式。  
  
         編輯緩衝區中目前的記錄不會儲存為在`AddNew`和`Edit`。  
  
    3.  `Delete` 認可刪除，執行**刪除**陳述式。 記錄會標示為已刪除資料來源上，如果記錄是在 ODBC 中的快照集。  
  
    4.  已刪除資料錄的值仍然會在欄位資料成員的資料錄集，但欄位資料成員會標示為 Null，而且資料錄集的`IsDeleted`成員函式傳回非零值。  
  
    > [!NOTE]
    >  之後刪除記錄，您應該捲動到重新填滿新資料錄的資料與編輯緩衝區的另一筆記錄。 它會呼叫錯誤`Delete`一次，或呼叫`Edit`。  
  
在更新作業中使用的 SQL 陳述式的相關資訊，請參閱[SQL](../../data/odbc/sql.md)。  
  
## <a name="see-also"></a>另請參閱  

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：更多更新的詳細資訊 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)