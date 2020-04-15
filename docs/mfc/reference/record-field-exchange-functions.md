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
ms.openlocfilehash: bfd3ba64a33547b8a27e0f3bc896f39c94486464
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372983"
---
# <a name="record-field-exchange-functions"></a>資料錄欄位交換函式

本主題列出資料錄欄位交換 (RFX、Bulk RFX 和 DFX) 函式，您可以使用這些函式將資料錄集物件與其資料來源之間的資料傳輸自動化，並對資料執行其他作業。

如果您使用 ODBC 類別並已實作大量資料列擷取，您必須針對對應至資料來源資料行的每個資料成員呼叫 Bulk RFX 函式，以手動方式覆寫 `DoBulkFieldExchange` 的 `CRecordset` 成員函式。

如果您尚未在基於 ODBC 的類中實現批量行提取,或者如果您使用的是基於 DAO 的類(已過時),則 ClassWizard 將覆蓋`DoFieldExchange``CRecordset`或`CDaoRecordset`透過為記錄集中的每個字段數據成員調用 RFX 函數(對於 ODBC 類)或 DFX 函數(用於 DAO 類)來覆蓋其成員函數。

每次架構呼叫 `DoFieldExchange` 或 `DoBulkFieldExchange`時，資料錄欄位交換函式都會傳輸資料。 每個函式會傳輸特定資料類型。

