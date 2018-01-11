---
title: "資料錄集： 擷取大量 (ODBC) 資料錄 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8d9738af557cb8d4dd26b792851f8be276e91380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>資料錄集：擷取大量資料錄 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 類別`CRecordset`提供支援大量資料列擷取，這是指多筆記錄可以擷取一次在單一的擷取，而不是擷取一筆資料錄一次從資料來源。 您可以實作大量資料列擷取，僅在衍生`CRecordset`類別。 將資料從資料來源傳送到資料錄集物件的程序稱為大量資料錄欄位交換 (Bulk RFX)。 請注意，如果您沒有使用中的大量資料列擷取`CRecordset`-衍生的類別中，資料透過資料錄欄位交換 (RFX) 傳送。 如需詳細資訊，請參閱[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
 本主題說明：  
  
-   [CRecordset 如何支援大量資料列擷取](#_core_how_crecordset_supports_bulk_row_fetching)。  
  
-   [當使用一些特殊考量大量資料列擷取](#_core_special_considerations)。  
  
-   [如何實作大量資料錄欄位交換](#_core_how_to_implement_bulk_record_field_exchange)。  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a>CRecordset 如何支援大量資料列擷取  
 在開啟之前資料錄集物件，您可以定義資料列集大小，以及`SetRowsetSize`成員函式。 資料列集大小指定應該在單一擷取期間擷取的多少筆記錄。 實作大量資料列擷取時，預設資料列集大小為 25。 如果未實作大量資料列擷取，資料列集大小會保持固定在 1。  
  
 在您初始化資料列集大小之後，請呼叫[開啟](../../mfc/reference/crecordset-class.md#open)成員函式。 您必須在這裡指定`CRecordset::useMultiRowFetch`選項**dwOptions**實作大量資料列擷取的參數。 您可以另外設定**CRecordset::userAllocMultiRowBuffers**選項。 大量資料錄欄位交換機制使用陣列來儲存多個提取時擷取的資料列。 這些儲存緩衝區可由架構自動配置，或手動配置。 指定**CRecordset::userAllocMultiRowBuffers**選項表示您將進行配置。  
  
 下表列出所提供的成員函式`CRecordset`以支援大量資料列擷取。  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|虛擬函式處理期間提取發生的任何錯誤。|  
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|實作大量資料錄欄位交換。 自動呼叫傳輸多個資料列從資料來源的資料錄集物件。|  
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|擷取資料列集大小的目前設定。|  
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|會告知實際上在給定提取之後擷取多少資料列。 在大部分情況下，這會是資料列集大小，除非您已存取不完整的資料列集。|  
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|傳回一個資料列集內的特定資料列的擷取狀態。|  
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|重新整理的資料和狀態資料列集內的特定資料列。|  
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|將游標移至 資料列集內的特定資料列。|  
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|虛擬函式變更資料列集大小設定為指定的值。|  
  
##  <a name="_core_special_considerations"></a>特殊考量  
 雖然大量資料列擷取為效能改善，某些功能以不同的方式運作。 您決定實作大量資料列擷取之前，請考慮下列各項：  
  
-   架構會自動呼叫`DoBulkFieldExchange`成員函式，將資料來源的資料傳送至資料錄集物件。 不過，未傳送資料集的資料錄回資料來源。 呼叫`AddNew`，**編輯**，**刪除**，或**更新**成員函式會導致失敗的判斷提示。 雖然`CRecordset`目前不提供一個機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式**SQLSetPos**。 如需有關**SQLSetPos**，請參閱*ODBC SDK 程式設計人員參考*MSDN 文件中。  
  
-   成員函式`IsDeleted`， `IsFieldDirty`， `IsFieldNull`， `IsFieldNullable`， `SetFieldDirty`，和`SetFieldNull`不能在實作大量資料列擷取的資料錄集。 不過，您可以呼叫`GetRowStatus`取代`IsDeleted`，和`GetODBCFieldInfo`取代`IsFieldNullable`。  
  
-   **移動**作業重新由資料列集定位資料錄集。 例如，假設您開啟具有 10 的初始資料列集大小的 100 筆記錄的資料錄集。 **開啟**會提取資料列 1 到 10，與目前位於資料列 1 的記錄。 呼叫`MoveNext`提取下一個資料列集，不下一個資料列。 此資料列集是由資料列 11 到 20，與目前的記錄放在資料列 11 所組成。 請注意，`MoveNext`和**移動 (1)**實作大量資料列擷取時，並不相等。 **移動 (1)**提取開始 1 個資料列與目前記錄的資料列集。 在此範例中，呼叫**移動 (1)**之後呼叫**開啟**提取資料列集包含的資料列到 11，2，與目前位於資料列 2 的記錄。 如需詳細資訊，請參閱[移動](../../mfc/reference/crecordset-class.md#move)成員函式。  
  
-   不同於資料錄欄位交換精靈並不支援大量資料錄欄位交換。 這表示您必須以手動方式宣告將欄位資料成員，並以手動方式覆寫`DoBulkFieldExchange`撰寫 Bulk RFX 函式的呼叫。 如需詳細資訊，請參閱[資料錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)中*類別庫參考*。  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a>如何實作大量資料錄欄位交換  
 大量資料錄欄位交換會傳輸至資料錄集物件從資料來源的資料列集資料。 大量 RFX 函式會使用陣列來儲存此資料，以及陣列來儲存資料列集中的每個資料項目的長度。 在類別定義中，您必須定義為指標存取陣列資料的欄位資料成員。 此外，您必須定義一組指標來存取陣列的長度。 任何參數的資料成員不應該宣告為指標。宣告參數資料成員時使用大量資料錄欄位交換等同於使用資料錄欄位交換時宣告它們。 下列程式碼會示範一個簡單的範例：  
  
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
  
 您可以手動配置儲存體的緩衝區，或由架構進行配置。 若要自行配置的緩衝區，您必須指定**CRecordset::userAllocMultiRowBuffers**選項**dwOptions**中的參數**開啟**成員函式。 請務必設定至少等於資料列集大小的陣列的大小。 如果您想要讓架構進行配置，您應該將指標的初始值來**NULL。** 這通常是在資料錄集物件的建構函式：  
  
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
  
 最後，您必須覆寫`DoBulkFieldExchange`成員函式。 欄位的資料成員呼叫 Bulk RFX 函式。針對任何參數的資料成員呼叫 RFX 函式。 如果您藉由傳遞 SQL 陳述式或預存程序來開啟資料錄集**開啟**，資料錄集中的資料行必須對應於您在 Bulk RFX 呼叫的順序; 同樣地，RFX 的順序呼叫，參數必須對應於參數中的 SQL 陳述式或預存程序。  
  
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
>  您必須呼叫**關閉**之前您衍生的成員函式`CRecordset`類別超出範圍。 這可確保任何架構所配置的記憶體釋出。 良好的程式設計作法一律明確地呼叫**關閉**，不論您是否有實作大量資料列擷取。  
  
 如需有關資料錄欄位交換 (RFX) 的詳細資訊，請參閱[資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 如需有關如何使用參數的詳細資訊，請參閱[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)和[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)   
 [CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

