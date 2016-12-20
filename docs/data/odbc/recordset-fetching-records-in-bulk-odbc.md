---
title: "資料錄集：擷取大量資料錄 (ODBC) | Microsoft Docs"
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
  - "大量資料錄欄位交換"
  - "大量 RFX 函式"
  - "大量資料列擷取"
  - "大量資料列擷取, 實作"
  - "DoBulkFieldExchange 方法"
  - "擷取大量 ODBC 資料錄"
  - "ODBC 資料錄集, 大量資料列擷取"
  - "資料錄集, 大量資料列擷取"
  - "RFX (ODBC), 大量"
  - "RFX (ODBC), 大量資料列擷取"
  - "資料列集, 大量資料列擷取"
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：擷取大量資料錄 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 `CRecordset` 類別提供支援大量資料列擷取，這意謂使用單一擷取就可一次擷取多筆資料錄，而不是從資料來源一次擷取一筆資料錄。  您只能在 `CRecordset` 衍生的類別內實作大量資料列擷取。  從資料來源傳送資料至資料錄集物件的處理過程就稱為大量資料錄欄位交換 \(Bulk RFX\)。  請注意，若您不是在 `CRecordset` 衍生的類別內使用大量資料列擷取，此資料會經由資料錄欄位交換 \(RFX\) 來傳送。  如需詳細資訊，請參閱[資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)。  
  
 這個主題說明：  
  
