---
title: "記錄欄位交換函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions
- DFX functions
- bulk RFX functions
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: acabc4e9469560b67c5fe10bcb845517e05c7854
ms.contentlocale: zh-tw
ms.lasthandoff: 03/31/2017

---
# <a name="record-field-exchange-functions"></a>資料錄欄位交換函式
本主題列出資料錄欄位交換 （RFX，Bulk RFX 和 DFX） 使用資料錄集物件與其資料來源之間的資料傳輸自動化，以及執行其他作業資料的函數。  
  
 如果您使用 ODBC 類別並已實作大量資料列擷取，您必須針對對應至資料來源資料行的每個資料成員呼叫 Bulk RFX 函式，以手動方式覆寫 `DoBulkFieldExchange` 的 `CRecordset` 成員函式。  
  
 如果您未在 ODBC 類別中實作大量資料列擷取，或是使用 DAO 類別，則 ClassWizard 會為資料錄集中的每個欄位資料成員呼叫 RFX 函式 (適用於 ODBC 類別) 或 DFX 函式 (適用於 DAO 類別)，以覆寫 `DoFieldExchange` 或 `CRecordset` 的 `CDaoRecordset` 成員函式。  
  
 每次架構呼叫 `DoFieldExchange` 或 `DoBulkFieldExchange`時，資料錄欄位交換函式都會傳輸資料。 每個函式會傳輸特定資料類型。  
  
 如需有關如何使用這些函數的詳細資訊，請參閱文章[資料錄欄位交換︰ 方式 RFX 的運作 (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md)。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 動態繫結的資料的資料行，您也可以呼叫 RFX 或 DFX 函式，文件中所述[資料錄集︰ 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。 此外，您可以撰寫您自己自訂 RFX 或 DFX 常式，技術提示中所述[43](../../mfc/tn043-rfx-routines.md) （適用於 ODBC) 和技術提示[53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) （適用於 DAO)。  
  
 舉例來說，RFX 和 Bulk RFX 函式中出現`DoFieldExchange`和`DoBulkFieldExchange`函式，請參閱[RFX_Text](#rfx_text)和 [RFX_Text_Bulk] #rfx_text_bulk)。 DFX 函式與 RFX 函式很類似。  
  
### <a name="rfx-functions-odbc"></a>RFX 函式 (ODBC)  
  
|||  
|-|-|  
|[RFX_Binary](#rfx_binary)|傳輸類型的位元組陣列[CByteArray](cbytearray-class.md)。|  
|[RFX_Bool](#rfx_bool)|傳輸布林值資料。|  
|[RFX_Byte](#rfx_byte)|傳輸資料的單一位元組。|  
|[RFX_Date](#rfx_date)|傳輸時間和日期資料使用[CTime](../../atl-mfc-shared/reference/ctime-class.md)或**TIMESTAMP_STRUCT**。|  
|[RFX_Double](#rfx_double)|傳輸雙精確度浮點數資料。|  
|[RFX_Int](#rfx_int)|傳輸整數資料。|  
|[RFX_Long](#rfx_long)|傳輸長整數資料。|  
|[RFX_LongBinary](#rfx_longbinary)|物件的二進位大型物件 (BLOB) 資料傳輸[CLongBinary](clongbinary-class.md)類別。|  
|[RFX_Single](#rfx_single)|傳輸浮點數資料。|  
|[RFX_Text](#rfx_text)|傳輸字串資料。|  
  
### <a name="bulk-rfx-functions-odbc"></a>Bulk RFX 函式 (ODBC)  
  
|||  
|-|-|  
|[RFX_Binary_Bulk](#rfx_binary_bulk)|傳輸位元組資料陣列。|  
|[RFX_Bool_Bulk](#rfx_bool_bulk)|傳輸布林值資料陣列。|  
|[RFX_Byte_Bulk](#rfx_byte_bulk)|傳輸單一位元組陣列。|  
|[RFX_Date_Bulk](#rfx_date_bulk)|傳輸 **TIMESTAMP_STRUCT**類型的資料陣列。|  
|[RFX_Double_Bulk](#rfx_double_bulk)|傳輸雙精確度浮點數資料陣列。|  
|[RFX_Int_Bulk](#rfx_int_bulk)|傳輸整數資料陣列。|  
|[RFX_Long_Bulk](#rfx_long_bulk)|傳輸長整數資料陣列。|  
|[RFX_Single_Bulk](#rfx_single_bulk)|傳輸浮點數資料陣列。|  
|[RFX_Text_Bulk](#rfx_text_bulk)|傳輸 **LPSTR**類型的資料陣列。|  
  
### <a name="dfx-functions-dao"></a>DFX 函式 (DAO)  
  
|||
|-|-|  
|[DFX_Binary](#dfx_binary)|傳輸類型的位元組陣列[CByteArray](cbytearray-class.md)。|  
|[DFX_Bool](#dfx_bool)|傳輸布林值資料。|  
|[DFX_Byte](#dfx_byte)|傳輸資料的單一位元組。|  
|[DFX_Currency](#dfx_currency)|傳輸類型的貨幣資料[COleCurrency](colecurrency-class.md)。|  
|[DFX_DateTime](#dfx_datetime)|將日期和時間類型的資料傳輸[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。|  
|[DFX_Double](#dfx_double)|傳輸雙精確度浮點數資料。|  
|[DFX_Long](#dfx_long)|傳輸長整數資料。|  
|[DFX_LongBinary](#dfx_longbinary)|傳輸物件類別為 `CLongBinary` 的二進位大型物件 (BLOB) 資料。 若是 DAO，建議您改用[DFX_Binary](#dfx_binary)改為。|  
|[DFX_Short](#dfx_short)|傳輸短整數資料。|  
|[DFX_Single](#dfx_single)|傳輸浮點數資料。|  
|[DFX_Text](#dfx_text)|傳輸字串資料。|  

 =============================================

## <a name="rfx_binary"></a>RFX_Binary
欄位資料成員之間傳送的位元組陣列`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_BINARY**， **SQL_VARBINARY**，或**SQL_LONGVARBINARY**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Binary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CByteArray& value,  
   int nMaxLength = 255);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， [CByteArray](cbytearray-class.md)，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `nMaxLength`  
 允許字串或傳輸的陣列的長度上限。 預設值`nMaxLength`為 255。 合法的值為 1 到`INT_MAX`。 架構會配置的空間資料。 為了達到最佳效能，傳遞的值大到足以容納預期的最大資料項目。  
  
### <a name="remarks"></a>備註  
 這些類型的資料來源中的資料型別進行來回對應`CByteArray`資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_bool"></a>RFX_Bool
傳輸布林值資料的欄位資料成員之間`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_BIT**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Bool(  
   CFieldExchange* pFX,  
   const char* szName,  
   BOOL& value);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， **BOOL**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_byte"></a>RFX_Byte
欄位資料成員之間傳輸單一位元組`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_TINYINT**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Byte(  
   CFieldExchange* pFX,  
   const char* szName,  
   BYTE& value);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值，**位元組**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_date"></a>RFX_Date
傳輸`CTime`或**TIMESTAMP_STRUCT**資料之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_DATE**， **SQL_TIME**，或**SQL_TIMESTAMP**。  
  
### <a name="syntax"></a>語法  
  
```
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
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 指定的資料成員; 中儲存的值要傳輸的值。 各種版本的函式會採用不同的資料類型的值︰  
  
 第一個版本的函式會參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。 從資料錄集傳輸至資料來源，這個值是取自指定的資料成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 第二個版本的函式會參考**TIMESTAMP_STRUCT**結構。 您必須設定此結構自行呼叫之前。 沒有對話方塊資料交換 (DDX) 支援也不是可供這個版本的程式碼精靈支援。 第三個版本的函式的運作方式類似的第一個版本不同之處在於它接受以參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。  
  
### <a name="remarks"></a>備註  
 `CTime`函式版本會加諸的一些中繼處理額外負荷，而且具有也會有所限制的範圍。 如果您發現其中一個這些限制太大的因素，使用第二個版本的函式。 但請注意其缺少的程式碼精靈和 DDX 支援以及您設定的結構自己的需求。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_double"></a>RFX_Double
傳輸**雙浮點**資料之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_DOUBLE**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Double(  
   CFieldExchange* pFX,  
   const char* szName,  
   double& value);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， **double**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_int"></a>RFX_Int
傳輸整數資料之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_SMALLINT**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， `int`，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_long"></a>RFX_Long
傳輸長整數資料之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_INTEGER**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Long(  
   CFieldExchange* pFX,  
   const char* szName,  
   LONG&   
value );  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值，**長**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  
## <a name="rfx_longbinary"></a>RFX_LongBinary
使用類別的二進位大型物件 (BLOB) 資料傳輸[CLongBinary](clongbinary-class.md)之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_LONGVARBINARY**或**SQL_LONGVARCHAR**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_LongBinary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CLongBinary& value);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， `CLongBinary`，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_single"></a>RFX_Single
傳輸浮點數資料之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_REAL**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Single(  
   CFieldExchange* pFX,  
   const char* szName,  
   float& value);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， **float**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  

## <a name="rfx_text"></a>RFX_Text
傳輸`CString`資料之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_LONGVARCHAR**， **SQL_CHAR**， **SQL_VARCHAR**， **SQL_DECIMAL**，或**SQL_NUMERIC**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Text(  
   CFieldExchange* pFX,  
   const char* szName,  
   CString& value,  
   int nMaxLength = 255,  
   int nColumnType = SQL_VARCHAR,  
   short nScale = 0);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標`CFieldExchange`。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， `CString`，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `nMaxLength`  
 允許字串或傳輸的陣列的長度上限。 預設值`nMaxLength`為 255。 合法的值為 1 到`INT_MAX`)。 架構會配置的空間資料。 為了達到最佳效能，傳遞的值大到足以容納預期的最大資料項目。  
  
 *nColumnType*  
 主要用於參數。 整數，指出參數的資料類型。 ODBC 資料類型是表單**SQL_XXX**。  
  
 `nScale`  
 指定 ODBC 類型之值的小數位數**SQL_DECIMAL**或**SQL_NUMERIC**。 `nScale`有用時才設定參數值。 如需詳細資訊，請參閱 「 有效位數、 小數位數、 長度和顯示大小 」 主題中的 < 附錄 D *ODBC SDK 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 所有這些類型的資料來源中的資料對應的`CString`資料錄集中。  
  
### <a name="example"></a>範例  
 此範例示範數個呼叫`RFX_Text`。 請注意也要在兩次呼叫`CFieldExchange::SetFieldType`。 參數中，您必須撰寫呼叫`SetFieldType`和其 RFX 呼叫。 輸出資料行呼叫和其相關聯的 RFX 呼叫通常會撰寫的程式碼精靈中。  
  
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
 **標頭︰** afxdb.h  


## <a name="rfx_binary_bulk"></a>RFX_Binary_Bulk
從 ODBC 資料來源的資料行的多個資料列的位元組資料傳輸至對應陣列中`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Binary_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgByteVals`  
 陣列的指標**位元組**值。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgByteVals`。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
 `nMaxLength`  
 允許的最大長度為所指陣列中儲存的值`prgByteVals`。 若要確保不會截斷資料，傳遞的值大到足以容納預期的最大資料項目。  
  
### <a name="remarks"></a>備註  
 資料來源資料行可以具有的 ODBC 類型**SQL_BINARY**， **SQL_VARBINARY**，或**SQL_LONGVARBINARY**。 資料錄集必須定義欄位資料成員的類型指標**位元組**。  
  
 如果您初始化`prgByteVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 為了讓您的資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_bool_bulk"></a>RFX_Bool_Bulk
將布林值資料的多個資料列從 ODBC 資料來源的資料行傳送至對應陣列中`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Bool_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL** prgBoolVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgBoolVals`  
 陣列的指標**BOOL**值。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgBoolVals`。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 資料來源資料行必須具有的 ODBC 類型**SQL_BIT**。 資料錄集必須定義欄位資料成員的類型指標**BOOL**。  
  
 如果您初始化`prgBoolVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 若要讓資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_byte_bulk"></a>RFX_Byte_Bulk
從 ODBC 資料來源的資料行的多個資料列的單一位元組傳輸至對應陣列中`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Byte_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgByteVals`  
 陣列的指標**位元組**值。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgByteVals`。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 資料來源資料行必須具有的 ODBC 類型**SQL_TINYINT**。 資料錄集必須定義欄位資料成員的類型指標**位元組**。  
  
 如果您初始化`prgByteVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 若要讓資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  
## <a name="rfx_date_bulk"></a>RFX_Date_Bulk
傳送多個資料列的**TIMESTAMP_STRUCT**資料從 ODBC 資料來源的資料行中的對應陣列`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Date_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   TIMESTAMP_STRUCT** prgTSVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgTSVals`  
 陣列的指標**TIMESTAMP_STRUCT**值。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。 如需有關**TIMESTAMP_STRUCT**資料類型，請參閱主題 < C 資料類型 > 中的 < 附錄 D *ODBC SDK 程式設計人員參考*。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgTSVals`。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 資料來源資料行可以具有的 ODBC 類型**SQL_DATE**， **SQL_TIME**，或**SQL_TIMESTAMP**。 資料錄集必須定義欄位資料成員的類型指標**TIMESTAMP_STRUCT**。  
  
 如果您初始化`prgTSVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 若要讓資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_double_bulk"></a>RFX_Double_Bulk
從 ODBC 資料來源的資料行的多個資料列的雙精確度浮點數資料傳輸至對應陣列中`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Double_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   double** prgDblVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgDblVals`  
 陣列的指標**double**值。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgDblVals`。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 資料來源資料行必須具有的 ODBC 類型**SQL_DOUBLE**。 資料錄集必須定義欄位資料成員的類型指標**double**。  
  
 如果您初始化`prgDblVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 若要讓資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_int_bulk"></a>RFX_Int_Bulk
傳輸整數資料之間的欄位資料成員`CRecordset`物件和資料行上的資料來源的 ODBC 類型的記錄**SQL_SMALLINT**。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CFieldExchange](cfieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。 如需有關作業`CFieldExchange`可以指定物件，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， `int`，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text](#rfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_long_bulk"></a>RFX_Long_Bulk
從 ODBC 資料來源的資料行的多個資料列的長整數資料傳輸至對應陣列中`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Long_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   long** prgLongVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgLongVals`  
 長整數的陣列指標。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgLongVals`。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 資料來源資料行必須具有的 ODBC 類型**SQL_INTEGER**。 資料錄集必須定義欄位資料成員的類型指標**長**。  
  
 如果您初始化`prgLongVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 若要讓資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  

## <a name="rfx_single_bulk"></a>RFX_Single_Bulk
從 ODBC 資料來源的資料行的多個資料列的浮點數資料傳輸至對應陣列中`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Single_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   float** prgFltVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgFltVals`  
 陣列的指標**float**值。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgFltVals`。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  
 資料來源資料行必須具有的 ODBC 類型**SQL_REAL**。 資料錄集必須定義欄位資料成員的類型指標**float**。  
  
 如果您初始化`prgFltVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 若要讓資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 請參閱[RFX_Text_Bulk](#rfx_text_bulk)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  

## <a name="rfx_text_bulk"></a>RFX_Text_Bulk
將字元資料的多個資料列從 ODBC 資料來源的資料行傳送至對應陣列中`CRecordset`-衍生物件。  
  
### <a name="syntax"></a>語法  
  
```
void RFX_Text_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   LPSTR* prgStrVals,  
   long** prgLengths,  
   int nMaxLength);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](cfieldexchange-class.md)物件。 這個物件包含定義函式的每個呼叫內容的資訊。 如需詳細資訊，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  
  
 `szName`  
 資料行的名稱。  
  
 `prgStrVals`  
 陣列的指標**LPSTR**值。 這個陣列會儲存要從資料來源傳輸至資料錄集的資料。 請注意，目前版本的 ODBC，這些值不可為 Unicode。  
  
 `prgLengths`  
 長整數的陣列指標。 這個陣列會將長度儲存在所指陣列中每個值的位元組`prgStrVals`。 此長度不包括 null 結束字元。 請注意，值**SQL_NULL_DATA**如果對應的資料項目包含 Null 值將會儲存。 如需詳細資訊，請參閱 ODBC API 函式**SQLBindCol**中*ODBC SDK 程式設計人員參考*。  
  
 `nMaxLength`  
 允許的最大長度為所指陣列中儲存的值`prgStrVals`，包括 null 結束字元。 若要確保不會截斷資料，傳遞的值大到足以容納預期的最大資料項目。  
  
### <a name="remarks"></a>備註  
 資料來源資料行可以具有的 ODBC 類型**SQL_LONGVARCHAR**， **SQL_CHAR**， **SQL_VARCHAR**， **SQL_DECIMAL**，或**SQL_NUMERIC**。 資料錄集必須定義類型的欄位資料成員**LPSTR**。  
  
 如果您初始化`prgStrVals`和`prgLengths`至**NULL**，然後指向陣列將會自動配置大小等於資料列集大小。  
  
> [!NOTE]
>  大量資料錄欄位交換僅從資料來源，資料傳輸的資料錄集物件。 若要讓資料錄集更新，您必須使用 ODBC API 函式**SQLSetPos**。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
### <a name="example"></a>範例  
 您必須在中手動撰寫呼叫您`DoBulkFieldExchange`覆寫。 這個範例會示範呼叫`RFX_Text_Bulk`，以及呼叫`RFX_Long_Bulk`，資料傳輸。 這些呼叫的前面呼叫都有[CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md)。 請注意，對於參數，您必須呼叫 RFX 函式，而非 Bulk RFX 函式。  
  
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
 **標頭︰** afxdb.h  

## <a name="dfx_binary"></a>DFX_Binary
欄位資料成員之間傳送的位元組陣列[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Binary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CByteArray& value,  
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， [CByteArray](cbytearray-class.md)，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `nPreAllocSize`  
 架構 preallocates 這樣的記憶體量。 如果您的資料較大，架構會將配置所需的空間。 為提升效能，設定此大小為夠大，無法防止重新配置的值。 AFXDAO 中定義的預設大小。H 檔案儲存為**AFX_DAO_BINARY_DEFAULT_SIZE**。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設值， `AFX_DAO_DISABLE_FIELD_CACHE`，不會不使用雙重緩衝，而您必須呼叫[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull](cdaorecordset-class.md#setfieldnull)自己。 其他可能的值︰ `AFX_DAO_ENABLE_FIELD_CACHE`，會使用雙重緩衝，而且您不需要執行額外的工作來標記的欄位已變更或傳回 Null。 效能和記憶體的原因，請避免此值，除非您的二進位資料是相對較小。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的所有欄位的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_BYTES** DAO 和型別中[CByteArray](cbytearray-class.md)資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  

## <a name="dfx_bool"></a>DFX_Bool
傳輸布林值資料的欄位資料成員之間[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Bool(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， **BOOL**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_BOOL** DAO 和型別中**BOOL**資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

## <a name="dfx_byte"></a>DFX_Byte
欄位資料成員之間傳輸單一位元組[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Byte(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值，**位元組**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_BYTES** DAO 以及類型**位元組**資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

## <a name="dfx_currency"></a>DFX_Currency
貨幣資料傳輸之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Currency(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleCurrency& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源，這個值會取自型別的指定之資料成員[COleCurrency](colecurrency-class.md)。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_CURRENCY** DAO 以及類型[COleCurrency](colecurrency-class.md)資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

## <a name="dfx_datetime"></a>DFX_DateTime
將日期和時間資料傳輸之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_DateTime(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleDateTime& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 此函數會採用參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。 從資料錄集傳輸至資料來源，這個值是取自指定的資料成員。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_DATE** DAO 以及類型[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)資料錄集中。  
  
> [!NOTE]
>  `COleDateTime`取代[CTime](../../atl-mfc-shared/reference/ctime-class.md)和**TIMESTAMP_STRUCT**針對此用途在 DAO 類別中。 `CTime`和**TIMESTAMP_STRUCT**都仍用於 ODBC 為基礎的資料存取的類別。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

## <a name="dfx_double"></a>DFX_Double
傳輸**雙浮點**資料之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Double(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   double& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， **double**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_R8** DAO 以及類型**雙浮點**資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

## <a name="dfx_long"></a>DFX_Long
傳輸長整數資料之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Long(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   long& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值，**長**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_I4** DAO 以及類型**長**資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  

## <a name="dfx_longbinary"></a>DFX_LongBinary
**重要**建議您改用[DFX_Binary](#dfx_binary)而不是此函式。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_LongBinary(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CLongBinary& value,  
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,  
   DWORD dwBindOptions = 0);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， [CLongBinary](clongbinary-class.md)，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 *dwPreAllocSize*  
 架構 preallocates 這樣的記憶體量。 如果您的資料較大，架構會將配置所需的空間。 為提升效能，設定此大小為夠大，無法防止重新配置的值。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設值， **AFX_DISABLE_FIELD_CACHE**，不會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_ENABLE_FIELD_CACHE`。 使用雙重緩衝，而且您不需要執行額外的工作來標記的欄位已變更或傳回 Null。 效能和記憶體的原因，請避免此值，除非您的二進位資料是相對較小。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 `DFX_LongBinary`提供 MFC ODBC 類別與相容性。 `DFX_LongBinary`函式會傳輸使用類別的二進位大型物件 (BLOB) 資料`CLongBinary`之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。 資料類型之間對應**DAO_BYTES** DAO 以及類型[CLongBinary](clongbinary-class.md)資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

## <a name="dfx_short"></a>DFX_Short
傳輸短整數資料之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Short(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   short& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值，**簡短**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_I2** DAO 以及類型**簡短**資料錄集中。  
  
> [!NOTE]
>  `DFX_Short`相當於[RFX_Int](#rfx_int) ODBC 為基礎的類別。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  

## <a name="dfx_single"></a>DFX_Single
傳輸浮點數資料之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Single(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   float& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， **float**，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須自行呼叫 `SetFieldDirty` 和 `SetFieldNull`。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_R4** DAO 以及類型**float**資料錄集中。  
  
### <a name="example"></a>範例  
 請參閱[DFX_Text](#dfx_text)。  
  
### <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  

## <a name="dfx_text"></a>DFX_Text
傳輸`CString`資料之間的欄位資料成員[CDaoRecordset](cdaorecordset-class.md)物件和資料行的資料來源上的記錄。  
  
### <a name="syntax"></a>語法  
  
```
void AFXAPI DFX_Text(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   CString& value,  
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 類別的物件的指標[CDaoFieldExchange](cdaofieldexchange-class.md)。 這個物件包含定義函式的每個呼叫內容的資訊。  
  
 `szName`  
 資料行的名稱。  
  
 *value*  
 儲存在指定資料成員中的值，即要傳輸的值。 從資料錄集傳輸至資料來源類型的值， [CString](../../atl-mfc-shared/reference/cstringt-class.md)，會從指定的資料成員中取得。 從資料來源傳輸至資料錄集時，值會儲存在指定的資料成員中。  
  
 `nPreAllocSize`  
 架構 preallocates 這樣的記憶體量。 如果您的資料較大，架構會將配置所需的空間。 為提升效能，設定此大小為夠大，無法防止重新配置的值。  
  
 `dwBindOptions`  
 可讓您利用 MFC 的雙重緩衝機制來偵測已變更的資料錄集欄位的選項。 預設的 `AFX_DAO_ENABLE_FIELD_CACHE` 會使用雙重緩衝。 另一個可能的值為 `AFX_DAO_DISABLE_FIELD_CACHE`。 如果您指定此值，MFC 就不會檢查此欄位。 您必須呼叫[SetFieldDirty](cdaorecordset-class.md#setfielddirty)和[SetFieldNull](cdaorecordset-class.md#setfieldnull)自己。  
  
> [!NOTE]
>  您可以控制是否資料為雙重緩衝的預設設定[M_bcheckcachefordirtyfields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)。  
  
### <a name="remarks"></a>備註  
 資料類型之間對應**DAO_CHAR**在 DAO 中 (或者，如果符號**_UNICODE**定義， **DAO_WCHAR**) 和型別[CString](../../atl-mfc-shared/reference/cstringt-class.md)資料錄集中。  n
  
### <a name="example"></a>範例  
 此範例示範數個呼叫`DFX_Text`。 請注意也要在兩次呼叫[CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype)。 您必須撰寫的第一個呼叫`SetFieldType`及其**DFX**呼叫。 第二個呼叫以及其相關聯**DFX**呼叫通常所撰寫的程式碼精靈產生的類別。  
  
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
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)   
 [CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)   
 [CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)


