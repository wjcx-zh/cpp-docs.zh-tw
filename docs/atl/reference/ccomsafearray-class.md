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
ms.openlocfilehash: d1e72d364858ea31541d574ed77bdc8ccca7d748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327394"
---
# <a name="ccomsafearray-class"></a>CComSafeArray 類別

此類是結構的`SAFEARRAY`包裝器。

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

|名稱|描述|
|----------|-----------------|
|[CComSafearray:CComSafearray](#ccomsafearray)|建構函式。|
|[CComSafearray:*CComSafearray](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComSafearray:新增](#add)|將一個或多個元素或`SAFEARRAY`結構加入 。 `CComSafeArray`|
|[CComSafearray:附加](#attach)|將`SAFEARRAY`結構附加到`CComSafeArray`物件。|
|[CComSafearray::從](#copyfrom)|將`SAFEARRAY`結構的內容複製到物件`CComSafeArray`中 。|
|[CComSafearray::複製到](#copyto)|建立 `CComSafeArray` 物件的複本。|
|[CComSafeArray::Create](#create)|建立 `CComSafeArray` 物件。|
|[CComSafeArray::Destroy](#destroy)|終結 `CComSafeArray` 物件。|
|[CComSafearray::D](#detach)|從`CComSafeArray`物件`SAFEARRAY`分離 。|
|[CComSafearray:GetAt](#getat)|從一維陣列中擷取單一項目。|
|[CComSafearray:取得計數](#getcount)|傳回陣列中的元素數目。|
|[CComSafearray:取得維度](#getdimensions)|傳回陣列中的維度數目。|
|[CComSafearray:取得下限](#getlowerbound)|傳回陣列中指定維度的下限。|
|[CComSafearray:取得安全陣列](#getsafearrayptr)|傳回 `m_psa` 資料成員的位址。|
|[CComSafearray:取得類型](#gettype)|傳回陣列中儲存之資料的類型。|
|[CComSafearray:取得上部](#getupperbound)|傳回陣列中任何維度的上限。|
|[CComSafearray::可比](#issizable)|測試是否可以調整 `CComSafeArray` 物件大小。|
|[CComSafearray::多迪姆格拉特](#multidimgetat)|從多維陣列中擷取單一項目。|
|[CComSafearray::多迪姆塞特](#multidimsetat)|設定多維陣列中的項目值。|
|[CComSafearray:調整大小](#resize)|調整 `CComSafeArray` 物件大小。|
|[CComSafearray::Setat](#setat)|設定一維陣列中的項目值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComSafearray::操作員LPSAFEARRAY](#operator_lpsafearray)|將值強制轉換為`SAFEARRAY`指標。|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|從陣列中擷取項目。|
|[CComSafeArray::操作員 |](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComSafearray:m_psa](#m_psa)|此資料成員儲存結構的位址`SAFEARRAY`。|

## <a name="remarks"></a>備註

`CComSafeArray` 提供 [SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray) 類別的包裝函式，因此可輕鬆地建立及管理由幾乎任何支援 VARIANT 的類型所組成的一維和多維陣列。

`CComSafeArray` 不僅簡化了在處理序之間傳遞陣列的作業，還藉由針對上下限檢查陣列索引值，來提供額外的安全性。

`CComSafeArray` 的下限開頭可以是任何使用者定義值；不過，透過 C++ 存取的陣列應該使用下限 0。 Visual Basic 等其他語言可能會使用其他界限值 (例如 -10 到 10)。

使用 [CComSafeArray::Create](#create) 可建立 `CComSafeArray` 物件，而 [CComSafeArray::Destroy](#destroy) 可將它刪除。

`CComSafeArray` 可包含以下 VARIANT 資料類型的子集︰

|VARTYPE|描述|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
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

## <a name="ccomsafearrayadd"></a><a name="add"></a>CComSafearray:新增

將一個或多個元素或`SAFEARRAY`結構加入 。 `CComSafeArray`

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>參數

*普薩斯克*<br/>
`SAFEARRAY` 物件的指標。

*ulCount*<br/>
要添加到陣列的物件數。

*鉑*<br/>
指向要添加到陣列的一個或多個物件的指標。

*t*<br/>
對要添加到陣列的物件的引用。

*bCopy*<br/>
指示是否應創建數據的副本。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

新物件將追加到現有`SAFEARRAY`物件的末尾。 不支援將物件添加到多維`SAFEARRAY`物件。 添加現有物件陣列時,兩個陣列必須包含相同類型的元素。

當將 BSTR 類型或 VARIANT 的元素添加到陣列時,將考慮*bCopy*標誌。 TRUE 的預設值可確保在元素添加到陣列時對資料進行新副本。

## <a name="ccomsafearrayattach"></a><a name="attach"></a>CComSafearray:附加

將`SAFEARRAY`結構附加到`CComSafeArray`物件。

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>參數

*普薩斯克*<br/>
指向結構的`SAFEARRAY`指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

將`SAFEARRAY`結構附加到`CComSafeArray`物件,使`CComSafeArray`現有方法可用。

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafearray:CComSafearray

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

*綁定*<br/>
`SAFEARRAYBOUND` 結構。

*ulCount*<br/>
陣列中的項目數。

*LLBound*<br/>
下限值;即陣列中第一個元素的索引。

*p 繫結*<br/>
指向結構的`SAFEARRAYBOUND`指標。

*烏迪姆*<br/>
陣列中的維度計數。

*薩斯爾克*<br/>
對`SAFEARRAY`結構或`CComSafeArray`物件的引用。 在這兩種情況下,建構函數都使用此引用來創建陣列的副本,因此在構造後不會引用陣列。

*普薩斯克*<br/>
指向結構的`SAFEARRAY`指標。 建構函數使用此位址創建陣列的副本,因此在建構後不會引用陣列。

### <a name="remarks"></a>備註

建立 `CComSafeArray` 物件。

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafearray:*CComSafearray

解構函式。

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafearray::從

將`SAFEARRAY`結構的內容複製到物件`CComSafeArray`中 。

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>參數

*ppArray*<br/>
指標`SAFEARRAY`到 要複製。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此方法將`SAFEARRAY`的內容 複製`CComSafeArray`到當前 物件中。 將替換陣列的現有內容。

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a>CComSafearray::複製到

建立 `CComSafeArray` 物件的複本。

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>參數

*ppArray*<br/>
指向要在其中創建新`SAFEARRAY`位置的位置的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此方法將`CComSafeArray`物件的內容複製到結構`SAFEARRAY`中 。

## <a name="ccomsafearraycreate"></a><a name="create"></a>CComSafearray:建立

建立 `CComSafeArray`。

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>參數

*p 繫結*<br/>
`SAFEARRAYBOUND` 物件的指標。

*烏迪姆*<br/>
陣列中維度的數目。

*ulCount*<br/>
陣列中的項目數。

*LLBound*<br/>
下限值;即陣列中第一個元素的索引。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

可以從`CComSafeArray`現有`SAFEARRAYBOUND`結構和維度數創建物件,或者通過指定陣列中的元素數和下限。 如果要從C++訪問陣列,下限應為0。 其他語言可能允許下限的其他值(例如,Visual Basic 支援具有元素的陣列,範圍為 -10 到 10)。

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray::D

終結 `CComSafeArray` 物件。

```
HRESULT Destroy();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

銷毀現有`CComSafeArray`物件及其包含的所有數據。

## <a name="ccomsafearraydetach"></a><a name="detach"></a>CComSafearray::D

從`CComSafeArray`物件`SAFEARRAY`分離 。

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>傳回值

返回指向`SAFEARRAY`物件的指標。

### <a name="remarks"></a>備註

此方法將`SAFEARRAY`物件`CComSafeArray`從 物件中分離出來。

## <a name="ccomsafearraygetat"></a><a name="getat"></a>CComSafearray:GetAt

從一維陣列中擷取單一項目。

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>參數

*lIndex*<br/>
要返回的陣列中值的索引編號。

### <a name="return-value"></a>傳回值

返回對所需陣列元素的引用。

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a>CComSafearray:取得計數

傳回陣列中的元素數目。

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>參數

*烏迪姆*<br/>
陣列維度。

### <a name="return-value"></a>傳回值

傳回陣列中的元素數目。

### <a name="remarks"></a>備註

當與多維陣列一起使用時,此方法將僅返回特定維度中的元素數。

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafearray:取得維度

傳回陣列中的維度數目。

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>傳回值

傳回陣列中的維度數目。

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafearray:取得下限

傳回陣列中指定維度的下限。

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>參數

*烏迪姆*<br/>
要為其獲取下限的陣列維度。 如果省略,默認值為 0。

### <a name="return-value"></a>傳回值

返回下限。

### <a name="remarks"></a>備註

如果下限為 0,則表示第一個元素為元素 0 的 C 樣陣組。 例如,如果出現錯誤,此方法調用`AtlThrow`HRESULT 來描述錯誤。

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafearray:取得安全陣列

傳回 `m_psa` 資料成員的位址。

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>傳回值

返回指向[CComSafeArray::m_psa](#m_psa)數據成員的指標。

## <a name="ccomsafearraygettype"></a><a name="gettype"></a>CComSafearray:取得類型

傳回陣列中儲存之資料的類型。

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>傳回值

傳回儲存在陣列中的資料類型,可以是以下任一類型:

|VARTYPE|描述|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
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

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafearray:取得上部

傳回陣列中任何維度的上限。

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>參數

*烏迪姆*<br/>
要為其獲取上限的陣列維度。 如果省略,默認值為 0。

### <a name="return-value"></a>傳回值

返回上邊界。 此值是包含的,此維度的最大有效索引。

### <a name="remarks"></a>備註

例如,如果出現錯誤,此方法調用`AtlThrow`HRESULT 來描述錯誤。

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a>CComSafearray::可比

測試是否可以調整 `CComSafeArray` 物件大小。

```
bool IsSizable() const;
```

### <a name="return-value"></a>傳回值

如果 可以`CComSafeArray`調整 大小,則返回 TRUE,如果無法返回 FALSE。

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a>CComSafearray:m_psa

儲存存取的結構的`SAFEARRAY`位址 。

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComSafearray::多迪姆格拉特

從多維陣列中擷取單一項目。

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>參數

*阿爾指數*<br/>
指向陣列中每個維度的索引向量。 最左邊(最重要的)維度`alIndex[0]`是 。

*t*<br/>
對返回的數據的引用。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafearray::多迪姆塞特

設定多維陣列中的項目值。

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>參數

*阿爾指數*<br/>
指向陣列中每個維度的索引向量。 最右側(最不顯著)的維度是`alIndex`{0}。

*T*<br/>
指定新元素的值。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

這是[CComSafearray](#setat)的多維版本:setAt 。

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray::操作員\[\]

從陣列中擷取項目。

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>參數

*lIndex, nIndex*<br/>
陣列中所需元素的索引編號。

### <a name="return-value"></a>傳回值

返回相應的陣組元素。

### <a name="remarks"></a>備註

執行與[CComSafeArray::getAt](#getat)類似的功能,但是此運算符僅適用於單維陣組。

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray::操作員 |

指派運算子。

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>參數

*薩斯爾克*<br/>
`CComSafeArray` 物件的參考。

*普薩斯克*<br/>
`SAFEARRAY` 物件的指標。

### <a name="return-value"></a>傳回值

傳回陣列中儲存之資料的類型。

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafearray::操作員LPSAFEARRAY

將值強制轉換為`SAFEARRAY`指標。

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>傳回值

將值強制轉換為`SAFEARRAY`指標。

## <a name="ccomsafearrayresize"></a><a name="resize"></a>CComSafearray:調整大小

調整 `CComSafeArray` 物件大小。

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>參數

*p 繫結*<br/>
指向`SAFEARRAYBOUND`包含有關元素數和陣列下限的資訊的指標。

*ulCount*<br/>
調整陣列中請求的物件數。

*LLBound*<br/>
下限。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此方法僅調整最右側維度的大小。 它不會調整返回`IsResizable`為 FALSE 的陣列的大小。

## <a name="ccomsafearraysetat"></a><a name="setat"></a>CComSafearray::Setat

設定一維陣列中的項目值。

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>參數

*lIndex*<br/>
要設置的陣列元素的索引編號。

*t*<br/>
指定之項目的新值。

*bCopy*<br/>
指示是否應創建數據的副本。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

當將 BSTR 類型或 VARIANT 的元素添加到陣列時,將考慮*bCopy*標誌。 TRUE 的預設值可確保在元素添加到陣列時對資料進行新副本。

## <a name="see-also"></a>另請參閱

[SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[類別概觀](../../atl/atl-class-overview.md)
