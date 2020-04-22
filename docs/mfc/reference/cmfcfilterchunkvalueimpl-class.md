---
title: CMFCFilterChunkValueImpl 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: c89d41f7db43d9504bfc22cbf35a59fcceb511e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752370"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl 類別

這是一個簡化塊和屬性值對邏輯的類。

## <a name="syntax"></a>語法

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 過濾器區塊值 impl:_CMFC過濾器區塊值 impl](#_dtorcmfcfilterchunkvalueimpl)|析構物件。|
|[CMFC 過濾器塊值 impl::CMFC 過濾器塊值](#cmfcfilterchunkvalueimpl)|建構物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC過濾器Chunkvalueimpl::清除](#clear)|清除塊值。|
|[CMFC 過濾器塊值 impl::複製區塊](#copychunk)|將此塊複製到描述塊特徵的結構。|
|[CMFC過濾器chunk值::從複製](#copyfrom)|從其他值初始化此塊值。|
|[CMFC過濾器塊值::獲取塊狀](#getchunkguid)|檢索塊 GUID。|
|[CMFC過濾器塊值::獲取塊狀PID](#getchunkpid)|檢索塊 PID(屬性 ID)。|
|[CMFC 過濾器塊值::取得塊類型](#getchunktype)|獲取塊類型。|
|[CMFC 過濾器區塊值::取得字串](#getstring)|檢索字串值。|
|[CMFC過濾器Chunkvalueimpl:獲取價值](#getvalue)|檢索該值作為分配的道具變數。|
|[CMFC過濾器Chunkvalueimpl::獲取ValueNoalloc](#getvaluenoalloc)|返回未分配(內部值)值。|
|[CMFC過濾器chunk值::有效](#isvalid)|檢查此屬性值是否有效。|
|[CMFC過濾器塊值::SetBoolValue](#setboolvalue)|已多載。 按鍵將屬性設置到布爾。|
|[CMFC 過濾器塊值::設定Word值](#setdwordvalue)|按鍵將屬性設置到 DWORD。|
|[CMFC 過濾器區塊值::設定檔案時間值](#setfiletimevalue)|按鍵將屬性設置到檔時間。|
|[CMFC 過濾器塊值:setint64值](#setint64value)|按鍵將屬性設置到 int64。|
|[CMFC 過濾器塊值::setintValue](#setintvalue)|按鍵將屬性設置到 int。|
|[CMFC 過濾器塊值::設定長值](#setlongvalue)|按鍵將屬性設置為 LONG。|
|[CMFC 過濾器區塊值::設定系統時間值](#setsystemtimevalue)|按鍵將屬性設置到系統時間。|
|[CMFC 過濾器區塊值::設定文字值](#settextvalue)|按鍵將屬性設定到 Unicode 字串。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC 過濾器塊值 impl::設定區塊](#setchunk)|設置塊公共屬性的説明器函數。|

## <a name="remarks"></a>備註

使用時,只需建立一個 CMFCFilterChunkValueImpl 類,即可獲得正確的類型

範例：

CMFC過濾器塊值塊;

hr = 塊。SetBoolValue(PKEY_IsAttachment,真實);

或

hr = 塊。設置文件時間值(PKEY_ItemDate,英尺已修改);

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ATL::IFilterChunkValue`

[CMFC 過濾器區塊值](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFC過濾器Chunkvalueimpl::清除

清除塊值。

```cpp
void Clear();
```

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFC 過濾器塊值 impl::CMFC 過濾器塊值

建構物件。

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFC 過濾器區塊值 impl:_CMFC過濾器區塊值 impl

析構物件。

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFC 過濾器塊值 impl::複製區塊

將此塊複製到描述塊特徵的結構。

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>參數

*pStatChunk*<br/>
指向描述塊特徵的目標值的指標。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFC過濾器chunk值::從複製

從其他值初始化此塊值。

```cpp
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>參數

*pValue*<br/>
指定要從中複製的源值。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFC過濾器塊值::獲取塊狀

檢索塊 GUID。

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>傳回值

對標識塊的 GUID 的引用。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFC過濾器塊值::獲取塊狀PID

檢索塊 PID(屬性 ID)。

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>傳回值

包含屬性 ID 的 DWORD 值。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFC 過濾器塊值::取得塊類型

檢索塊類型。

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>傳回值

一個 CHUNKSTATE 枚舉值,它指定當前塊是文本類型屬性還是值類型屬性。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFC 過濾器區塊值::取得字串

檢索字串值。

```
CString &GetString();
```

### <a name="return-value"></a>傳回值

包含塊值的字串。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFC過濾器Chunkvalueimpl:獲取價值

檢索該值作為分配的道具變數。

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>參數

*ppPropVariant*<br/>
當函數返回時,此參數包含塊值。

### <a name="return-value"></a>傳回值

S_OK如果 PROPVARIANT 已成功分配,並且塊值已成功複製到*ppPropvariant;* 否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFC過濾器Chunkvalueimpl::獲取ValueNoalloc

返回未分配(內部值)值。

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>傳回值

返回當前塊值。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFC過濾器chunk值::有效

檢查此屬性值是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果當前塊值有效,則為 TRUE;如果當前塊值有效,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFC過濾器塊值::SetBoolValue

已多載。 按鍵將屬性設置到布爾。

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

*皮基*<br/>
指定屬性鍵。

*bVal*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFC 過濾器塊值 impl::設定區塊

設置塊公共屬性的説明器函數。

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

*皮基*<br/>
指定屬性鍵。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFC 過濾器塊值::設定Word值

按鍵將屬性設置為 DWORD。

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

*皮基*<br/>
指定屬性鍵。

*德瓦爾*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFC 過濾器區塊值::設定檔案時間值

按鍵將屬性設置為文件時間。

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

*皮基*<br/>
指定屬性鍵。

*德瓦爾*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFC 過濾器塊值:setint64值

按鍵將屬性設置為 int64。

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

*皮基*<br/>
指定屬性鍵。

*恩瓦爾*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFC 過濾器塊值::setintValue

按鍵將屬性設置為 int。

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

*皮基*<br/>
指定屬性鍵。

*恩瓦爾*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFC 過濾器塊值::設定長值

按鍵將屬性設置為 LONG。

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

*皮基*<br/>
指定屬性鍵。

*lVal*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFC 過濾器區塊值::設定系統時間值

按鍵將屬性設置到系統時間。

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

*皮基*<br/>
指定屬性鍵。

*系統時間*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFC 過濾器區塊值::設定文字值

按鍵將屬性設定到 Unicode 字串。

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

*皮基*<br/>
指定屬性鍵。

*pszValue*<br/>
指定要設置的塊值。

*區塊類型*<br/>
標誌指示此塊是否包含文本類型或值類型屬性。 標誌值取自 CHUNKSTATE 枚舉。

*locale*<br/>
與文本塊關聯的語言和子語言。 塊區域設置由文檔索引器用於執行正確的文本斷字。 如果塊既不是文本類型,也不是數據類型為VT_LPWSTR、VT_LPSTR 或VT_BSTR的值類型,則此欄位將被忽略。

*cwcLen來源*<br/>
衍生目前的區塊的來源文字的長度( 零值表示源文本和派生文本之間的字元對應。 非零值表示不存在此類直接對應關係。

*cwcStart 來源*<br/>
派生塊的源文本從其開始的偏移量。

*區斷型別*<br/>
將前一個塊與當前塊分隔的中斷類型。 值來自CHUNK_BREAKTYPE枚舉。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則是錯誤代碼。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
