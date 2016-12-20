---
title: "資料錄集：加入、更新和刪除資料錄 (ODBC) | Microsoft Docs"
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
  - "資料錄編輯 [C++]"
  - "資料錄編輯 [C++], 在資料錄集中"
  - "資料錄 [C++], 加入"
  - "資料錄 [C++], 刪除"
  - "資料錄 [C++], 編輯"
  - "資料錄 [C++], 更新"
  - "資料錄集 [C++], 加入資料錄"
  - "資料錄集 [C++], 刪除資料錄"
  - "資料錄集 [C++], 編輯資料錄"
  - "資料錄集 [C++], 更新"
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：加入、更新和刪除資料錄 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
> [!NOTE]
>  您現在可以更有效地加入大量資料錄。  如需詳細資訊，請參閱[資料錄集：加入大量資料錄 \(ODBC\)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  如果您要使用大量資料列擷取，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 可更新的快照集和動態集讓您可加入、編輯 \(更新\) 和刪除資料錄。  這個主題說明：  
  
-   [如何判斷您的資料錄集是否為可更新的](#_core_determining_whether_your_recordset_is_updatable)  
  
-   [如何加入新資料錄](#_core_adding_a_record_to_a_recordset)  
  
-   [如何編輯現有資料錄](#_core_editing_a_record_in_a_recordset)  
  
-   [如何刪除資料錄](#_core_deleting_a_record_from_a_recordset)  
  
 如需如何執行更新以及您的更新如何顯示給其他使用者的詳細資訊，請參閱[資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  一般說來，當您加入、編輯或刪除資料錄時，資料錄集會立即變更資料來源。  您可以將相關更新以群組批次方式放至交易中。  若有一個交易正在處理中，則在您認可該交易前，更新都不會完成。  這讓您能取回或復原所做的變動。  如需交易的詳細資訊，請參閱[交易 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
 下表摘要中說明了不同更新特色的可用資料錄集選項。  
  
### 資料錄集讀取\/更新選項  
  
|型別|讀取|編輯資料錄|刪除資料錄|加入 \(附加\)|  
|--------|--------|-----------|-----------|---------------|  
|唯讀|Y|N|N|N|  
|僅能附加|Y|N|N|Y|  
|可完全更新|Y|Y|Y|Y|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> 決定您的資料錄集是否為可更新的  
 若資料來源是可更新的，則資料錄集物件也是可更新的，且您會將該資料錄集開啟成可更新的。  資料錄集的可更新性也會根據您使用的 SQL 陳述式、ODBC 驅動程式的功能以及 ODBC 資料指標程式庫是否在記憶體中而定。  您不能更新一個唯讀的資料錄集或資料來源。  
  
#### 若要判斷您的資料錄集是否為可更新的  
  
1.  呼叫資料錄集物件的 [Update](../Topic/CRecordset::CanUpdate.md) 成員函式。  
  
     `CanUpdate` 在資料錄集是可更新的情況下會傳回一個非零值。  
  
 資料錄集預設是可完全更新的 \(即您能夠執行 `AddNew`、**Edit** 和 **Delete** 作業\)。  但您也可使用 [appendOnly](../Topic/CRecordset::Open.md) 選項來開啟可更新的資料錄集。  用此方法來開啟的資料錄集只允許使用 `AddNew` 來附加新資料錄。  您無法編輯或刪除現有的資料錄。  您可藉由呼叫 [CanAppend](../Topic/CRecordset::CanAppend.md) 成員函式，來測試資料錄集是否只開啟為附加用途。  如果資料錄集是完全可更新的或只開啟供附加之用，`CanAppend` 會傳回非零的值。  
  
 下列程式碼展示您能如何對名為 `rsStudentSet` 的資料錄集物件使用 `CanUpdate`。  
  
```  
if( !rsStudentSet.Open( ) )  
    return FALSE;  
if( !rsStudentSet.CanUpdate( ) )  
{  
    AfxMessageBox( "Unable to update the Student recordset." );  
    return;  
}  
```  
  
> [!CAUTION]
>  當您準備呼叫 **Update** 來更新資料錄集時，請特別注意，您的資料錄集包括了組成資料表主索引鍵的所有資料行 \(或資料表上任何唯一索引的所有資料行\)。  在某些情況下，架構只能使用您在資料錄集內選取的資料行，以識別您的資料表需進行更新的資料錄。  若不具所有必要的資料行，資料表中可能會更新多筆資料錄，而損害資料表的參考完整性。  在這種情況下，架構會在您呼叫 **Update** 時擲回例外狀況。  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a> 在資料錄集中加入資料錄  
 如果資料錄集的 [CanAppend](../Topic/CRecordset::CanAppend.md) 成員函式傳回非零的值，您便加入新資料錄至資料錄集。  
  
#### 若要在資料錄集中加入一筆新資料錄  
  
1.  請先確定資料錄集是可附加的。  
  
2.  呼叫資料錄集物件的 [AddNew](../Topic/CRecordset::AddNew.md) 成員函式。  
  
     `AddNew` 會準備將資料錄集當成一個編輯緩衝區來使用。  所有欄位資料成員設定為特定值 Null，並且標記為不可變更的，如此當您呼叫 [Update](../Topic/CRecordset::Update.md) 時只有變更的 \(Dirty\) 值會寫入資料來源。  
  
3.  設定新資料錄的欄位資料成員值。  
  
     指定欄位資料成員值。  您沒有指派的就不會寫入至資料來源。  
  
4.  呼叫資料錄集物件的 **Update** 成員函式。  
  
     **Update** 會在資料來源中寫入新的資料錄，完成附加作業。  如需無法呼叫 **Update** 的詳細資訊，請參閱[資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 如需加入資料錄如何運作以及何時可在資料錄集內看到加入的資料錄的詳細資訊，請參閱[資料錄集：AddNew、Edit 和 Delete 的運作方式 \(ODBC\)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)。  
  
 下列範例說明了新資料錄的加入方式：  
  
```  
if( !rsStudent.Open( ) )  
    return FALSE;  
if( !rsStudent.CanAppend( ) )  
    return FALSE;                      // no field values were set  
rsStudent.AddNew( );  
rsStudent.m_strName = strName;  
rsStudent.m_strCity = strCity;  
rsStudent.m_strStreet = strStreet;  
if( !rsStudent.Update( ) )  
{  
    AfxMessageBox( "Record not added; no field values were set." );  
    return FALSE;  
}  
```  
  
> [!TIP]
>  若要取消 `AddNew` 或 **Edit** 呼叫，只要另外呼叫 `AddNew` 或 **Edit**，或使用 **AFX\_MOVE\_REFRESH** 參數呼叫 **Move**。  資料成員將重設回先前的值，且您仍會處於 **Edit** 或 **Add** 模式。  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a> 編輯資料錄集中的資料錄  
 如果資料錄集的 [CanUpdate](../Topic/CRecordset::CanUpdate.md) 成員函式傳回非零的值，您就可以編輯現有資料錄。  
  
#### 若要在資料錄集中編輯現有資料錄  
  
1.  確定資料錄集是可更新的。  
  
2.  捲動至您想要更新的資料錄。  
  
3.  呼叫資料錄集物件的 [Edit](../Topic/CRecordset::Edit.md) 成員函式。  
  
     **Edit** 會準備將資料錄集當成編輯緩衝區來使用。  所有欄位資料成員都會被標記，如此資料錄集便可在以後辨別這些成員是否有進行變動。  當您呼叫 [Update](../Topic/CRecordset::Update.md) 時，變動過的欄位資料成員的新值便會寫入資料來源。  
  
4.  設定新資料錄的欄位資料成員值。  
  
     指定欄位資料成員值。  您沒有指定值的項目會維持不變。  
  
5.  呼叫資料錄集物件的 **Update** 成員函式。  
  
     **Update** 會在資料來源中寫入變更的資料錄，完成編輯作業。  如需無法呼叫 **Update** 的詳細資訊，請參閱[資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
 當您編輯一筆資料錄後，編輯過的資料錄仍會維持目前的資料錄。  
  
 下列範例說明一個 **Edit** 作業。  其假設使用者已移動到其想要編輯的資料錄。  
  
```  
rsStudent.Edit( );  
rsStudent.m_strStreet = strNewStreet;  
rsStudent.m_strCity = strNewCity;  
rsStudent.m_strState = strNewState;  
rsStudent.m_strPostalCode = strNewPostalCode;  
if( !rsStudent.Update( ) )  
{  
    AfxMessageBox( "Record not updated; no field values were set." );  
    return FALSE;  
}  
```  
  
> [!TIP]
>  若要取消 `AddNew` 或 **Edit** 呼叫，只要另外呼叫 `AddNew` 或 **Edit**，或使用 **AFX\_MOVE\_REFRESH** 參數呼叫 **Move**。  資料成員將重設回先前的值，且您仍會處於 **Edit** 或 **Add** 模式。  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a> 從資料錄集中刪除資料錄  
 如果資料錄集的 [CanUpdate](../Topic/CRecordset::CanUpdate.md) 成員函式傳回非零的值，您就可以刪除資料錄。  
  
#### 若要刪除資料錄  
  
1.  確定資料錄集是可更新的。  
  
2.  捲動至您想要更新的資料錄。  
  
3.  呼叫資料錄集物件的 [Delete](../Topic/CRecordset::Delete.md) 成員函式。  
  
     **Delete** 會立即將資料錄標記為已刪除的，不論是在資料錄集內或在資料來源上。  
  
     不像 `AddNew` 和 **Edit**，**Delete** 沒有任何對應的 **Update** 呼叫。  
  
4.  捲動至其他資料錄。  
  
    > [!NOTE]
    >  在資料錄集中移動時，不會略過已刪除的資料錄。  如需詳細資訊，請參閱 [IsDeleted](../Topic/CRecordset::IsDeleted.md) 成員函式。  
  
 下列範例說明了一個 **Delete** 作業。  它假設使用者已移動至想要刪除的資料錄。  在呼叫 **Delete** 之後，移動至新的資料錄是重要的動作。  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 如需 `AddNew`、**Edit** 和 **Delete** 成員函式效果的詳細資訊，請參閱[資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：鎖定資料錄 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)