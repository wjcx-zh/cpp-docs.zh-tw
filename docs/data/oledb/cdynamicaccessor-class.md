---
title: CDynamicAccessor 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- GetColumnFlags
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a4a1b08d82e915780817a47abddcf417fe5ab715
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338242"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor 類別
讓您能在不知道資料庫結構描述 (資料庫的基礎結構) 的情況下，存取資料來源。  
  
## <a name="syntax"></a>語法

```cpp
class CDynamicAccessor : public CAccessorBase  
```  

## <a name="requirements"></a>需求  
 **標頭檔**：atldbcli.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddBindEntry](#addbindentry)|當覆寫預設存取子，則您可以將輸出資料行的繫結項目。|  
|[CDynamicAccessor](#cdynamicaccessor)|具現化並初始化`CDynamicAccessor`物件。|  
|[關閉](#close)|所有資料行解除繫結，釋放配置的記憶體，並釋放[IAccessor](https://msdn.microsoft.com/library/ms719672.aspx)類別中的介面指標。|  
|[GetBlobHandling](#getblobhandling)|擷取 BLOB 處理目前的資料列的值。|  
|[GetBlobSizeLimit](#getblobsizelimit)|擷取最大 BLOB 大小 （位元組）。|  
|[GetBookmark](#getbookmark)|擷取目前的資料列的書籤。|  
|[GetColumnCount](#getcolumncount)|擷取資料列集中的資料行的數目。|  
|[GetColumnFlags](#getcolumnflags)|擷取的資料行的特性。|  
|[GetColumnInfo](#getcolumninfo)|擷取資料行中繼資料。|  
|[GetColumnName](#getcolumnname)|擷取指定的資料行的名稱。|  
|[GetColumnType](#getcolumntype)|擷取指定之資料行的資料類型。|  
|[GetLength](#getlength)|擷取以位元組為單位的資料行的最大可能長度。|  
|[GetOrdinal](#getordinal)|擷取給定資料行名稱的資料行索引。|  
|[GetStatus](#getstatus)|擷取指定之資料行的狀態。|  
|[GetValue](#getvalue)|從緩衝區中擷取資料。|  
|[SetBlobHandling](#setblobhandling)|設定 BLOB 處理目前的資料列的值。|  
|[SetBlobSizeLimit](#setblobsizelimit)|設定 BLOB 大小上限 （位元組）。|  
|[SetLength](#setlength)|設定資料行的長度，以位元組為單位。|  
|[SetStatus](#setstatus)|設定指定的資料行的狀態。|  
|[SetValue](#setvalue)|儲存至緩衝區的資料。|  
  
## <a name="remarks"></a>備註  
 使用`CDynamicAccessor`方法來取得資料行資訊，例如資料行名稱、 資料行計數、 資料類型等等。 然後，您會使用此資料行資訊在執行階段動態建立存取子。  
  
 資料行資訊會儲存在緩衝區中，建立和管理由這個類別。 取得從緩衝區使用的資料[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)。  
  
 討論和使用動態存取子類別的範例，請參閱[使用動態存取子](../../data/oledb/using-dynamic-accessors.md)。  

## <a name="addbindentry"></a> Cdynamicaccessor:: Addbindentry
將輸出資料行的繫結項目。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *資訊*  
 [in]A`DBCOLUMNINFO`結構，其中包含資料行資訊。 請參閱中的"DBCOLUMNINFO 結構 」 [icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/library/ms722704.aspx)中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 使用這個方法時覆寫以建立預設存取子`CDynamicAccessor`(請參閱 < [How Do I 擷取資料嗎？](../../data/oledb/fetching-data.md))。 
  
## <a name="cdynamicaccessor"></a> Cdynamicaccessor:: Cdynamicaccessor
具現化並初始化`CDynamicAccessor`物件。  
  
### <a name="syntax"></a>語法  
  
```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000);  
```  
  
#### <a name="parameters"></a>參數  
 *eBlobHandling*  
 指定要處理的二進位大型物件 (BLOB) 資料的方式。 預設值是 DBBLOBHANDLING_DEFAULT。 請參閱[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) cdynamicaccessor:: SETBLOBHANDLING 值的描述。  
  
 *nBlobSize*  
 最大 BLOB 的大小 (以位元組為單位)；此值的資料行資料被視為 BLOB。 預設值為 8000。 請參閱[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)如需詳細資訊。  
  
### <a name="remarks"></a>備註  
 如果您使用建構函式來初始化`CDynamicAccessor`物件時，您可以指定如何 Blob 會繫結。 Blob 可以包含二進位資料，例如圖形、 聲音，或已編譯程式碼。 預設行為是以 Blob 的形式將資料行超過 8,000 個位元組，並嘗試進行繫結`ISequentialStream`物件。 不過，您可以指定 BLOB 的大小不同的值。  
  
 您也可以指定如何`CDynamicAccessor`處理可視為 BLOB 資料的資料行資料： 它可以處理 BLOB 資料，以預設方式，可以略過 （不是繫結） 提供者配置的記憶體中 BLOB 資料，也可以繫結 BLOB 資料。  

## <a name="close"></a> Cdynamicaccessor:: Close
所有資料行解除繫結，釋放配置的記憶體，並釋放[IAccessor](https://msdn.microsoft.com/library/ms719672.aspx)類別中的介面指標。  
  
### <a name="syntax"></a>語法  
  
```cpp
void Close() throw();  
```  

## <a name="getblobhandling"></a> Cdynamicaccessor:: Getblobhandling
擷取 BLOB 處理目前的資料列的值。  
  
### <a name="syntax"></a>語法  
  
```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;  
```  
  
### <a name="remarks"></a>備註  
 傳回處理值的 BLOB *eBlobHandling*所設定的[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)。 

## <a name="getblobsizelimit"></a> Cdynamicaccessor:: Getblobsizelimit
擷取最大 BLOB 大小 （位元組）。  
  
### <a name="syntax"></a>語法  
  
```cpp
const DBLENGTH GetBlobSizeLimit() const;  
```  
  
### <a name="remarks"></a>備註  
 傳回處理值的 BLOB *nBlobSize*所設定的[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)。  

## <a name="getbookmark"></a> Cdynamicaccessor:: Getbookmark
擷取目前的資料列的書籤。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *Findnextrow*  
 [out]指標[CBookmark](../../data/oledb/cbookmark-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 您需要設定`DBPROP_IRowsetLocate`為 VARIANT_TRUE 以便擷取書籤。 

## <a name="getcolumncount"></a> Cdynamicaccessor:: Getcolumncount
擷取資料行的數目。  
  
### <a name="syntax"></a>語法  
  
```cpp
DBORDINAL GetColumnCount() const throw();  
```  
  
### <a name="return-value"></a>傳回值  
 擷取的資料行數目。  

## <a name="getcolumnflags"></a> Cdynamicaccessor:: Getcolumnflags
擷取的資料行的特性。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool GetColumnFlags(DBORDINAL nColumn,   
   DBCOLUMNFLAGS* pFlags) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
 *pFlags*  
 [out]指標，描述資料行特性的位元遮罩。 在中看到 「 < DBCOLUMNFLAGS 列舉類型 」 [icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/library/ms722704.aspx)中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  
 傳回 **，則為 true**如果成功擷取的資料行的特性。 否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 其中一個位移的資料行編號。 零的資料行是特殊案例;如果有的話，它就會是書籤。

## <a name="getcolumninfo"></a> Cdynamicaccessor:: Getcolumninfo
傳回大部分消費者所需的資料行中繼資料。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetColumnInfo(IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *pRowset*  
 [in]指標[IRowset](https://msdn.microsoft.com/library/ms720986.aspx)介面。  
  
 *pColumns*  
 [out]要在其中傳回的資料行數目資料列集; 中的記憶體指標如果有的話，這個數目包含書籤資料行。  
  
 *ppColumnInfo*  
 [out]要在其中傳回的陣列的記憶體指標`DBCOLUMNINFO`結構。 請參閱中的"DBCOLUMNINFO 結構 」 [icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/library/ms722704.aspx)中*OLE DB 程式設計人員參考*。  
  
 *ppStringsBuffer*  
 [out]要在其中傳回的所有字串值的儲存體的指標記憶體的指標 (使用中的名稱*columnid*或是*pwszName*) 單一配置區塊內。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 請參閱[icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/library/ms722704.aspx)中*OLE DB 程式設計人員參考*如需資料類型資訊`DBORDINAL`， `DBCOLUMNINFO`，和`OLECHAR`。  

## <a name="getcolumnname"></a> Cdynamicaccessor:: Getcolumnname
擷取指定的資料行的名稱。  
  
### <a name="syntax"></a>語法  
  
```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
### <a name="return-value"></a>傳回值  
 指定資料行的名稱。  

## <a name="getcolumntype"></a> Cdynamicaccessor:: Getcolumntype
擷取指定之資料行的資料類型。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool GetColumnType(DBORDINAL nColumn,   
   DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
 *pType*  
 [out]指定的資料行的資料型別指標。  
  
### <a name="return-value"></a>傳回值  
 傳回**真**成功或**false**失敗。  

## <a name="getlength"></a> Cdynamicaccessor:: Getlength
擷取指定的資料行的長度。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool GetLength(DBORDINAL nColumn,   
   DBLENGTH* pLength) const throw();  

bool GetLength(const CHAR* pColumnName,   
   DBLENGTH* pLength) const throw();  

bool GetLength(const WCHAR* pColumnName,   
   DBLENGTH* pLength) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
 *pColumnName*  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 *pLength*  
 [out]包含資料行，以位元組為單位的長度的整數指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 **，則為 true**如果找到指定的資料行。 否則，此函數會傳回**false**。  
  
### <a name="remarks"></a>備註  
 第一個覆寫會採用資料行數目，和第二個和第三個覆寫資料行名稱格式採用的 ANSI 或 Unicode，分別。 

## <a name="getordinal"></a> Cdynamicaccessor:: Getordinal
擷取指定資料行名稱的資料行數目。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool GetOrdinal(const CHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  

bool GetOrdinal(const WCHAR* pColumnName,  
   DBORDINAL* pOrdinal) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *pColumnName*  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 *pOrdinal*  
 [out] 指向資料行數目的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 **，則為 true**如果找到具有指定名稱的資料行。 否則，此函數會傳回**false**。

## <a name="getstatus"></a> Cdynamicaccessor:: Getstatus
擷取指定的資料行的狀態。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool GetStatus(DBORDINAL nColumn,   
   DBSTATUS* pStatus) const throw();  

bool GetStatus(const CHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  

bool GetStatus(const WCHAR* pColumnName,  
   DBSTATUS* pStatus) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
 *pColumnName*  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 *pStatus*  
 [out]包含的資料行狀態變數的指標。 請參閱[DBSTATUS](https://msdn.microsoft.com/library/ms722617.aspx)中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回 **，則為 true**如果找到指定的資料行。 否則，此函數會傳回**false**。  

## <a name="getvalue"></a> Cdynamicaccessor:: Getvalue
擷取指定之資料行的資料。  
  
### <a name="syntax"></a>語法  
  
```cpp
void* GetValue(DBORDINAL nColumn) const throw();  

void* GetValue(const CHAR* pColumnName) const throw();  

void* GetValue(const WCHAR* pColumnName) const throw();  

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();  

template < class ctype >  
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *ctype*  
 [in]處理字串型別以外之任何資料類型的樣板參數 (`CHAR*`， `WCHAR*`)，而這需要特殊處理。 `GetValue` 會使用根據您所指定以下的適當資料類型。  
  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
 *pColumnName*  
 [in]資料行名稱。  
  
 *pData*  
 [out]指定的資料行的內容指標。  
  
### <a name="return-value"></a>傳回值  
 如果您想要將字串資料傳遞，使用的樣板版本`GetValue`。 樣板版本，這個方法會傳回`void*`，指向包含指定的資料行資料的緩衝區的一部分。 如果找不到資料行，則傳回 NULL。  
  
 對於所有其他資料類型，是比較容易使用的樣板化版本`GetValue`。 樣板化的版本會傳回**真**成功或**false**失敗。  
  
### <a name="remarks"></a>備註  
 傳回包含字串和樣板化版本，包含其他資料類型的資料行的資料行使用的樣板版本。  
  
 在偵錯模式中，如果您會收到的判斷提示的大小*pData*是它所指向的資料行的大小不相等。  

## <a name="setblobhandling"></a> Cdynamicaccessor:: Setblobhandling
設定 BLOB 處理目前的資料列的值。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);  
```  
  
#### <a name="parameters"></a>參數  
 *eBlobHandling*  
 指定 BLOB 資料的處理方式。 它可以接受下列值：  
  
-   DBBLOBHANDLING_DEFAULT： 處理資料行資料的大小多於*nBlobSize* (由所設定`SetBlobSizeLimit`) 做為 BLOB 資料，並擷取它透過`ISequentialStream`或`IStream`物件。 此選項會嘗試繫結每個資料行，內含資料的大小多於*nBlobSize*或列示為 DBTYPE_IUNKNOWN，做為 BLOB 資料。  
  
-   DBBLOBHANDLING_NOSTREAMS： 處理資料行資料的大小多於*nBlobSize* (所設定的`SetBlobSizeLimit`) 做為 BLOB 資料，並擷取它透過提供者配置、 取用者所擁有的記憶體中的參考。 這個選項適用於有一個以上的 BLOB 資料行的資料表，而且提供者支援只有一個`ISequentialStream`每個存取子的物件。  
  
-   DBBLOBHANDLING_SKIP： 略過 （不會繫結） 限定為包含 Blob 的資料行 （存取子不會繫結或擷取資料行值，但它仍然會擷取資料行的狀態和長度）。  
  
### <a name="remarks"></a>備註  
 您應該先呼叫 `SetBlobHandling`，然後再呼叫 `Open`。  
  
 建構函式方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)設定 BLOB 處理 DBBLOBHANDLING_DEFAULT 的值。

## <a name="setblobsizelimit"></a> Cdynamicaccessor:: Setblobsizelimit
設定 BLOB 大小上限 （位元組）。  
  
### <a name="syntax"></a>語法  
  
```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);  
```  
  
#### <a name="parameters"></a>參數  
 *nBlobSize*  
 指定的 BLOB 大小限制。  
  
### <a name="remarks"></a>備註  
 設定最大 BLOB 大小 （位元組）;資料行資料的大小比這個值會被視為 BLOB。 某些提供者 （例如 2 GB) 的資料行提供極大的大小。 而不是嘗試配置記憶體的資料行這種大小，您通常會嘗試為 Blob 的這些資料行繫結。 這麼一來，您不需要配置所有記憶體時，但您仍然可以讀取的恐懼，截斷的所有資料。 不過，有某些情況的下，您可能想要強制`CDynamicAccessor`繫結其原生資料類型的大型的資料行。 若要這樣做，請呼叫`SetBlobSizeLimit`再呼叫`Open`。  
  
 建構函式方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)設定 BLOB 大小上限為 8,000 個位元組的預設值。  

## <a name="setlength"></a> Cdynamicaccessor:: Setlength
設定指定的資料行的長度。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool SetLength(DBORDINAL nColumn,   
   DBLENGTH nLength)throw();  

bool SetLength(const CHAR* pColumnName,   
   DBLENGTH nLength) throw();  

bool SetLength(const WCHAR* pColumnName,   
   DBLENGTH nLength) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
 *nLength*  
 [in]以位元組為單位的資料行的長度。  
  
 *pColumnName*  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 **，則為 true**如果已成功設定指定的資料行的長度。 否則，此函數會傳回**false**。  

## <a name="setstatus"></a> Cdynamicaccessor:: Setstatus
設定指定的資料行的狀態。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool SetStatus(DBORDINAL nColumn,   
   DBSTATUS status)throw();  

bool SetStatus(const CHAR* pColumnName,   
   DBSTATUS status) throw();  

bool SetStatus(const WCHAR* pColumnName,   
   DBSTATUS status) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
 *status*  
 [in]資料行狀態。 請參閱[DBSTATUS](https://msdn.microsoft.com/library/ms722617.aspx)中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
 *pColumnName*  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 **，則為 true**如果已成功設定指定的資料行狀態。 否則，此函數會傳回**false**。 

## <a name="setvalue"></a> Cdynamicaccessor:: Setvalue
儲存至指定的資料行的資料。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *ctype*  
 [in]處理字串型別以外之任何資料類型的樣板參數 (`CHAR*`， `WCHAR*`)，而這需要特殊處理。 `GetValue` 會使用根據您所指定以下的適當資料類型。  
  
 *pColumnName*  
 [in] 指向包含資料行名稱之字元字串的指標。  
  
 *data*  
 [in]包含資料的記憶體指標。  
  
 *nColumn*  
 [in] 資料行編號。 資料行編號是從 1 開始。 如果有的話，值為 0 就是指書籤資料行。  
  
### <a name="return-value"></a>傳回值  
 如果您想要設定字串資料，使用的樣板版本`GetValue`。 樣板版本，這個方法會傳回`void*`，指向包含指定的資料行資料的緩衝區的一部分。 如果找不到資料行，則傳回 NULL。  
  
 對於所有其他資料類型，是比較容易使用的樣板化版本`GetValue`。 樣板化的版本會傳回**真**成功或**false**失敗。  

## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)