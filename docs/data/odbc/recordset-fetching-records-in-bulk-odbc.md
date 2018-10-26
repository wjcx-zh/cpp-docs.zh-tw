---
title: 資料錄集： 擷取大量 (ODBC) 資料錄 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e314f086a1a83a68edd52e11b5d7740be7272fc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053002"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>資料錄集：擷取大量資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

類別`CRecordset`提供支援大量資料列擷取，這表示，多筆記錄可以是一次擷取單一的擷取，而不是擷取一筆資料錄一次從資料來源。 您可以實作只在衍生的大量資料列擷取`CRecordset`類別。 將資料來源的資料傳送到資料錄集物件的程序稱為大量資料錄欄位交換 (Bulk RFX)。 請注意，如果您未使用中的大量資料列擷取`CRecordset`-衍生的類別中，資料透過資料錄欄位交換 (RFX) 傳送。 如需詳細資訊，請參閱 <<c0> [ 資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。

本主題說明：

- [CRecordset 如何支援大量資料列擷取](#_core_how_crecordset_supports_bulk_row_fetching)。

- [當使用一些特殊考量大量資料列擷取](#_core_special_considerations)。

- [如何實作大量資料錄欄位交換](#_core_how_to_implement_bulk_record_field_exchange)。

##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> CRecordset 如何支援大量資料列擷取

然後再開啟您的資料錄集物件，您可以定義具有的資料列集大小`SetRowsetSize`成員函式。 資料列集大小會指定單一擷取期間應該擷取記錄數目。 實作大量資料列擷取時，預設的資料列集大小為 25。 如果未實作大量資料列擷取，資料列集大小會保持固定在 1。

在初始化資料列集大小之後，呼叫[開啟](../../mfc/reference/crecordset-class.md#open)成員函式。 您必須在這裡指定`CRecordset::useMultiRowFetch`的選項*dwOptions*參數來實作大量資料列擷取。 您可以另外設定`CRecordset::userAllocMultiRowBuffers`選項。 大量資料錄欄位交換機制會使用陣列來儲存多個提取時擷取的資料列。 這些儲存體緩衝區可由架構自動配置，或以手動方式配置。 指定`CRecordset::userAllocMultiRowBuffers`選項表示您將進行配置。

下表列出所提供的成員函式`CRecordset`以支援大量資料列擷取。

|成員函式|描述|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|虛擬函式處理期間擷取發生的任何錯誤。|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|實作大量資料錄欄位交換。 會自動呼叫傳輸多個資料列從資料來源的資料錄集物件。|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|擷取資料列集大小的目前設定。|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|會告知實際上在指定的提取之後擷取多少資料列。 在大部分情況下，這是資料列集大小，除非不完整的資料列集擷取。|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|傳回特定資料列內資料列集的提取狀態。|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|重新整理的資料和資料列集內的特定資料列的狀態。|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|將游標移至 資料列集內的特定資料列。|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|虛擬函式變更資料列集大小設定為指定的值。|

##  <a name="_core_special_considerations"></a> 特殊的考量

雖然大量資料列擷取為增進效能，某些功能會以不同的方式運作。 您決定實作大量資料列擷取之前，請考慮下列各項：

- 架構會自動呼叫`DoBulkFieldExchange`將從資料來源的資料傳送到資料錄集物件的成員函式。 不過，資料無法從傳輸資料錄集回資料來源。 呼叫`AddNew`， `Edit`， `Delete`，或`Update`成員函式會導致失敗的判斷提示。 雖然`CRecordset`目前不提供一個機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式`SQLSetPos`。 如需詳細資訊`SQLSetPos`，請參閱 < *ODBC SDK 程式設計人員參考*MSDN 文件中。

- 成員函式`IsDeleted`， `IsFieldDirty`， `IsFieldNull`， `IsFieldNullable`， `SetFieldDirty`，和`SetFieldNull`不能用在實作大量資料列擷取的資料錄集。 不過，您可以呼叫`GetRowStatus`代替`IsDeleted`，並`GetODBCFieldInfo`取代`IsFieldNullable`。

- `Move`作業重新置放的資料列集的資料錄集。 例如，假設您開啟已使用 10 的初始資料列集大小的 100 筆記錄的資料錄集。 `Open` 擷取位於資料列 1 資料列 1 到 10，且目前的記錄。 呼叫`MoveNext`提取下一個資料列集，不下一個資料列。 此資料列集是由資料列 11 到 20，且目前的記錄放在資料列 11 所組成。 請注意，`MoveNext`和`Move( 1 )`所實作的大量資料列擷取時，並不相等。 `Move( 1 )` 擷取開頭的 1 個資料列的目前資料錄的資料列集。 在此範例中，呼叫`Move( 1 )`之後呼叫`Open`提取資料列集包含的資料列 2 到第 11 與目前位於資料列 2 的記錄。 如需詳細資訊，請參閱 <<c0> [ 移動](../../mfc/reference/crecordset-class.md#move)成員函式。

- 不同於資料錄欄位交換，精靈不支援大量資料錄欄位交換。 這表示您必須以手動方式宣告欄位資料成員，並以手動方式覆寫`DoBulkFieldExchange`藉由撰寫 Bulk RFX 函式的呼叫。 如需詳細資訊，請參閱 <<c0> [ 記錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)中*類別庫參考*。

##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> 如何實作大量資料錄欄位交換

大量資料錄欄位交換會傳輸自資料來源的資料列集的資料，資料錄集物件。 大量 RFX 函式會使用陣列來儲存此資料，以及陣列來儲存資料列集中的每個資料項目的長度。 在類別定義中，您必須定義欄位資料成員，為存取的資料陣列的指標。 此外，您必須定義一組指標來存取陣列的長度。 任何參數的資料成員不應該宣告為指標;宣告參數資料成員時使用大量資料錄欄位交換等同於使用資料錄欄位交換時宣告它們。 下列程式碼顯示一個簡單的範例：

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

您可以手動配置這些存放區的緩衝區，或由架構來進行配置。 若要自行配置的緩衝區，您必須指定`CRecordset::userAllocMultiRowBuffers`的選項*dwOptions*中的參數`Open`成員函式。 請務必設定陣列的大小至少等於資料列集大小。 如果您想要讓架構來進行配置，您應該初始化為 NULL 指標。 這通常是在資料錄集物件的建構函式：

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

最後，您必須覆寫`DoBulkFieldExchange`成員函式。 欄位資料成員呼叫 Bulk RFX 函式針對任何參數的資料成員呼叫 RFX 函式。 如果您藉由傳遞的 SQL 陳述式或預存程序來開啟資料錄集`Open`，在您進行 Bulk RFX 呼叫的順序，必須對應於資料錄集中的資料行; 同樣地，RFX 的順序呼叫的參數必須對應此順序中的 SQL 陳述式或預存程序的參數。

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
>  您必須呼叫`Close`成員函式之前您衍生`CRecordset`類別超出範圍。 這可確保會釋出架構配置的任何記憶體。 它是良好的程式設計做法一律明確地呼叫`Close`，而不論您是否有實作大量資料列擷取。

如需有關資料錄欄位交換 (RFX) 的詳細資訊，請參閱 <<c0> [ 資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 如需使用參數的詳細資訊，請參閱[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)並[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

