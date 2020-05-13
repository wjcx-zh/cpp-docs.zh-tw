---
title: 資料錄集：擷取大量資料錄 (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: ec4d83481f6335d4c40ffb8f004b617f2ee09c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367023"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>資料錄集：擷取大量資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

類`CRecordset`支援批量行提取,這意味著在單個提取期間可以同時檢索多個記錄,而不是一次從數據源檢索一條記錄。 只能在派生`CRecordset`類中實現批量行提取。 將數據從數據源傳輸到記錄集物件的過程稱為批量記錄欄位交換 (Bulk RFX)。 請注意,如果不在`CRecordset`派生類中使用批量行提取,則數據將通過記錄欄位交換 (RFX) 傳輸。 有關詳細資訊,請參閱[記錄欄位交換 (RFX)。](../../data/odbc/record-field-exchange-rfx.md)

本主題將說明：

- [CRecordset 如何支援批次的行取](#_core_how_crecordset_supports_bulk_row_fetching)。

- [使用批次提取時,有一些特殊注意事項](#_core_special_considerations)。

- [如何實作批次紀錄欄位交換](#_core_how_to_implement_bulk_record_field_exchange)。

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>CRecordset 如何支援批次

在打開記錄集物件之前,可以使用`SetRowsetSize`成員函數定義行集大小。 行集大小指定在單個提取期間應檢索的記錄數。 實現批量行提取時,默認行集大小為 25。 如果未實現批量行提取,則行集大小將保持為 1。

初始化列集大小後,呼叫[Open](../../mfc/reference/crecordset-class.md#open)成員函數。 在這裡,`CRecordset::useMultiRowFetch`必須指定*dwOptions*參數的選項,以實現大量的量行提取。 您還可以另外設置該`CRecordset::userAllocMultiRowBuffers`選項。 批量記錄欄位交換機制使用數位來存儲在提取期間檢索的多行數據。 這些存儲緩衝區可以由框架自動分配,也可以手動分配它們。 指定這個`CRecordset::userAllocMultiRowBuffers`選項意味著您將執行分配。

下表列出了 為支援批量行提取`CRecordset`而 提供的成員函數。

|成員函數|描述|
|---------------------|-----------------|
|[檢查羅塞特錯誤](../../mfc/reference/crecordset-class.md#checkrowseterror)|處理提取過程中發生的任何錯誤的虛擬函數。|
|[多布爾菲爾德交易所](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|實現批量記錄欄位交換。 自動調用以將數據源傳輸到記錄集物件的多行數據。|
|[取得羅塞特大小](../../mfc/reference/crecordset-class.md#getrowsetsize)|檢索行集大小的當前設置。|
|[取得列](../../mfc/reference/crecordset-class.md#getrowsfetched)|告訴給定提取后實際檢索的行數。 在大多數情況下,這是行集大小,除非提取不完整的行集。|
|[取得羅維狀態](../../mfc/reference/crecordset-class.md#getrowstatus)|返回行集中特定行的提取狀態。|
|[重新載賽](../../mfc/reference/crecordset-class.md#refreshrowset)|刷新行集中特定行的數據和狀態。|
|[設定羅塞特游標位置](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|將游標移動到行集中的特定行。|
|[設定羅塞特大小](../../mfc/reference/crecordset-class.md#setrowsetsize)|將排組大小的設置更改為指定值的虛擬函數。|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>特殊注意事項

儘管批量行提取是性能提升,但某些功能的操作方式不同。 在決定實現批量行提取之前,請考慮以下事項:

- 框架自動調用`DoBulkFieldExchange`成員函數將數據從數據源傳輸到記錄集物件。 但是,數據不會從記錄集傳輸回數據源。 呼叫`AddNew``Edit``Delete`、、`Update`或成員函數會導致斷言失敗。 儘管`CRecordset`目前不提供更新大量資料行的機制,但您可以使用 ODBC API 函數編寫`SQLSetPos`自己的函數 。 關於的詳細資訊`SQLSetPos`,請參考 MSDN 文件中*的 ODBC SDK 程式者參考*。

- 成員函數`IsDeleted``IsFieldDirty`、 `IsFieldNull` `IsFieldNullable``SetFieldDirty`、`SetFieldNull`和 不能用於實現批量行提取的記錄集。 但是,您可以呼叫`GetRowStatus`代替與`GetODBCFieldInfo``IsFieldNullable``IsDeleted`

- 操作`Move`按行集重新置放記錄集。 例如,假設您打開一個記錄集,該記錄集具有 100 條記錄,初始行集大小為 10。 `Open`獲取行 1 到 10,當前記錄位於第 1 行。 獲取`MoveNext`下一行集的調用,而不是下一行。 此行集由行 11 到 20 組成,當前記錄位於第 11 行上。 請注意,`MoveNext``Move( 1 )`當 實現批量行提取時,並不等效。 `Move( 1 )`從當前記錄獲取 1 行開始的行集。 在此示例中,調用`Open`後調`Move( 1 )`用 獲取由行 2 到 11 組成的行集,當前記錄位於第 2 行。 有關詳細資訊,請參閱[移動](../../mfc/reference/crecordset-class.md#move)成員函數。

- 與記錄欄位交換不同,嚮導不支援批量記錄欄位交換。 這意味著您必須手動聲明欄位數據成員,並通過編寫對大容量 RFX`DoBulkFieldExchange`函數的調用來手動覆蓋。 有關詳細資訊,請參閱*類庫參考*中的[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>如何實現批次記錄欄位交換

批量記錄欄位交換將一排數據從數據源傳輸到記錄集物件。 Bulk RFX 函數使用數位來存儲此數據,以及數位來存儲行集中中每個數據項的長度。 在類定義中,必須將欄位數據成員定義為訪問數據陣列的指標。 此外,必須定義一組指標才能訪問長度陣列。 不應將任何參數數據成員聲明為指標;使用批量記錄欄位交換時聲明參數數據成員與使用記錄欄位交換時聲明參數資料成員相同。 以下代碼顯示了一個簡單的範例:

```cpp
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

您可以手動分配這些儲存緩衝區,也可以讓框架執行分配。 要自己分配緩衝區,必須在`CRecordset::userAllocMultiRowBuffers``Open`成員函數中指定*dwOptions*參數的選項。 請確保設置陣列的大小至少等於行集大小。 如果要讓框架進行分配,則應初始化指向 NULL 的指標。 這通常在紀錄集物件的建構函數中完成:

```cpp
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

最後,必須重寫`DoBulkFieldExchange`成員函數。 對於現場數據成員,調用批量 RFX 函數;對於任何參數數據成員,調用 RFX 函數。 如果通過將 SQL 語句或`Open`儲存過程 傳遞給 來打開記錄集,則進行批量 RFX 調用的順序必須對應於記錄集中列的順序;否則,對 批量 RFX 調用的順序必須與同樣,RFX 調用參數的順序必須對應於 SQL 語句或存儲過程中參數的順序。

```cpp
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
> 在派生`CRecordset`類`Close`超出 範圍之前,必須調用成員函數。 這可確保釋放框架分配的任何記憶體。 無論是否已實現批量行提取,始終顯式調用`Close`都是良好的程式設計實踐。

有關記錄欄位交換 (RFX) 的詳細資訊,請參閱[記錄欄位交換:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有關使用參數的詳細資訊,請參閱[CFieldExchange:SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)和[記錄集:參數化記錄集 (ODBC)。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset:m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