如需這些函式使用方式的詳細資訊，請參閱 [資料錄欄位交換：RFX 的運作方式 (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)一文。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

針對您動態繫結的資料行，您也可以自行呼叫 RFX 或 DFX 函式，如 [資料錄集：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)一文中所述。 此外，您可以撰寫自己的自訂 RFX 或 DFX 常式，如技術提示 [43](../../mfc/tn043-rfx-routines.md) (適用於 ODBC) 和技術提示 [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (適用於 DAO) 中所述。

有關 RFX 和批量 RFX`DoFieldExchange``DoBulkFieldExchange`函數在 和 函數中顯示的示例,請參閱[RFX_Text](#rfx_text)和 [RFX_Text_Bulk]#rfx_text_bulk)。 DFX 函式與 RFX 函式很類似。

### <a name="rfx-functions-odbc"></a>RFX 函式 (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|傳輸 [CByteArray](cbytearray-class.md)類型的位元組陣列。|
|[RFX_Bool](#rfx_bool)|傳輸布林值資料。|
|[RFX_Byte](#rfx_byte)|傳輸資料的單一位元組。|
|[RFX_Date](#rfx_date)|使用[CTime](../../atl-mfc-shared/reference/ctime-class.md)或 TIMESTAMP_STRUCT傳輸時間和日期數據。|
|[RFX_Double](#rfx_double)|傳輸雙精確度浮點數資料。|
|[RFX_Int](#rfx_int)|傳輸整數資料。|
|[RFX_Long](#rfx_long)|傳輸長整數資料。|
|[RFX_LongBinary](#rfx_longbinary)|傳輸物件類別為 [CLongBinary](clongbinary-class.md) 的二進位大型物件 (BLOB) 資料。|
|[RFX_Single](#rfx_single)|傳輸浮點數資料。|
|[RFX_Text](#rfx_text)|傳輸字串資料。|

### <a name="bulk-rfx-functions-odbc"></a>Bulk RFX 函式 (ODBC)

|||
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

|||
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

## <a name="rfx_binary"></a><a name="rfx_binary"></a>RFX_Binary

在`CRecordset`物件的欄位資料成員和ODBC類型SQL_BINARY、SQL_VARBINARY或SQL_LONGVARBINARY資料來源上的記錄列之間傳輸位元組。

### <a name="syntax"></a>語法

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源[,CByteArray](cbytearray-class.md)類型的值取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nMaxLength*<br/>
要傳輸的字串或數位的最大允許長度。 *nMaxLength 的*默認值為 255。 法律價值為 1 到 INT_MAX。 框架為數據分配此空間量。 為了獲得最佳性能,傳遞足夠大的值以容納您期望的最大數據項。

### <a name="remarks"></a>備註

這些類型的資料來源中的資料映射到`CByteArray`記錄集中的類型和類型。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_bool"></a><a name="rfx_bool"></a>RFX_Bool

在`CRecordset`物件的欄位資料成員和ODBC類型資料源上的記錄列之間傳輸布林資料SQL_BIT。

### <a name="syntax"></a>語法

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,BOOL 類型的值取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_byte"></a><a name="rfx_byte"></a>RFX_Byte

在`CRecordset`物件的欄位資料成員和ODBC類型數據源上的記錄列之間傳輸單個字節SQL_TINYINT。

### <a name="syntax"></a>語法

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源時，類型為 BYTE 的值會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_date"></a><a name="rfx_date"></a>RFX_Date

在物件的欄位資料成員與ODBC類型SQL_DATE、SQL_TIME或SQL_TIMESTAMP的數據源上的記錄列之間傳輸`CTime`或TIMESTAMP_STRUCT資料。 `CRecordset`

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

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
存儲在指定數據成員中的值;要傳輸的值。 函數的不同版本為值使用不同的資料類型:

函數的第一個版本用於引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。 對於從記錄集傳輸到數據源,此值從指定的數據成員獲取。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

函數的第二個版本參考結構`TIMESTAMP_STRUCT`。 您必須在調用之前自己設置此結構。 此版本不支援對話數據交換 (DDX) 或代碼嚮導支援。 函數的第三個版本的工作方式與第一個版本類似,只不過它引用了[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

### <a name="remarks"></a>備註

函數`CTime`的版本施加了某些中間處理的開銷,並且範圍有限。 如果發現其中任一因素過於限制,請使用函數的第二個版本。 但請注意,它缺乏代碼嚮導和 DDX 支援,以及您自己設置結構的要求。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_double"></a><a name="rfx_double"></a>RFX_Double

在`CRecordset`物件的欄位資料成員和ODBC類型資料來源上的記錄列之間傳輸**雙浮點**資料SQL_DOUBLE。

### <a name="syntax"></a>語法

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,值(類型**為double)** 取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_int"></a><a name="rfx_int"></a>RFX_Int

在`CRecordset`物件的欄位資料成員和ODBC類型資料源上的記錄列之間傳輸SQL_SMALLINT整數資料。

### <a name="syntax"></a>語法

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,從指定的數據成員獲取**類型 int**的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_long"></a><a name="rfx_long"></a>RFX_Long

在`CRecordset`物件的欄位資料成員和ODBC類型數據源上的記錄列之間傳輸長整數資料,SQL_INTEGER。

### <a name="syntax"></a>語法

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,值(類型**長**)取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a>RFX_LongBinary

使用類[CLongBinary](clongbinary-class.md)在`CRecordset`物件的欄位數據成員和 ODBC 類型數據來源上的記錄列之間傳輸二進位大型物件 (BLOB) 資料,SQL_LONGVARBINARY或SQL_LONGVARCHAR。

### <a name="syntax"></a>語法

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,值類型`CLongBinary`從指定的數據成員獲取。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_single"></a><a name="rfx_single"></a>RFX_Single

在`CRecordset`物件的欄位資料成員和ODBC類型數據源上的記錄列之間傳輸浮點資料SQL_REAL。

### <a name="syntax"></a>語法

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,從指定的數據成員獲取類型**float**的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_text"></a><a name="rfx_text"></a>RFX_Text

在`CString``CRecordset`物件欄位資料成員和ODBC類型資料源上SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL或SQL_NUMERIC的數據源上記錄列之間傳輸數據。

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

*pFX*<br/>
指向類`CFieldExchange`物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,值類型`CString`從指定的數據成員獲取。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nMaxLength*<br/>
要傳輸的字串或數位的最大允許長度。 *nMaxLength 的*默認值為 255。 法律價值為 1 到 INT_MAX)。 框架為數據分配此空間量。 為了獲得最佳性能,傳遞足夠大的值以容納您期望的最大數據項。

*nColumnType*<br/>
主要用於參數。 指示參數數據類型的整數。 該類型是表單**SQL_XXX**的 ODBC 資料類型。

*nScale*<br/>
指定 ODBC 類型值SQL_DECIMAL或SQL_NUMERIC的值的比例。 *nScale*僅在設置參數值時有用。 有關詳細資訊,請參閱*ODBC SDK 程式師參考*附錄 D 中的主題「精度、比例、長度和顯示大小」。。

### <a name="remarks"></a>備註

所有這些類型的資料來源中的資料都映射到紀錄集中的和`CString`紀錄中 。

### <a name="example"></a>範例

此示例顯示對`RFX_Text`的多個調用。 另請注意,兩個`CFieldExchange::SetFieldType`呼叫 。 對於參數,您必須將調用寫入`SetFieldType`其 RFX 調用。 輸出列調用及其關聯的 RFX 調用通常由代碼嚮導編寫。

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

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

將多行位元資料從 ODBC 資料來源的列`CRecordset`傳輸到 派生對象的相應陣列。

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

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgByteVals*<br/>
指向 BYTE 值陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgByteVals*指向的陣列中每個值的長度( 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

*nMaxLength*<br/>
*prgByteVals*指向的陣列中儲存的值的最大允許長度。 為確保數據不會被截斷,傳遞足夠大的值以容納預期的最大數據項。

### <a name="remarks"></a>備註

數據來源列可以具有 ODBC 類型的SQL_BINARY、SQL_VARBINARY或SQL_LONGVARBINARY。 記錄集必須定義指向 BYTE 的類型指標的欄位數據成員。

如果將*prgByteVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 為了使記錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參考[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

將多行布林數據從 ODBC 資料來源的`CRecordset`列傳輸到 派生對象的相應陣列。

### <a name="syntax"></a>語法

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgBoolVals*<br/>
指向 BOOL 值陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgBoolVals*指向的陣列中每個值的長度( 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

### <a name="remarks"></a>備註

數據來源列必須具有 ODBC 類型的SQL_BIT。 記錄集必須定義指向 BOOL 的類型數據成員。

如果將*prgBoolVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 要使紀錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參考[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

將多行單位元組從 ODBC 資料來源的`CRecordset`列傳輸到 派生物件中的相應陣列。

### <a name="syntax"></a>語法

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgByteVals*<br/>
指向 BYTE 值陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgByteVals*指向的陣列中每個值的長度( 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

### <a name="remarks"></a>備註

數據來源列必須具有 ODBC 類型的SQL_TINYINT。 記錄集必須定義指向 BYTE 的類型指標的欄位數據成員。

如果將*prgByteVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 要使紀錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參考[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a>RFX_Date_Bulk

將多行TIMESTAMP_STRUCT數據從 ODBC 資料來源的列`CRecordset`傳輸到 派生對象的相應陣列。

### <a name="syntax"></a>語法

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgTSVals*<br/>
指向TIMESTAMP_STRUCT值陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。 有關TIMESTAMP_STRUCT資料類型的詳細資訊,請參閱*ODBC SDK 程式師參考*附錄 D 中的「C 數據類型」主題。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgTSVals*指向的陣列中每個值的長度( 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

### <a name="remarks"></a>備註

數據來源列可以具有 ODBC 類型的SQL_DATE、SQL_TIME或SQL_TIMESTAMP。 記錄集必須定義指向TIMESTAMP_STRUCT的類型指標的欄位數據成員。

如果將*prgTSVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 要使紀錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參考[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a>RFX_Double_Bulk

將多行雙精度浮點數據從 ODBC 資料源的列`CRecordset`傳輸到 派生物件的相應陣列。

### <a name="syntax"></a>語法

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgDblVals*<br/>
指向**雙**值陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgDblVals*指向的陣列中每個值的長度( 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

### <a name="remarks"></a>備註

數據來源列必須具有 ODBC 類型的SQL_DOUBLE。 記錄集必須定義類型指標為**double**的欄位數據成員。

如果將*prgDblVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 要使紀錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參考[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a>RFX_Int_Bulk

在`CRecordset`物件的欄位資料成員和ODBC類型資料源上的記錄列之間傳輸SQL_SMALLINT整數資料。

### <a name="syntax"></a>語法

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關`CFieldExchange`物件可以指定的操作的詳細資訊,請參閱[記錄欄位交換的文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,從指定的數據成員獲取**類型 int**的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

### <a name="example"></a>範例

請參考[RFX_Text](#rfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a>RFX_Long_Bulk

將多行長整數數據從 ODBC 資料來源的列`CRecordset`傳輸到 派生對象的相應陣列。

### <a name="syntax"></a>語法

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgLongVals*<br/>
指向長整數陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgLongVals*指向的陣列中每個值的長度( 以位元組為單位)。 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

### <a name="remarks"></a>備註

數據來源列必須具有 ODBC 類型的SQL_INTEGER。 記錄集必須定義指向**long**的類型指標的欄位數據成員。

如果將*prgLongVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 要使紀錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參考[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a>RFX_Single_Bulk

將多行浮點數據從 ODBC 資料來源的列`CRecordset`傳輸到 派生對象的相應陣列。

### <a name="syntax"></a>語法

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgFltVals*<br/>
指向**浮點**值陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgFltVals*指向的陣列中每個值的長度( 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

### <a name="remarks"></a>備註

數據來源列必須具有 ODBC 類型的SQL_REAL。 記錄集必須定義要**浮動**的類型指標的欄位數據成員。

如果將*prgFltVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 要使紀錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

請參考[RFX_Text_Bulk](#rfx_text_bulk)。

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a>RFX_Text_Bulk

將多行字元數據從 ODBC 資料來源的列`CRecordset`傳輸到 派生對象的相應陣列。

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

*pFX*<br/>
指向[CFieldExchange](cfieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。 有關詳細資訊,請參閱[記錄欄位交換文章:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。

*szName*<br/>
資料行的名稱。

*prgStrVals*<br/>
指向 LPSTR 值陣列的指標。 此陣列將存儲要從數據源傳輸到記錄集的數據。 請注意,使用當前版本的 ODBC 時,這些值不能為 Unicode。

*prgLengths*<br/>
指向長整數陣列的指標。 此陣列將儲存*prgStrVals*指向的陣列中每個值的長度( 此長度不包括空終止字元。 請注意,如果相應的資料項包含 Null 值,則將存儲SQL_NULL_DATA值。 有關詳細資訊,請參閱`SQLBindCol`*ODBC SDK 程式師參考中的 ODBC*API 函數。

*nMaxLength*<br/>
*prgStrVals*指向的陣列中儲存的值的最大允許長度,包括空終止字元。 為確保數據不會被截斷,傳遞足夠大的值以容納預期的最大數據項。

### <a name="remarks"></a>備註

數據來源列可以具有 ODBC 類型的SQL_LONGVARCHAR、SQL_CHAR、SQL_VARCHAR、SQL_DECIMAL或SQL_NUMERIC。 記錄集必須定義 LPSTR 類型的欄位數據成員。

如果將*prgStrVals*和*prgLengths*初始化到 NULL,則它們指向的陣列將自動分配,大小等於行集大小。

> [!NOTE]
> 大量記錄欄位交換僅將資料從資料源傳輸到記錄集物件。 要使紀錄集可更新,必須使用 ODBC API`SQLSetPos`函數 。

有關詳細資訊,請參閱[記錄集:批次提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX) 的文章](../../data/odbc/record-field-exchange-rfx.md)。

### <a name="example"></a>範例

您必須在`DoBulkFieldExchange`重寫中手動寫入呼叫。 此示例顯示對`RFX_Text_Bulk`的調用,以及對`RFX_Long_Bulk`的數據傳輸的調用。 這些呼叫之前先呼叫[CFieldExchange::SetFieldType](cfieldexchange-class.md#setfieldtype)。 請注意,對於參數,必須調用 RFX 函數,而不是批量 RFX 函數。

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

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="dfx_binary"></a><a name="dfx_binary"></a>DFX_Binary

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸位元組。

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

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源[,CByteArray](cbytearray-class.md)類型的值取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nPreAllocSize*<br/>
框架預分配此內存量。 如果數據較大,框架將根據需要分配更多空間。 為了更好的性能,將此大小設置為足夠大的值,以防止重新分配。 默認大小在 AFXDAO 中定義。H 檔為AFX_DAO_BINARY_DEFAULT_SIZE。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設值AFX_DAO_DISABLE_FIELD_CACHE不使用雙重緩衝,您必須自己調用[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull。](cdaorecordset-class.md#setfieldnull) 另一個可能的值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝,您不必執行額外的工作來標記欄位臟或 Null。 出於性能和記憶體原因,請避免此值,除非您的二進位數據相對較小。

> [!NOTE]
> 通過設置[CDaoRecordset:::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對所有欄位雙緩衝數據。

### <a name="remarks"></a>備註

數據在 DAO 中的DAO_BYTES類型和記錄集中的[CByteArray](cbytearray-class.md)類型之間映射。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_bool"></a><a name="dfx_bool"></a>DFX_Bool

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸布林數據。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,BOOL 類型的值取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的類型DAO_BOOL和記錄集中的 BOOL 類型之間映射。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_byte"></a><a name="dfx_byte"></a>DFX_Byte

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸單個字節。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源時，類型為 BYTE 的值會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

會在 DAO 中的 DAO_BYTES 類型和資料錄集中的 BYTE 類型之間對應資料。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_currency"></a><a name="dfx_currency"></a>DFX_Currency

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸貨幣數據。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,此值取自[COleCurrency](colecurrency-class.md)類型的指定數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的DAO_CURRENCY類型和記錄集中的[COleCurrency](colecurrency-class.md)類型之間映射。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a>DFX_DateTime

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和資料來源上記錄的列之間傳輸時間和日期數據。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 此函數引用[COleDateTime 物件](../../atl-mfc-shared/reference/coledatetime-class.md)。 對於從記錄集傳輸到數據源,此值從指定的數據成員獲取。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的類型DAO_DATE和記錄集中的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)類型之間映射。

> [!NOTE]
> `COleDateTime`在 DAO 類別替換[CTime](../../atl-mfc-shared/reference/ctime-class.md)和 TIMESTAMP_STRUCT。 `CTime`並且TIMESTAMP_STRUCT仍用於基於ODBC的數據存取類。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_double"></a><a name="dfx_double"></a>DFX_Double

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸**雙浮點**數據。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,值(類型**為double)** 取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的類型DAO_R8和記錄集中的雙**浮點**類型之間映射。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_long"></a><a name="dfx_long"></a>DFX_Long

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸長整數數據。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,值(類型**長**)取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的類型DAO_I4和記錄集中的類型**長**之間映射。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary

**重要**建議您使用[DFX_Binary](#dfx_binary)而不是此功能。

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

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源[,CLongBinary](clongbinary-class.md)類型的值取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwPreAllocSize*<br/>
框架預分配此內存量。 如果數據較大,框架將根據需要分配更多空間。 為了更好的性能,將此大小設置為足夠大的值,以防止重新分配。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值 AFX_DISABLE_FIELD_CACHE 不使用雙重緩衝。 另一個可能的值是AFX_DAO_ENABLE_FIELD_CACHE。 使用雙重緩衝,您不必執行額外的工作來標記欄位臟或 Null。 出於性能和記憶體原因,請避免此值,除非您的二進位數據相對較小。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

`DFX_LongBinary`提供與 MFC ODBC 類相容。 函式會使用類別`CLongBinary`，在 [CDaoRecordset](cdaorecordset-class.md) 物件的欄位資料成員和資料來源上的記錄資料行之間，傳送二進位大型物件（BLOB）資料。`DFX_LongBinary` 數據在 DAO 中的類型DAO_BYTES和記錄集中的[CLongBinary](clongbinary-class.md)類型之間映射。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_short"></a><a name="dfx_short"></a>DFX_Short

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸短整數數據。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到資料來源,從指定的資料成員獲取類型為**short**的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的類型DAO_I2和記錄集中的**短**類型之間映射。

> [!NOTE]
> `DFX_Short`等效於基於 ODBC 的類[RFX_Int。](#rfx_int)

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_single"></a><a name="dfx_single"></a>DFX_Single

在[CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄的列之間傳輸浮點數據。

### <a name="syntax"></a>語法

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源,從指定的數據成員獲取類型**float**的值。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的類型DAO_R4和記錄集中的**浮點**類型之間映射。

### <a name="example"></a>範例

請參考[DFX_Text](#dfx_text)。

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="dfx_text"></a><a name="dfx_text"></a>DFX_Text

在`CString` [CDaoRecordset](cdaorecordset-class.md)物件的欄位數據成員和數據源上記錄列之間傳輸數據。

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

*pFX*<br/>
指向類[CDaoFieldExchange](cdaofieldexchange-class.md)物件的指標。 這個物件包含定義函式的每個呼叫內容的資訊。

*szName*<br/>
資料行的名稱。

*值*<br/>
儲存在指定資料成員中的值，即要傳輸的值。 對於從記錄集傳輸到數據源[,CString](../../atl-mfc-shared/reference/cstringt-class.md)類型的值取自指定的數據成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。

*nPreAllocSize*<br/>
框架預分配此內存量。 如果數據較大,框架將根據需要分配更多空間。 為了更好的性能,將此大小設置為足夠大的值,以防止重新分配。

*dwBindOptions*<br/>
可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 默認值AFX_DAO_ENABLE_FIELD_CACHE使用雙緩衝。 另一個可能的值是AFX_DAO_DISABLE_FIELD_CACHE。 如果您指定此值，MFC 就不會檢查此欄位。 您必須親自致電[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull。](cdaorecordset-class.md#setfieldnull)

> [!NOTE]
> 通過設置[CDaoRecordset::m_bCheckCacheForDirtyFields,](cdaorecordset-class.md#m_bcheckcachefordirtyfields)可以控制預設情況下是否對數據進行雙重緩衝。

### <a name="remarks"></a>備註

數據在 DAO 中的類型DAO_CHAR(或者,如果定義了符號_UNICODE,DAO_WCHAR)和記錄集中的[CString](../../atl-mfc-shared/reference/cstringt-class.md)類型之間映射。  n

### <a name="example"></a>範例

此示例顯示對`DFX_Text`的多個調用。 另請注意,兩個通話到[CDaoFieldExchange:setFieldType](cdaofieldexchange-class.md#setfieldtype)。 您必須將第一個調用`SetFieldType`寫入其**DFX**調用。 第二個調用及其關聯的**DFX**調用通常由生成類的代碼嚮導編寫。

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

### <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
