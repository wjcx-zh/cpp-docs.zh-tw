---
title: "CMFCFilterChunkValueImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFilterChunkValueImpl
- afxwin/CMFCFilterChunkValueImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCFilterChunkValueImpl class
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8de3cba19a60b8022df96a9edafd13677fa3fecb
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl 類別
這是簡化區塊和屬性值組邏輯的類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destructs 物件。|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|建構物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::Clear](#clear)|清除 ChunkValue。|  
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|將此區塊複製到結構描述的區塊特性。|  
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|初始化此區塊值，與其他的值。|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|擷取區塊 GUID。|  
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|擷取區塊 PID （內容識別碼）。|  
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|取得區塊型別。|  
|[CMFCFilterChunkValueImpl::GetString](#getstring)|擷取字串值。|  
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|為已配置的 propvariant 擷取的值。|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|未配置 （內部值） 的傳回值。|  
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|會檢查這個屬性值是否為有效。|  
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|多載。 布林值的索引鍵所設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Dword 的索引鍵所設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|以 filetime 的索引鍵所設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Int64 的索引鍵所設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|設定屬性索引鍵為 int。|  
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|改為長整數索引鍵所設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|SystemTime 的金鑰設定的屬性。|  
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Unicode 字串的索引鍵所設定的屬性。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Helper 函式會設定區塊的通用屬性。|  
  
## <a name="remarks"></a>備註  
 若要使用，您只要建立正確類型的 CMFCFilterChunkValueImpl 類別  
  
 範例：  
  
 CMFCFilterChunkValueImpl 區塊。  
  
 hr = 區塊。SetBoolValue(PKEY_IsAttachment, true);  
  
 或  
  
 hr = 區塊。SetFileTimeValue (PKEY_ItemDate ftLastModified);  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecleara--cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFCFilterChunkValueImpl::Clear  
 清除 ChunkValue。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecmfcfilterchunkvalueimpla--cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl  
 建構物件。  
  
```  
CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedtorcmfcfilterchunkvalueimpla--cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl  
 Destructs 物件。  
  
```  
virtual ~CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecopychunka--cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk  
 將此區塊複製到結構描述的區塊特性。  
  
```  
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```  
  
### <a name="parameters"></a>參數  
 `pStatChunk`  
 描述區塊的特性目的地值的指標。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecopyfroma--cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFCFilterChunkValueImpl::CopyFrom  
 初始化此區塊值，與其他的值。  
  
```  
void CopyFrom (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>參數  
 `pValue`  
 指定要複製的來源值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetchunkguida--cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID  
 擷取區塊 GUID。  
  
```  
REFGUID GetChunkGUID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 識別區塊的 GUID 參考。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetchunkpida--cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID  
 擷取區塊 PID （內容識別碼）。  
  
```  
DWORD GetChunkPID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 DWORD 值，其中包含屬性識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetchunktypea--cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType  
 擷取區塊型別。  
  
```  
CHUNKSTATE GetChunkType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 CHUNKSTATE 列舉值，指定目前區塊是文字型別屬性或實值型別屬性。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetstringa--cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFCFilterChunkValueImpl::GetString  
 擷取字串值。  
  
```  
CString &GetString();
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含區塊的值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetvaluea--cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue  
 為已配置的 propvariant 擷取的值。  
  
```  
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```  
  
### <a name="parameters"></a>參數  
 `ppPropVariant`  
 函式傳回時，此參數會包含區塊的值。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果已成功地配置 PROPVARIANT 和區塊值已成功地複製到`ppPropVariant`，否則為錯誤程式碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetvaluenoalloca--cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc  
 傳回的未配置 （內部值） 的值。  
  
```  
PROPVARIANT GetValueNoAlloc ();
```  
  
### <a name="return-value"></a>傳回值  
 傳回目前區塊值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisvalida--cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid  
 會檢查這個屬性值是否為有效。  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果目前的區塊值有效，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetboolvaluea--cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue  
 多載。 布林值的索引鍵所設定的屬性。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetchunka--cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk  
 Helper 函式會設定區塊的通用屬性。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則為錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetdwordvaluea--cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue  
 Dword 的索引鍵所設定的屬性。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetfiletimevaluea--cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue  
 Filetime 的金鑰來設定屬性。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetint64valuea--cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value  
 設定屬性索引鍵的 int64。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetintvaluea--cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue  
 設定屬性索引鍵為 int。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetlongvaluea--cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue  
 長時間的金鑰來設定屬性。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetsystemtimevaluea--cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue  
 SystemTime 的金鑰設定的屬性。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesettextvaluea--cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue  
 Unicode 字串的索引鍵所設定的屬性。  
  
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
 文字區塊相關聯的語言和語言。 文件索引子會使用區塊地區設定，以執行適當的斷詞的文字。 如果區塊文字型別都具有資料型別 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 值型別，則會忽略這個欄位。  
  
 `cwcLenSource`  
 目前區塊衍生的來源文字的字元長度。 零值表示逐字元之原始程式文字和衍生的文字之間的對應關係。 非零值表示這種直接對應存在。  
  
 `cwcStartSource`  
 從中衍生的區塊之原始程式文字來源區塊中的啟動位移。  
  
 `chunkBreakType`  
 中斷與目前區塊分隔前一個區塊的類型。 值為 CHUNK_BREAKTYPE 列舉型別。  
  
### <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則錯誤碼。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

