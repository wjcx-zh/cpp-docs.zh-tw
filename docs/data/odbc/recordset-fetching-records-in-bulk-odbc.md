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
ms.openlocfilehash: cd9597da7ab4c405f90a145182d63945cef48c53
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079816"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>資料錄集：擷取大量資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

類別 `CRecordset` 支援大量資料列提取，這表示在單一提取期間可以一次抓取多筆記錄，而不是一次從資料來源中取出一筆記錄。 您只能在衍生的 `CRecordset` 類別中，執行大量資料列提取。 將資料從資料來源傳送到記錄集物件的程式稱為大量記錄欄位交換（Bulk RFX）。 請注意，如果您未在 `CRecordset`衍生的類別中使用大量資料列提取，則會透過記錄欄位交換（RFX）來傳送資料。 如需詳細資訊，請參閱[記錄欄位交換（RFX）](../../data/odbc/record-field-exchange-rfx.md)。

本主題將說明：

- [CRecordset 如何支援大量資料列提取](#_core_how_crecordset_supports_bulk_row_fetching)。

- [使用大量資料列提取時的一些特殊考慮](#_core_special_considerations)。

- [如何執行大量記錄欄位交換](#_core_how_to_implement_bulk_record_field_exchange)。

##  <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>CRecordset 如何支援大量資料列提取

開啟記錄集物件之前，您可以使用 `SetRowsetSize` 成員函式來定義資料列集大小。 資料列集大小會指定在單一提取期間應抓取多少記錄。 當執行大量資料列提取時，預設資料列集大小為25。 如果未執行大量資料列提取，資料列集大小會保持固定的1。

在初始化資料列集大小時，請呼叫[Open](../../mfc/reference/crecordset-class.md#open)成員函式。 在這裡，您必須指定*dwOptions*參數的 `CRecordset::useMultiRowFetch` 選項，以執行大量資料列提取。 此外，您還可以設定 `CRecordset::userAllocMultiRowBuffers` 選項。 大量記錄欄位交換器制會使用陣列來儲存提取期間所抓取的多個資料列。 這些儲存體緩衝區可以由架構自動設定，您也可以手動加以配置。 指定 `CRecordset::userAllocMultiRowBuffers` 選項表示您將進行配置。

下表列出 `CRecordset` 提供的成員函式，以支援大量資料列提取。

|成員函數|描述|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|處理提取期間所發生之任何錯誤的虛擬函式。|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|執行大量記錄欄位交換。 自動呼叫以將資料來源中的多個資料列傳輸到記錄集物件。|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|抓取資料列集大小的目前設定。|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|告訴在給定的提取之後，實際取出了多少資料列。 在大部分情況下，這是資料列集大小，除非提取了不完整的資料列集。|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|傳回資料列集內特定資料列的提取狀態。|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|重新整理資料列集內特定資料列的資料和狀態。|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|將資料指標移至資料列集內的特定資料列。|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|虛擬函式，會將資料列集大小的設定變更為指定的值。|

##  <a name="special-considerations"></a><a name="_core_special_considerations"></a>特殊考慮

雖然大量資料列提取是效能提升，但某些功能的運作方式不同。 在您決定要執行大量資料列提取之前，請考慮下列事項：

- 架構會自動呼叫 `DoBulkFieldExchange` 成員函式，將資料從資料來源傳送到記錄集物件。 不過，資料不會從記錄集傳送回資料來源。 呼叫 `AddNew`、`Edit`、`Delete`或 `Update` 成員函式會導致失敗的判斷提示。 雖然 `CRecordset` 目前並未提供更新大量資料列的機制，但是您可以使用 ODBC API 函式 `SQLSetPos`來撰寫自己的函式。 如需 `SQLSetPos`的詳細資訊，請參閱 MSDN 檔中的*ODBC SDK 程式設計人員參考*。

- 成員函式 `IsDeleted`、`IsFieldDirty`、`IsFieldNull`、`IsFieldNullable`、`SetFieldDirty`和 `SetFieldNull` 不能用在執行大量資料列提取的記錄集上。 不過，您可以呼叫 `GetRowStatus` 取代 `IsDeleted`，並 `GetODBCFieldInfo` 來取代 `IsFieldNullable`。

- `Move` 作業會依資料列集重新置放您的記錄集。 例如，假設您開啟的記錄集具有100記錄，其初始資料列集大小為10。 `Open` 會提取資料列1到10，而目前的記錄位於資料列1。 `MoveNext` 的呼叫會提取下一個資料列集，而不是下一個資料列。 此資料列集是由資料列11到20組成，而目前的記錄位於資料列11。 請注意，執行大量資料列提取時，`MoveNext` 和 `Move( 1 )` 並不相等。 `Move( 1 )` 提取從目前記錄開始1個數據列的資料列集。 在此範例中，呼叫後呼叫 `Move( 1 )` `Open` 提取由資料列2到11組成的資料列集，而目前的記錄位於資料列2。 如需詳細資訊，請參閱[Move](../../mfc/reference/crecordset-class.md#move)成員函式。

- 不同于記錄欄位交換，此嚮導不支援大量記錄欄位交換。 這表示您必須手動宣告欄位資料成員，並藉由撰寫對大量 RFX 函數的呼叫來手動覆寫 `DoBulkFieldExchange`。 如需詳細資訊，請參閱*類別庫參考*中的[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。

##  <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>如何執行大量記錄欄位交換

大量記錄欄位交換會將資料列集從資料來源傳送到記錄集物件。 Bulk RFX 函式會使用陣列來儲存這項資料，以及用來儲存資料列集內每個資料項目長度的陣列。 在您的類別定義中，您必須將欄位資料成員定義為可存取資料陣列的指標。 此外，您必須定義一組指標來存取長度的陣列。 任何參數資料成員都不應該宣告為指標;當使用大量記錄欄位交換時，宣告參數資料成員與使用記錄欄位交換時，會有相同的聲明。 下列程式碼顯示一個簡單的範例：

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

您可以手動設定這些儲存體緩衝區，或讓架構進行配置。 若要自行配置緩衝區，您必須在 `Open` 成員函式中指定*dwOptions*參數的 `CRecordset::userAllocMultiRowBuffers` 選項。 請務必將陣列的大小設定為至少等於資料列集大小。 如果您想要讓架構進行配置，您應該將指標初始化為 Null。 這通常是在記錄集物件的函式中完成：

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

最後，您必須覆寫 `DoBulkFieldExchange` 成員函式。 針對欄位資料成員，呼叫 Bulk RFX 函數;針對任何參數資料成員，呼叫 RFX 函數。 如果您藉由將 SQL 語句或預存程式傳遞至 `Open`來開啟記錄集，則您進行大量 RFX 呼叫的順序必須對應至記錄集內的資料行順序;同樣地，對於參數的 RFX 呼叫順序，必須對應至 SQL 語句或預存程式中的參數順序。

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
>  您必須先呼叫 `Close` 成員函式，您的衍生 `CRecordset` 類別才會超出範圍。 這可確保會釋放架構所配置的任何記憶體。 無論您是否已執行大量資料列提取，都一定要明確地呼叫 `Close`，這是很好的程式設計作法。

如需記錄欄位交換（RFX）的詳細資訊，請參閱[記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 如需使用參數的詳細資訊，請參閱[CFieldExchange：： SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)和[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset：： m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset：： m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
