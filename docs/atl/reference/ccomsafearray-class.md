---
title: CComSafeArray 類別
ms.date: 05/06/2019
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: 36750990dc62d5b24cf1107ac8a2724df787a47d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497000"
---
# <a name="ccomsafearray-class"></a>CComSafeArray 類別

這個類別是`SAFEARRAY`結構的包裝函式。

## <a name="syntax"></a>語法

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>參數

*T*<br/>
陣列中儲存之資料的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|建構函式。|
|[CComSafeArray:: ~ CComSafeArray](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComSafeArray::Add](#add)|將一個或多個元素或`SAFEARRAY`結構加入`CComSafeArray`至。|
|[CComSafeArray::Attach](#attach)|將結構附加至`CComSafeArray`物件。 `SAFEARRAY`|
|[CComSafeArray::CopyFrom](#copyfrom)|將`SAFEARRAY`結構的內容複寫`CComSafeArray`到物件中。|
|[CComSafeArray::CopyTo](#copyto)|建立 `CComSafeArray` 物件的複本。|
|[CComSafeArray::Create](#create)|建立 `CComSafeArray` 物件。|
|[CComSafeArray::Destroy](#destroy)|終結 `CComSafeArray` 物件。|
|[CComSafeArray::Detach](#detach)|`SAFEARRAY` 從`CComSafeArray`物件卸離。|
|[CComSafeArray::GetAt](#getat)|從一維陣列中擷取單一項目。|
|[CComSafeArray::GetCount](#getcount)|傳回陣列中的元素數目。|
|[CComSafeArray::GetDimensions](#getdimensions)|傳回陣列中的維度數目。|
|[CComSafeArray::GetLowerBound](#getlowerbound)|傳回陣列中指定維度的下限。|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|傳回 `m_psa` 資料成員的位址。|
|[CComSafeArray::GetType](#gettype)|傳回陣列中儲存之資料的類型。|
|[CComSafeArray::GetUpperBound](#getupperbound)|傳回陣列中任何維度的上限。|
|[CComSafeArray::IsSizable](#issizable)|測試是否可以調整 `CComSafeArray` 物件大小。|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|從多維陣列中擷取單一項目。|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|設定多維陣列中的項目值。|
|[CComSafeArray::Resize](#resize)|調整 `CComSafeArray` 物件大小。|
|[CComSafeArray::SetAt](#setat)|設定一維陣列中的項目值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComSafeArray:: operator LPSAFEARRAY](#operator_lpsafearray)|將值轉換成`SAFEARRAY`指標。|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|從陣列中擷取項目。|
|[CComSafeArray:: operator =](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|此資料成員會保存`SAFEARRAY`結構的位址。|

## <a name="remarks"></a>備註

`CComSafeArray` 提供 [SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-tagsafearray) 類別的包裝函式，因此可輕鬆地建立及管理由幾乎任何支援 VARIANT 的類型所組成的一維和多維陣列。

`CComSafeArray` 不僅簡化了在處理序之間傳遞陣列的作業，還藉由針對上下限檢查陣列索引值，來提供額外的安全性。

`CComSafeArray` 的下限開頭可以是任何使用者定義值；不過，透過 C++ 存取的陣列應該使用下限 0。 Visual Basic 等其他語言可能會使用其他界限值 (例如 -10 到 10)。

使用 [CComSafeArray::Create](#create) 可建立 `CComSafeArray` 物件，而 [CComSafeArray::Destroy](#destroy) 可將它刪除。

`CComSafeArray` 可包含以下 VARIANT 資料類型的子集︰

|VARTYPE|描述|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|ssNoversion|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|FLOAT|
|VT_R8|double|
|VT_DECIMAL|decimal 指標|
|VT_VARIANT|variant 指標|
|VT_CY|Currency 資料類型|

## <a name="requirements"></a>需求

**標頭︰** atlsafe.h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>CComSafeArray:: Add

將一個或多個元素或`SAFEARRAY`結構加入`CComSafeArray`至。

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>參數

*psaSrc*<br/>
          `SAFEARRAY` 物件的指標。

*ulCount*<br/>
要加入至陣列的物件數目。

*pT*<br/>
要加入至陣列的一或多個物件的指標。

*t*<br/>
要加入至陣列之物件的參考。

*bCopy*<br/>
指出是否應該建立資料的複本。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

新的物件會附加至現有`SAFEARRAY`物件的結尾。 不支援將物件加入至`SAFEARRAY`多維度物件。 當加入現有的物件陣列時, 兩個數組都必須包含相同類型的元素。

將 BSTR 或 VARIANT 類型的專案加入至陣列時, 會將*bCopy*旗標納入考慮。 TRUE 的預設值可確保當元素加入至陣列時, 會建立新的複本。

##  <a name="attach"></a>CComSafeArray:: Attach

將結構附加至`CComSafeArray`物件。 `SAFEARRAY`

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>參數

*psaSrc*<br/>
`SAFEARRAY`結構的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

將結構附加`CComSafeArray`至物件, 讓現有`CComSafeArray`的方法可供使用。 `SAFEARRAY`

##  <a name="ccomsafearray"></a>CComSafeArray:: CComSafeArray

建構函式。

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>參數

*限制*<br/>
`SAFEARRAYBOUND` 結構。

*ulCount*<br/>
陣列中的項目數。

*lLBound*<br/>
下限值;也就是陣列中第一個元素的索引。

*pBound*<br/>
`SAFEARRAYBOUND`結構的指標。

*uDims*<br/>
陣列中的維度計數。

*saSrc*<br/>
`SAFEARRAY`結構或`CComSafeArray`物件的參考。 在任一情況下, 此函式都會使用此參考來製作陣列的複本, 因此在結構之後不會參考陣列。

*psaSrc*<br/>
`SAFEARRAY`結構的指標。 此函式會使用此位址來建立陣列的複本, 因此不會在結構後參考陣列。

### <a name="remarks"></a>備註

建立 `CComSafeArray` 物件。

##  <a name="dtor"></a>CComSafeArray:: ~ CComSafeArray

解構函式。

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="copyfrom"></a>CComSafeArray:: CopyFrom

將`SAFEARRAY`結構的內容複寫`CComSafeArray`到物件中。

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>參數

*ppArray*<br/>
要複製之`SAFEARRAY`的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法會將的內容`SAFEARRAY`複製到目前`CComSafeArray`的物件中。 已取代陣列的現有內容。

##  <a name="copyto"></a>CComSafeArray:: CopyTo

建立 `CComSafeArray` 物件的複本。

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>參數

*ppArray*<br/>
要在其中建立新`SAFEARRAY`之位置的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法會將`CComSafeArray`物件的內容複寫`SAFEARRAY`到結構中。

##  <a name="create"></a>  CComSafeArray::Create

建立 `CComSafeArray`。

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>參數

*pBound*<br/>
          `SAFEARRAYBOUND` 物件的指標。

*uDims*<br/>
陣列中的維度數目。

*ulCount*<br/>
陣列中的項目數。

*lLBound*<br/>
下限值;也就是陣列中第一個元素的索引。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

物件可以從現有`SAFEARRAYBOUND`的結構和維度數目建立, 或藉由指定陣列中的專案數目和下限。 `CComSafeArray` 如果要從C++存取陣列, 下限應該是0。 其他語言可能會允許下限的其他值 (例如, Visual Basic 支援陣列的元素具有範圍, 例如-10 到 10)。

##  <a name="destroy"></a>  CComSafeArray::Destroy

終結 `CComSafeArray` 物件。

```
HRESULT Destroy();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

終結現有`CComSafeArray`的物件及其包含的所有資料。

##  <a name="detach"></a>CComSafeArray::D etach

`SAFEARRAY` 從`CComSafeArray`物件卸離。

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>傳回值

傳回`SAFEARRAY`物件的指標。

### <a name="remarks"></a>備註

這個方法會`CComSafeArray`從`SAFEARRAY`物件卸離物件。

##  <a name="getat"></a>CComSafeArray:: GetAt

從一維陣列中擷取單一項目。

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>參數

*lIndex*<br/>
要傳回之陣列中值的索引編號。

### <a name="return-value"></a>傳回值

傳回所需陣列元素的參考。

##  <a name="getcount"></a>CComSafeArray:: GetCount

傳回陣列中的元素數目。

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>參數

*uDim*<br/>
陣列維度。

### <a name="return-value"></a>傳回值

傳回陣列中的元素數目。

### <a name="remarks"></a>備註

與多維陣列搭配使用時, 這個方法只會傳回特定維度中的元素數目。

##  <a name="getdimensions"></a>CComSafeArray:: GetDimensions

傳回陣列中的維度數目。

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>傳回值

傳回陣列中的維度數目。

##  <a name="getlowerbound"></a>CComSafeArray:: GetLowerBound

傳回陣列中指定維度的下限。

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>參數

*uDim*<br/>
要取得下限的陣列維度。 如果省略, 則預設值為0。

### <a name="return-value"></a>傳回值

傳回下限。

### <a name="remarks"></a>備註

如果下限為 0, 這會指出類似 C 的陣列, 其第一個元素為元素編號0。 如果發生錯誤 (例如, 不正確維度引數), 這個方法會呼叫`AtlThrow`並描述錯誤的 HRESULT。

##  <a name="getsafearrayptr"></a>CComSafeArray:: GetSafeArrayPtr

傳回 `m_psa` 資料成員的位址。

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>傳回值

傳回[CComSafeArray:: m_psa](#m_psa)資料成員的指標。

##  <a name="gettype"></a>CComSafeArray:: GetType

傳回陣列中儲存之資料的類型。

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>傳回值

傳回儲存在陣列中的資料類型, 可以是下列任何一種類型:

|VARTYPE|描述|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|ssNoversion|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|FLOAT|
|VT_R8|double|
|VT_DECIMAL|decimal 指標|
|VT_VARIANT|variant 指標|
|VT_CY|Currency 資料類型|

##  <a name="getupperbound"></a>CComSafeArray:: System.array.getupperbound

傳回陣列中任何維度的上限。

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>參數

*uDim*<br/>
要取得上限的陣列維度。 如果省略, 則預設值為0。

### <a name="return-value"></a>傳回值

傳回上限。 此值包含此維度的最大有效索引。

### <a name="remarks"></a>備註

如果發生錯誤 (例如, 不正確維度引數), 這個方法會呼叫`AtlThrow`並描述錯誤的 HRESULT。

##  <a name="issizable"></a>CComSafeArray:: IsSizable

測試是否可以調整 `CComSafeArray` 物件大小。

```
bool IsSizable() const;
```

### <a name="return-value"></a>傳回值

如果`CComSafeArray`可以調整大小, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="m_psa"></a>CComSafeArray:: m_psa

保存所`SAFEARRAY`存取之結構的位址。

```
LPSAFEARRAY m_psa;
```

##  <a name="multidimgetat"></a>CComSafeArray:: MultiDimGetAt

從多維陣列中擷取單一項目。

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>參數

*alIndex*<br/>
陣列中每個維度之索引向量的指標。 最左邊的 (最重要的) `alIndex[0]`維度是。

*t*<br/>
傳回之資料的參考。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="multidimsetat"></a>CComSafeArray:: MultiDimSetAt

設定多維陣列中的項目值。

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>參數

*alIndex*<br/>
陣列中每個維度之索引向量的指標。 最右邊 (最重要的) 維度`alIndex`是 [0]。

*T*<br/>
指定新元素的值。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這是多維度版本的[CComSafeArray:: SetAt](#setat)。

##  <a name="operator_at"></a>CComSafeArray:: operator\[\]

從陣列中擷取項目。

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>參數

*lIndex、nIndex*<br/>
陣列中必要元素的索引編號。

### <a name="return-value"></a>傳回值

傳回適當的陣列元素。

### <a name="remarks"></a>備註

對[CComSafeArray:: GetAt](#getat)執行類似的函式, 不過, 這個運算子只適用于一維陣列。

##  <a name="operator_eq"></a>CComSafeArray:: operator =

指派運算子。

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>參數

*saSrc*<br/>
對 `CComSafeArray` 物件的參考。

*psaSrc*<br/>
          `SAFEARRAY` 物件的指標。

### <a name="return-value"></a>傳回值

傳回陣列中儲存之資料的類型。

##  <a name="operator_lpsafearray"></a>CComSafeArray:: operator LPSAFEARRAY

將值轉換成`SAFEARRAY`指標。

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>傳回值

將值轉換成`SAFEARRAY`指標。

##  <a name="resize"></a>CComSafeArray:: Resize

調整 `CComSafeArray` 物件大小。

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>參數

*pBound*<br/>
`SAFEARRAYBOUND`結構的指標, 其中包含元素數目和陣列下限的資訊。

*ulCount*<br/>
已調整大小之陣列中要求的物件數目。

*lLBound*<br/>
下限。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法只會調整最右邊的維度大小。 它不會調整傳回`IsResizable`為 FALSE 的陣列大小。

##  <a name="setat"></a>CComSafeArray:: SetAt

設定一維陣列中的項目值。

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>參數

*lIndex*<br/>
要設定之陣列元素的索引編號。

*t*<br/>
所指定專案的新值。

*bCopy*<br/>
指出是否應該建立資料的複本。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

將 BSTR 或 VARIANT 類型的專案加入至陣列時, 會將*bCopy*旗標納入考慮。 TRUE 的預設值可確保當元素加入至陣列時, 會建立新的複本。

## <a name="see-also"></a>另請參閱

[SAFEARRAY 資料類型](/windows/win32/api/oaidl/ns-oaidl-tagsafearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[類別總覽](../../atl/atl-class-overview.md)