-   [CRecordset 如何支援大量資料列擷取](#_core_how_crecordset_supports_bulk_row_fetching)。  
  
-   [使用大量資料列擷取時的某些特殊考量](#_core_special_considerations)。  
  
-   [如何實作大量資料列欄位交換](#_core_how_to_implement_bulk_record_field_exchange)。  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> CRecordset 如何支援大量資料列擷取  
 在開啟您的資料錄集物件前，您可使用 `SetRowsetSize` 成員函式來定義資料列集大小。  資料列集大小指出一個單一擷取應擷取多少筆資料錄。  在實作大量資料列擷取時，預設的資料列集大小是 25。  如果沒有實作大量資料列擷取，資料列集大小會固定保持在 1。  
  
 在您將資料列集大小初始化後，會呼叫 [Open](../Topic/CRecordset::Open.md) 成員函式。  您必須在這裡指定 **dwOptions** 參數的 `CRecordset::useMultiRowFetch` 選項，以實作大量資料列擷取。  您可另外設定 **CRecordset::userAllocMultiRowBuffers** 選項。  大量資料錄欄位交換機制使用陣列來儲存一次擷取中取得的多筆資料列。  架構 \(Framework\) 會自動地配置這些儲存緩衝區，或您也可以手動地配置它們。  指定 **CRecordset::userAllocMultiRowBuffers** 選項意謂您要自己配置。  
  
 下表列出 `CRecordset` 為了支援大量資料列擷取所提供的成員函式。  
  
|成員函式|說明|  
|----------|--------|  
|[CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)|處理所有在擷取時發生的錯誤之虛擬函式 \(Virtual Function\)。|  
|[DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)|實作大量資料錄欄位交換。  自動呼叫以便從資料來源傳送多筆資料列至資料錄集物件。|  
|[GetRowsetSize](../Topic/CRecordset::GetRowsetSize.md)|擷取資料列集大小目前的設定。|  
|[GetRowsFetched](../Topic/CRecordset::GetRowsFetched.md)|告知執行一個擷取後實際上取得多少資料列。  在大多數情況下，這會是資料列集大小，除非有擷取到未完成的資料列集。|  
|[GetRowStatus](../Topic/CRecordset::GetRowStatus.md)|傳回一個資料列集內特定資料列的擷取狀態。|  
|[RefreshRowset](../Topic/CRecordset::RefreshRowset.md)|重新整理資料列集內特定資料列的資料和狀態。|  
|[SetRowsetCursorPosition](../Topic/CRecordset::SetRowsetCursorPosition.md)|移動資料指標 \(Cursor\) 至資料列集內的特定資料列。|  
|[SetRowsetSize](../Topic/CRecordset::SetRowsetSize.md)|變更資料列集大小設定值為指定數值的虛擬函式。|  
  
##  <a name="_core_special_considerations"></a> 特殊考量  
 雖然大量資料列擷取可增進效能，但在某些運作中仍有功能上的差異性。  在您決定實作大量資料列擷取前，請考量下列因素：  
  
-   架構會自動呼叫 `DoBulkFieldExchange` 成員函式，以將資料從資料來源傳送至資料錄集物件。  然而，資料不會從資料錄集回傳至資料來源。  呼叫 `AddNew`、**Edit**、**Delete** 或 **Update** 成員函式會導致提示失敗。  雖然 `CRecordset` 類別目前並未提供更新大量資料列的機制，但是您可以使用 ODBC API 函式 **SQLSetPos** 來撰寫自己的函式。  如需 **SQLSetPos** 的詳細資訊，請參閱 MSDN 文件內的＜ODBC SDK 程式設計人員參考＞。  
  
-   實作大量資料列擷取的資料錄集不能使用 `IsDeleted`、`IsFieldDirty`、`IsFieldNull`、`IsFieldNullable`、`SetFieldDirty` 和 `SetFieldNull` 成員函式。  然而，您可呼叫 `GetRowStatus` 來取代 `IsDeleted`，以及呼叫 `GetODBCFieldInfo` 來取代 `IsFieldNullable`。  
  
-   **Move** 作業將使用資料列集來重新調整資料錄集的位置。  例如，假設您開啟擁有 100 個資料錄且初始資料列集大小為 10 的資料錄集。  當目前的資料錄是位於列 1 時，**Open** 會擷取資料列 1 到 10。  呼叫 `MoveNext` 將會擷取下一個資料列集，而不是下一個資料列。  此資料列集是由列 11 到列 20 所組成，且目前的資料錄是位於列 11。  請注意，實作大量資料列擷取時，`MoveNext` 並不相當於 **Move\( 1 \)**。  **Move\( 1 \)** 將會從目前資料錄的下一列開始擷取資料列集。  在這個範例中，在呼叫 **Open** 後再呼叫 **Move\( 1 \)**，會擷取到的資料列集包含有列 2 到列 11，且目前的資料錄是位於列 2。  如需詳細資訊，請參閱 [Move](../Topic/CRecordset::Move.md) 成員函式。  
  
-   與資料錄欄位交換不同的是，精靈並不支援大量資料錄欄位交換。  這意謂您必須手動宣告欄位資料成員，並編寫 Bulk RFX 函式的呼叫，以手動方式覆寫 `DoBulkFieldExchange`。  如需詳細資訊，請參閱在《類別庫參考》中的[資料錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> 如何實作大量資料列欄位交換  
 大量資料錄欄位交換會將一資料列集資料由資料來源傳送至資料錄集物件。  Bulk RFX 函式使用陣列來儲存此資料，正如陣列儲存資料列集中每個資料項目的長度。  在您的類別定義中，您必須將欄位資料成員定義為存取陣列資料的指標。  除此之外，您必須定義一組指標來存取陣列的長度。  所有的參數資料成員都不該宣告為指標；在使用大量資料錄欄位交換時與使用資料錄欄位交換時所宣告的參數資料成員是相同的。  下列程式碼示範一個簡易範例：  
  
```  
class MultiRowSet : public CRecordset  
{  
public:  
   // Field/Param Data  
      // field data members  
      long* m_rgID;  
      LPSTR m_rgName;  
  
      // pointers for the lengths  
      // of the field data  
      long* m_rgIDLengths;  
      long* m_rgNameLengths;  
  
      // input parameter data member  
      CString m_strNameParam;  
  
   .  
   .  
   .  
}  
```  
  
 您可手動配置這些儲存緩衝區，或讓架構來進行配置工作。  若要自行配置緩衝區，您必須指定 **Open** 成員函式 **dwOptions** 參數的 **CRecordset::userAllocMultiRowBuffers** 選項。  請確定陣列的大小設定至少與資料列集大小相等。  如果希望由架構來進行配置工作，您應該將指標的初始值設為 **NULL**。通常這會由資料錄集物件的建構函式完成：  
  
```  
MultiRowSet::MultiRowSet( CDatabase* pDB )  
   : CRecordset( pDB )  
{  
   m_rgID = NULL;  
   m_rgName = NULL;  
   m_rgIDLengths = NULL;  
   m_rgNameLengths = NULL;  
   m_strNameParam = "";  
  
   m_nFields = 2;  
   m_nParams = 1;  
  
   .  
   .  
   .  
}  
```  
  
 最後，您必須覆寫 `DoBulkFieldExchange` 成員函式。  對欄位資料成員呼叫 Bulk RFX 函式；對任何參數資料成員呼叫 RFX 函式。  如果您藉由傳遞 SQL 陳述式或預存程序至 **Open** 來開啟資料錄集，則建立 Bulk RFX 呼叫的順序必須與資料錄集內的資料行順序一致，同樣地，參數的 RFX 呼叫順序必須與 SQL 陳述式或預存程序內的參數順序相對應。  
  
```  
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )  
{  
   // call the Bulk RFX functions  
   // for field data members  
   pFX->SetFieldType( CFieldExchange::outputColumn );  
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),  
                  &m_rgID, &m_rgIDLengths );  
   RFX_Text_Bulk( pFX, _T( "[colName]" ),  
                  &m_rgName, &m_rgNameLengths, 30 );  
  
   // call the RFX functions for  
   // for parameter data members  
   pFX->SetFieldType( CFieldExchange::inputParam );  
   RFX_Text( pFX, "NameParam", m_strNameParam );  
}  
```  
  
> [!NOTE]
>  您必須在 `CRecordset` 衍生類別離開範圍前呼叫 **Close** 成員函式。  如此能確保釋放架構所配置的任何記憶體。  不論您是否有實作大量資料列擷取，永遠保持明確呼叫 **Close** 是良好的程式設計作法。  
  
 如需資料錄欄位交換 \(RFX\) 的詳細資訊，請參閱[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  如需使用參數的詳細資訊，請參閱 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md) 和[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m\_nFields](../Topic/CRecordset::m_nFields.md)   
 [CRecordset::m\_nParams](../Topic/CRecordset::m_nParams.md)