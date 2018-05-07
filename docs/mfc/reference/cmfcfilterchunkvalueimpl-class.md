---
title: CMFCFilterChunkValueImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
dev_langs:
- C++
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d274cbafbd50df2f577b484e433c964f1dec096
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl 類別
這是可簡化區塊和屬性值組邏輯的類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destructs 物件。|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|建構物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::Clear](#clear)|清除 ChunkValue。|  
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|將此區塊複製到結構描述的區塊 (chunk) 的特性。|  
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|初始化這個區塊值，與其他的值。|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|擷取區塊的 GUID。|  
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|擷取區塊 PID （內容識別碼）。|  
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|取得區塊型別。|  
|[CMFCFilterChunkValueImpl::GetString](#getstring)|擷取字串值。|  
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|值擷取成配置 propvariant。|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|未配置 （內部值） 的傳回值。|  
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|檢查這個屬性值是否為有效。|  
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|多載。 將屬性設定為布林值的索引鍵。|  
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Dword 的索引鍵所設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|所要 filetime 索引鍵屬性設定。|  
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|所要以 int64 索引鍵屬性設定。|  
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|所要整數索引鍵屬性設定|  
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|長時間的金鑰設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|將屬性設定成 SystemTime 的索引鍵。|  
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|將屬性設定為 Unicode 字串的索引鍵。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|設定區塊的通用屬性的 helper 函式。|  
  
## <a name="remarks"></a>備註  
 若要使用，您只要建立正確類型的 CMFCFilterChunkValueImpl 類別  
  
 範例：  
  
 CMFCFilterChunkValueImpl 區塊;  
  
 hr = 區塊。SetBoolValue(PKEY_IsAttachment, true);  
  
 或  
  
 hr = 區塊。SetFileTimeValue (PKEY_ItemDate ftLastModified);  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="clear"></a>  CMFCFilterChunkValueImpl::Clear  
 清除 ChunkValue。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="cmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl  
 建構物件。  
  
```  
CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl  
 Destructs 物件。  
  
```  
virtual ~CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk  
 將此區塊複製到結構描述的區塊 (chunk) 的特性。  
  
```  
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```  
  
### <a name="parameters"></a>參數  
 `pStatChunk`  
 指向目的地值描述區塊的特性。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom  
 初始化這個區塊值，與其他的值。  
  
```  
void CopyFrom (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>參數  
 `pValue`  
 指定要複製的來源值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID  
 擷取區塊的 GUID。  
  
```  
REFGUID GetChunkGUID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 GUID，識別區塊的參考。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID  
 擷取區塊 PID （內容識別碼）。  
  
```  
DWORD GetChunkPID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 DWORD 值，包含屬性識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType  
 擷取的區塊類型。  
  
```  
CHUNKSTATE GetChunkType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 CHUNKSTATE 列舉值，指定目前區塊是文字類型的屬性或值類型的屬性。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString  
 擷取字串值。  
  
```  
CString &GetString();
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含區塊值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue  
 值擷取成配置 propvariant。  
  
```  
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```  
  
### <a name="parameters"></a>參數  
 `ppPropVariant`  
 此函式傳回時，此參數會包含區塊值。  
  
### <a name="return-value"></a>傳回值  
 如果已成功地配置 PROPVARIANT 和區塊值已成功地複製至 S_OK `ppPropVariant`，否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc  
 傳回的未配置 （內部值） 的值。  
  
```  
PROPVARIANT GetValueNoAlloc ();
```  
  
### <a name="return-value"></a>傳回值  
 傳回目前的區塊值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid  
 檢查這個屬性值是否為有效。  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果目前的區塊值有效，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue  
 多載。 將屬性設定為布林值的索引鍵。  
  
```  
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,  
    BOOL bVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

 
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,  
    VARIANT_BOOL bVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `bVal`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk  
 設定區塊的通用屬性的 helper 函式。  
  
```  
HRESULT SetChunk(
    REFPROPERTYKEY pkey,  
    CHUNKSTATE chunkType=CHUNK_VALUE,  
    LCID locale=0,  
    DWORD cwcLenSource=0,  
    DWORD cwcStartSource=0,  
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue  
 設定機碼 dword 的屬性。  
  
```  
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,  
    DWORD dwVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `dwVal`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue  
 設定要 filetime 索引鍵屬性。  
  
```  
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,  
    FILETIME dtVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `dtVal`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value  
 設定要以 int64 索引鍵屬性。  
  
```  
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,  
    __int64 nVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `nVal`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue  
 將屬性設定為 int。 索引鍵  
  
```  
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,  
    int nVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `nVal`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue  
 設定要長時間索引鍵屬性。  
  
```  
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,  
    long lVal,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `lVal`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue  
 將屬性設定成 SystemTime 的索引鍵。  
  
```  
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,  
    const SYSTEMTIME& systemTime,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale=0,  
    DWORD cwcLenSource=0,  
    DWORD cwcStartSource=0,  
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `systemTime`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue  
 將屬性設定為 Unicode 字串的索引鍵。  
  
```  
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,  
    LPCTSTR pszValue,  
    CHUNKSTATE chunkType = CHUNK_VALUE,  
    LCID locale = 0,  
    DWORD cwcLenSource = 0,  
    DWORD cwcStartSource = 0,  
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```  
  
### <a name="parameters"></a>參數  
 `pkey`  
 指定屬性的索引鍵。  
  
 `pszValue`  
 指定要設定的區塊值。  
  
 `chunkType`  
 旗標會指出這個區塊包含文字類型或實值型別屬性。 旗標值取自 CHUNKSTATE 列舉型別。  
  
 `locale`  
 語言和次要語言的文字區塊相關聯。 文件索引子會使用區塊地區設定，執行適當的斷詞的文字。 如果區塊是文字類型都具有資料類型 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 實值類型，則會忽略此欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示原始程式文字與衍生的文字之間的逐字元對應。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生區塊 (chunk) 的來源文字來源區塊中的開始位移。  
  
 `chunkBreakType`  
 中斷目前的區塊從分隔的前一個區塊的類型。 值是從 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
