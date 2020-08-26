---
title: 資料錄欄位交換函式
ms.date: 09/17/2019
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
ms.openlocfilehash: 9bb1b7bcbce16bba8029fcfbbeea7552b1d4a0ba
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843595"
---
# <a name="record-field-exchange-functions"></a>資料錄欄位交換函式

本主題列出資料錄欄位交換 (RFX、Bulk RFX 和 DFX) 函式，您可以使用這些函式將資料錄集物件與其資料來源之間的資料傳輸自動化，並對資料執行其他作業。

如果您使用 ODBC 類別並已實作大量資料列擷取，您必須針對對應至資料來源資料行的每個資料成員呼叫 Bulk RFX 函式，以手動方式覆寫 `DoBulkFieldExchange` 的 `CRecordset` 成員函式。

如果您未在以 ODBC 為基礎的類別中執行大量資料列提取，或是使用 DAO 型類別 (過時的) ，則 ClassWizard 將會覆寫的函數的成員函式，或藉 `DoFieldExchange` `CRecordset` 由針對 `CDaoRecordset` 記錄集中的每個欄位資料成員，)  (呼叫 dao 類別 (的 DFX 函數) 。

每次架構呼叫 `DoFieldExchange` 或 `DoBulkFieldExchange`時，資料錄欄位交換函式都會傳輸資料。 每個函式會傳輸特定資料類型。

如需這些函式使用方式的詳細資訊，請參閱 [資料錄欄位交換：RFX 的運作方式 (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)一文。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

針對您動態繫結的資料行，您也可以自行呼叫 RFX 或 DFX 函式，如 [資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)一文中所述。 此外，您可以撰寫自己的自訂 RFX 或 DFX 常式，如技術提示 [43](../../mfc/tn043-rfx-routines.md) (適用於 ODBC) 和技術提示 [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (適用於 DAO) 中所述。

如需 RFX 和 Bulk RFX 函數出現在和函式的範例 `DoFieldExchange` `DoBulkFieldExchange` ，請參閱 [RFX_Text](#rfx_text) 和 [RFX_Text_Bulk] #rfx_text_bulk) 。 DFX 函式與 RFX 函式很類似。

### <a name="rfx-functions-odbc"></a>RFX 函式 (ODBC)

|名稱|描述|
|-|-|
|[RFX_Binary](#rfx_binary)|傳輸 [CByteArray](cbytearray-class.md)類型的位元組陣列。|
|[RFX_Bool](#rfx_bool)|傳輸布林值資料。|
|[RFX_Byte](#rfx_byte)|傳輸資料的單一位元組。|
|[RFX_Date](#rfx_date)|使用 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 或 TIMESTAMP_STRUCT 傳送時間和日期資料。|
|[RFX_Double](#rfx_double)|傳輸雙精確度浮點數資料。|
|[RFX_Int](#rfx_int)|傳輸整數資料。|
|[RFX_Long](#rfx_long)|傳輸長整數資料。|
|[RFX_LongBinary](#rfx_longbinary)|傳輸物件類別為 [CLongBinary](clongbinary-class.md) 的二進位大型物件 (BLOB) 資料。|
|[RFX_Single](#rfx_single)|傳輸浮點數資料。|
|[RFX_Text](#rfx_text)|傳輸字串資料。|

### <a name="bulk-rfx-functions-odbc"></a>Bulk RFX 函式 (ODBC)

|名稱|描述|
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|傳輸位元組資料陣列。|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|傳輸布林值資料陣列。|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|傳輸單一位元組陣列。|
|[RFX_Date_Bulk](#rfx_date_bulk)|傳輸 TIMESTAMP_STRUCT 類型的資料陣列。|
|[RFX_Double_Bulk](#rfx_double_bulk)|傳輸雙精確度浮點數資料陣列。|
|[RFX_Int_Bulk](#rfx_int_bulk)|傳輸整數資料陣列。|
|[RFX_Long_Bulk](#rfx_long_bulk)|傳輸長整數資料陣列。|
|[RFX_Single_Bulk](#rfx_single_bulk)|傳輸浮點數資料陣列。|
|[RFX_Text_Bulk](#rfx_text_bulk)|傳輸 LPSTR 類型的資料陣列。|

### <a name="dfx-functions-dao"></a>DFX 函式 (DAO)

|名稱|描述|
|-|-|
|[DFX_Binary](#dfx_binary)|傳輸 [CByteArray](cbytearray-class.md)類型的位元組陣列。|
|[DFX_Bool](#dfx_bool)|傳輸布林值資料。|
|[DFX_Byte](#dfx_byte)|傳輸資料的單一位元組。|
|[DFX_Currency](#dfx_currency)|傳輸 [COleCurrency](colecurrency-class.md)類型的貨幣資料。|
|[DFX_DateTime](#dfx_datetime)|傳輸 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)類型的時間和日期資料。|
|[DFX_Double](#dfx_double)|傳輸雙精確度浮點數資料。|
|[DFX_Long](#dfx_long)|傳輸長整數資料。|
|[DFX_LongBinary](#dfx_longbinary)|傳輸物件類別為 `CLongBinary` 的二進位大型物件 (BLOB) 資料。 若是 DAO，建議您改用 [DFX_Binary](#dfx_binary) 。|
|[DFX_Short](#dfx_short)|傳輸短整數資料。|
|[DFX_Single](#dfx_single)|傳輸浮點數資料。|
|[DFX_Text](#dfx_text)|傳輸字串資料。|

=============================================

## <a name="rfx_binary"></a><a name="rfx_binary"></a> RFX_Binary

在物件的欄位資料成員 `CRecordset` 和 ODBC 類型之資料來源上的記錄資料行之間傳輸位元組陣列 SQL_BINARY、SQL_VARBINARY 或 SQL_LONGVARBINARY。

### <a name="syntax"></a>語法

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則會從指定的資料成員取得 [CByteArray](cbytearray-class.md)類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nMaxLength*<br/>
要傳送之字串或陣列的最大允許長度。 *NMaxLength*的預設值為255。 合法值為1到 INT_MAX。 架構會為數據配置此空間量。 為了達到最佳效能，請傳遞夠大的值以容納您預期的最大資料項目。

### <a name="remarks"></a>備註

這些類型之資料來源中的資料會對應至記錄集內的類型或從中對應 `CByteArray` 。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_bool"></a><a name="rfx_bool"></a> RFX_Bool

在物件的欄位資料成員 `CRecordset` 和 ODBC 類型的資料來源 SQL_BIT 之間的記錄資料行之間傳輸布林資料。

### <a name="syntax"></a>語法

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則會從指定的資料成員取得 BOOL 類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_byte"></a><a name="rfx_byte"></a> RFX_Byte

在物件的欄位資料成員 `CRecordset` 和 ODBC 類型之資料來源上的記錄資料行之間傳輸單一位元組 SQL_TINYINT。

### <a name="syntax"></a>語法

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源時，類型為 BYTE 的值會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_date"></a><a name="rfx_date"></a> RFX_Date

在 `CTime` 物件的欄位資料成員 `CRecordset` 和 ODBC 類型之資料來源上的記錄資料行之間傳輸或 TIMESTAMP_STRUCT 資料 SQL_DATE、SQL_TIME 或 SQL_TIMESTAMP。

### <a name="syntax"></a>語法

```cpp
void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   CTime& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   TIMESTAMP_STRUCT& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   COleDateTime& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定之資料成員中的值;要傳送的值。 不同版本的函式會採用不同的資料類型來取得值：

函數的第一個版本會接受 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 物件的參考。 若為從記錄集傳送到資料來源，此值取自指定的資料成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

第二個版本的函式會使用結構的參考 `TIMESTAMP_STRUCT` 。 您必須在呼叫之前自行設定此結構。 此版本不提供對話方塊資料交換 (DDX) 支援或程式碼嚮導支援。 函式的第三個版本的運作方式與第一個版本類似，不同之處在于它會取得 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 物件的參考。

### <a name="remarks"></a>備註

函式的版本會造成 `CTime` 某些中繼處理的額外負荷，並有稍微受限的範圍。 如果您發現其中一個因素太過限制，請使用函式的第二個版本。 但是，請注意缺少的程式碼嚮導和 DDX 支援，以及您自行設定結構的需求。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_double"></a><a name="rfx_double"></a> RFX_Double

在**double float**物件的欄位資料成員 `CRecordset` 和 ODBC 類型之資料來源 SQL_DOUBLE 的記錄資料行之間傳輸雙 float 資料。

### <a name="syntax"></a>語法

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`double`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_int"></a><a name="rfx_int"></a> RFX_Int

在物件的欄位資料成員 `CRecordset` 和 ODBC 類型的資料來源 SQL_SMALLINT 的記錄資料行之間傳輸整數資料。

### <a name="syntax"></a>語法

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`int`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_long"></a><a name="rfx_long"></a> RFX_Long

在物件的欄位資料成員 `CRecordset` 和 ODBC 類型的資料來源 SQL_INTEGER 的記錄資料行之間傳輸長整數資料。

### <a name="syntax"></a>語法

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`long`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a> RFX_LongBinary

使用物件的欄位資料成員和 ODBC 類型之資料來源上之記錄資料行之間的類別 [CLongBinary](clongbinary-class.md) ，傳輸二進位大型物件 (BLOB) 資料 `CRecordset` SQL_LONGVARBINARY 或 SQL_LONGVARCHAR。

### <a name="syntax"></a>語法

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 `CLongBinary` 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_single"></a><a name="rfx_single"></a> RFX_Single

在物件的欄位資料成員 `CRecordset` 和 ODBC 類型之資料來源上的記錄資料行之間，傳輸浮點數資料 SQL_REAL。

### <a name="syntax"></a>語法

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`float`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_text"></a><a name="rfx_text"></a> RFX_Text

在 `CString` 物件的欄位資料成員 `CRecordset` 和 ODBC 類型之資料來源上的記錄資料行之間傳輸資料 SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL 或 SQL_NUMERIC。

### <a name="syntax"></a>語法

```cpp
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
類別物件的指標 `CFieldExchange` 。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 `CString` 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nMaxLength*<br/>
要傳送之字串或陣列的最大允許長度。 *NMaxLength*的預設值為255。 合法值為1，INT_MAX) 。 架構會為數據配置此空間量。 為了達到最佳效能，請傳遞夠大的值以容納您預期的最大資料項目。

*nColumnType*<br/>
主要用於參數。 整數，表示參數的資料類型。 此類型是 **SQL_XXX**形式的 ODBC 資料類型。

*nScale*<br/>
指定 ODBC 類型 SQL_DECIMAL 或 SQL_NUMERIC 之值的小數位數。 *nScale* 只有在設定參數值時才有用。 如需詳細資訊，請參閱《 *ODBC SDK 程式設計人員參考*》的附錄 D 中的「精確度、小數位數、長度和顯示大小」主題。

### <a name="remarks"></a>備註

所有這些類型之資料來源中的資料，都會對應到 `CString` 記錄集內的和。

### <a name="example"></a>範例

這個範例會顯示數個對 `RFX_Text` 的呼叫。 另外也請注意兩個對的呼叫 `CFieldExchange::SetFieldType` 。 針對參數，您必須撰寫呼叫 `SetFieldType` 和其 RFX 呼叫。 輸出資料行呼叫與其相關聯的 RFX 呼叫通常是由程式碼嚮導所撰寫。

```cpp
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a> RFX_Binary_Bulk

從 ODBC 資料來源的資料行將多個位元組資料列傳送至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgByteVals*<br/>
位元組值陣列的指標。 此陣列會儲存要從資料來源傳送到記錄集的資料。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgByteVals*所指向的陣列中。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

*nMaxLength*<br/>
*PrgByteVals*所指向陣列中所儲存之值的最大允許長度。 為確保不會截斷資料，請傳遞夠大的值來容納您預期的最大資料項目。

### <a name="remarks"></a>備註

資料來源資料行可以有 SQL_BINARY、SQL_VARBINARY 或 SQL_LONGVARBINARY 的 ODBC 類型。 記錄集必須將指標類型的欄位資料成員定義為 BYTE。

如果您將 *prgByteVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 為了讓您的記錄集可更新，您必須使用 ODBC API 函式 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參閱 [RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a> RFX_Bool_Bulk

從 ODBC 資料來源的資料行，將布林資料的多個資料列傳送至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgBoolVals*<br/>
BOOL 值陣列的指標。 此陣列會儲存要從資料來源傳送到記錄集的資料。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgBoolVals*所指向的陣列中。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

### <a name="remarks"></a>備註

資料來源資料行必須有 SQL_BIT 的 ODBC 類型。 記錄集必須定義 BOOL 型別指標的欄位資料成員。

如果您將 *prgBoolVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 若要讓您的記錄集可更新，您必須使用 ODBC API 函數 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參閱 [RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a> RFX_Byte_Bulk

從 ODBC 資料來源的資料行，將單一位元組的多個資料列傳送至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgByteVals*<br/>
位元組值陣列的指標。 此陣列會儲存要從資料來源傳送到記錄集的資料。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgByteVals*所指向的陣列中。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

### <a name="remarks"></a>備註

資料來源資料行必須有 SQL_TINYINT 的 ODBC 類型。 記錄集必須將指標類型的欄位資料成員定義為 BYTE。

如果您將 *prgByteVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 若要讓您的記錄集可更新，您必須使用 ODBC API 函數 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參閱 [RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a> RFX_Date_Bulk

從 ODBC 資料來源的資料行，將 TIMESTAMP_STRUCT 資料的多個資料列傳送至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgTSVals*<br/>
TIMESTAMP_STRUCT 值陣列的指標。 此陣列會儲存要從資料來源傳送到記錄集的資料。 如需有關 TIMESTAMP_STRUCT 資料類型的詳細資訊，請參閱《 *ODBC SDK 程式設計人員參考*》的附錄 D 中的「C 資料類型」主題。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgTSVals*所指向的陣列中。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

### <a name="remarks"></a>備註

資料來源資料行可以有 SQL_DATE、SQL_TIME 或 SQL_TIMESTAMP 的 ODBC 類型。 記錄集必須將型別指標的欄位資料成員定義為 TIMESTAMP_STRUCT。

如果您將 *prgTSVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 若要讓您的記錄集可更新，您必須使用 ODBC API 函數 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參閱 [RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a> RFX_Double_Bulk

從 ODBC 資料來源的資料行，將雙精確度、浮點數資料的多個資料列傳輸至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgDblVals*<br/>
值陣列的指標 **`double`** 。 此陣列會儲存要從資料來源傳送到記錄集的資料。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgDblVals*所指向的陣列中。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

### <a name="remarks"></a>備註

資料來源資料行必須有 SQL_DOUBLE 的 ODBC 類型。 記錄集必須定義型別指標的欄位資料成員 **`double`** 。

如果您將 *prgDblVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 若要讓您的記錄集可更新，您必須使用 ODBC API 函數 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參閱 [RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a> RFX_Int_Bulk

在物件的欄位資料成員 `CRecordset` 和 ODBC 類型的資料來源 SQL_SMALLINT 的記錄資料行之間傳輸整數資料。

### <a name="syntax"></a>語法

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需物件可以指定之作業的詳細資訊 `CFieldExchange` ，請參閱 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`int`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參閱 [RFX_Text](#rfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a> RFX_Long_Bulk

從 ODBC 資料來源的資料行，將長整數資料的多個資料列傳送至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgLongVals*<br/>
長整數陣列的指標。 此陣列會儲存要從資料來源傳送到記錄集的資料。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgLongVals*所指向的陣列中。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

### <a name="remarks"></a>備註

資料來源資料行必須有 SQL_INTEGER 的 ODBC 類型。 記錄集必須定義型別指標的欄位資料成員 **`long`** 。

如果您將 *prgLongVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 若要讓您的記錄集可更新，您必須使用 ODBC API 函數 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參閱 [RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a> RFX_Single_Bulk

從 ODBC 資料來源的資料行，將浮點數據的多個資料列傳送至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgFltVals*<br/>
值陣列的指標 **`float`** 。 此陣列會儲存要從資料來源傳送到記錄集的資料。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgFltVals*所指向的陣列中。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

### <a name="remarks"></a>備註

資料來源資料行必須有 SQL_REAL 的 ODBC 類型。 記錄集必須定義型別指標的欄位資料成員 **`float`** 。

如果您將 *prgFltVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 若要讓您的記錄集可更新，您必須使用 ODBC API 函數 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參閱 [RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a> RFX_Text_Bulk

從 ODBC 資料來源的資料行將多個資料列傳送至衍生物件中的對應陣列 `CRecordset` 。

### <a name="syntax"></a>語法

```cpp
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[>cfieldexchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章 [記錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgStrVals*<br/>
LPSTR 值陣列的指標。 此陣列會儲存要從資料來源傳送到記錄集的資料。 請注意，使用 ODBC 的最新版本時，這些值不能是 Unicode。

*prgLengths*<br/>
長整數陣列的指標。 此陣列會將每個值的長度（以位元組為單位）儲存在 *prgStrVals*所指向的陣列中。 此長度不包括 null 終止字元。 請注意，如果對應的資料項目包含 Null 值，則會儲存 SQL_Null_DATA 的值。 如需詳細資訊，請參閱 `SQLBindCol` ODBC SDK 程式設計 *人員參考*中的 odbc API 函數。

*nMaxLength*<br/>
*PrgStrVals*所指向陣列中所儲存值的最大允許長度，包括 null 終止字元。 為確保不會截斷資料，請傳遞夠大的值來容納您預期的最大資料項目。

### <a name="remarks"></a>備註

資料來源資料行可以有 SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL 或 SQL_NUMERIC 的 ODBC 類型。 記錄集必須定義 LPSTR 類型的欄位資料成員。

如果您將 *prgStrVals* 和 *PRGLENGTHS* 初始化為 Null，則會自動設定其指向的陣列，其大小等於資料列集大小。

> [!NOTE]
> 大量記錄欄位交換只會將資料從資料來源傳輸到記錄集物件。 若要讓您的記錄集可更新，您必須使用 ODBC API 函數 `SQLSetPos` 。

如需詳細資訊，請參閱 [記錄集：將大量 (ODBC 中的記錄提取) ](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 和 [記錄欄位交換 (RFX) ](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

您必須在覆寫中手動寫入呼叫 `DoBulkFieldExchange` 。 這個範例會顯示對資料傳輸的呼叫，以及對進行的 `RFX_Text_Bulk` 呼叫 `RFX_Long_Bulk` 。 這些呼叫的開頭會是對 [>cfieldexchange：： SetFieldType](cfieldexchange-class.md#setfieldtype)的呼叫。 請注意，針對參數，您必須呼叫 RFX 函式，而不是大量 RFX 函數。

```cpp
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="dfx_binary"></a><a name="dfx_binary"></a> DFX_Binary

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間傳輸位元組陣列。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則會從指定的資料成員取得 [CByteArray](cbytearray-class.md)類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nPreAllocSize*<br/>
架構會會預先配置此數量的記憶體。 如果您的資料較大，架構會視需要配置更多空間。 為了達到較佳的效能，請將此大小設定為夠大的值，以防止重新配置。 預設大小是在 AFXDAO 中定義。H 檔案做為 AFX_DAO_BINARY_DEFAULT_SIZE。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_DISABLE_FIELD_CACHE 不會使用雙重緩衝，您必須自行呼叫 [SetFieldDirty](cdaorecordset-class.md#setfielddirty) 和 [SetFieldNull](cdaorecordset-class.md#setfieldnull) 。 另一個可能的值 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝，而您不需要執行額外的工作來將欄位標示為已變更或為 Null。 基於效能和記憶體的考慮，除非您的二進位資料相對較小，否則請避免此值。

> [!NOTE]
> 您可以設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，以控制是否根據預設，針對所有欄位將資料進行雙重緩衝。

### <a name="remarks"></a>備註

資料會在 DAO 的類型 DAO_BYTES 和記錄集中的類型 [CByteArray](cbytearray-class.md) 之間對應。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_bool"></a><a name="dfx_bool"></a> DFX_Bool

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間傳輸布林資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則會從指定的資料成員取得 BOOL 類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 的類型 DAO_BOOL 和記錄集中的類型 BOOL 之間進行對應。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_byte"></a><a name="dfx_byte"></a> DFX_Byte

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間傳輸單一位元組。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源時，類型為 BYTE 的值會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

會在 DAO 中的 DAO_BYTES 類型和資料錄集中的 BYTE 類型之間對應資料。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_currency"></a><a name="dfx_currency"></a> DFX_Currency

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間傳輸貨幣資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 若為從記錄集傳送到資料來源，此值取自 [COleCurrency](colecurrency-class.md)類型的指定資料成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 的類型 DAO_CURRENCY 和記錄集中的類型 [COleCurrency](colecurrency-class.md) 之間對應。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a> DFX_DateTime

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間，傳送時間和日期資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 函數會採用 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 物件的參考。 若為從記錄集傳送到資料來源，此值取自指定的資料成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 的類型 DAO_DATE 和記錄集中的類型 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 之間對應。

> [!NOTE]
> `COleDateTime` 將 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 和 TIMESTAMP_STRUCT 取代為 DAO 類別中的這個用途。 `CTime` 和 TIMESTAMP_STRUCT 仍用於以 ODBC 為基礎的資料存取類別。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_double"></a><a name="dfx_double"></a> DFX_Double

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位資料成員和資料來源上的記錄資料行之間傳輸**雙 float**資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`double`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 的型別 DAO_R8 之間進行對應，並在記錄集中輸入 **雙精度浮點數** 。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_long"></a><a name="dfx_long"></a> DFX_Long

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間傳輸長整數資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`long`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 中的類型 DAO_I4 和 **`long`** 記錄集內的類型之間對應。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a> DFX_LongBinary

**重要** 建議您使用 [DFX_Binary](#dfx_binary) 而不是此函數。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則會從指定的資料成員取得 [CLongBinary](clongbinary-class.md)類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwPreAllocSize*<br/>
架構會會預先配置此數量的記憶體。 如果您的資料較大，架構會視需要配置更多空間。 為了達到較佳的效能，請將此大小設定為夠大的值，以防止重新配置。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DISABLE_FIELD_CACHE 不會使用雙重緩衝。 另一個可能的值為 AFX_DAO_ENABLE_FIELD_CACHE。 使用雙重緩衝，您不需要執行額外的工作來將欄位標示為已變更或為 Null。 基於效能和記憶體的考慮，除非您的二進位資料相對較小，否則請避免此值。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

`DFX_LongBinary` 是為了與 MFC ODBC 類別相容而提供。 函式會使用類別`CLongBinary`，在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間，傳送二進位大型物件（BLOB）資料。`DFX_LongBinary` 資料會在 DAO 的類型 DAO_BYTES 和記錄集中的類型 [CLongBinary](clongbinary-class.md) 之間對應。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_short"></a><a name="dfx_short"></a> DFX_Short

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間，傳輸簡短的整數資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`short`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 中的類型 DAO_I2 和 **`short`** 記錄集內的類型之間對應。

> [!NOTE]
> `DFX_Short` 相當於以 ODBC 為基礎之類別的 [RFX_Int](#rfx_int) 。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_single"></a><a name="dfx_single"></a> DFX_Single

在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間傳輸浮點數資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則 **`float`** 會從指定的資料成員取得類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 中的類型 DAO_R4 和 **`float`** 記錄集內的類型之間對應。

### <a name="example"></a>範例

請參閱 [DFX_Text](#dfx_text)。

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="dfx_text"></a><a name="dfx_text"></a> DFX_Text

在 `CString` [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間傳輸資料。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
[CDaoFieldExchange](cdaofieldexchange-class.md)類別的物件指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*value*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 如果是從記錄集傳送到資料來源，則會從指定的資料成員中取得 [CString](../../atl-mfc-shared/reference/cstringt-class.md)類型的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nPreAllocSize*<br/>
架構會會預先配置此數量的記憶體。 如果您的資料較大，架構會視需要配置更多空間。 為了達到較佳的效能，請將此大小設定為夠大的值，以防止重新配置。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 AFX_DAO_ENABLE_FIELD_CACHE 會使用雙重緩衝。 另一個可能的值為 AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 [SetFieldDirty](cdaorecordset-class.md#setfielddirty) 和 [SetFieldNull](cdaorecordset-class.md#setfieldnull) 。

> [!NOTE]
> 您可以藉由設定 [CDaoRecordset：： m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)，來控制是否依預設將資料進行雙重緩衝處理。

### <a name="remarks"></a>備註

資料會在 DAO 的類型 DAO_CHAR 之間對應 (或者，如果定義了符號 _UNICODE，DAO_WCHAR) 並在記錄集中輸入 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。  n

### <a name="example"></a>範例

這個範例會顯示數個對 `DFX_Text` 的呼叫。 另外也請注意兩個對 [CDaoFieldExchange：： SetFieldType](cdaofieldexchange-class.md#setfieldtype)的呼叫。 您必須撰寫的第一個呼叫 `SetFieldType` 和它的 **DFX** 呼叫。 第二個呼叫和其相關聯的 **DFX** 呼叫通常是由產生類別的程式碼嚮導所撰寫。

```cpp
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```

### <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
