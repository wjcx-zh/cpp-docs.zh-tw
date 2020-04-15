---
title: CArray 類別
ms.date: 11/04/2016
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
ms.openlocfilehash: 2c520a732edf54ebb36c07728ceb19791b351143
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377029"
---
# <a name="carray-class"></a>CArray 類別

支持類似於 C 陣列的陣列,但可以根據需要動態減少和增長。

## <a name="syntax"></a>語法

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>參數

*類型*<br/>
指定陣列中儲存的物件類型的範本參數。 *TYPE*是返回`CArray`的 參數。

*ARG_TYPE*<br/>
指定用於存取陣列中儲存物件的參數類型的範本參數。 通常參考*TYPE*。 *ARG_TYPE*是傳遞`CArray`給的參數。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CArray:CArray](#carray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CArray::新增](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CArray::追加](#append)|將另一個陣列追加到陣列中;如有必要,增大陣列|
|[CArray::複製](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[Carray::元素At](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CArray::免費額外](#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[Carray:getat](#getat)|傳回給定索引的值。|
|[CArray:取得計數](#getcount)|取得此陣列中項目的數目。|
|[CArray:取得資料](#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CArray:取得 Size](#getsize)|取得此陣列中項目的數目。|
|[Carray:抓取上部](#getupperbound)|傳回最大的有效索引。|
|[Carray::插入At](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[陣列::為空](#isempty)|確定陣列是否為空。|
|[Carray::刪除所有](#removeall)|從此陣列移除所有項目。|
|[陣列::刪除 AT](#removeat)|移除特定索引處的項目。|
|[Carray::Setat](#setat)|設定給定索引的值；不容許陣列成長。|
|[Carray:setat增長](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CArray::設定大小](#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

陣列索引始終從位置 0 開始。 您可以決定是否修復上限,還是使陣列在添加超過當前綁定的元素時展開。 即使某些元素為空,記憶體也會連續分配給上限。

> [!NOTE]
> 大多數調整`CArray`物件大小或向其添加元素的方法都使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)來移動元素。 這是一個問題,因為`memcpy_s`與需要調用構造函數的任何物件不相容。 如果`CArray`中的項`memcpy_s`與不相容,則必須創建適當大小`CArray`的新項。 然後,您必須使用[CArray::copy](#copy)和[CArray:setAt](#setat)來填充新陣列,因為這些方法使用賦`memcpy_s`值運算子 而不是 。

與 C 陣列一`CArray`樣, 索引元素的訪問時間是恆定的,並且與陣列大小無關。

> [!TIP]
> 在使用陣列之前,請使用[SetSize](#setsize)來建立其大小併為其分配記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果需要陣列中單個元素的轉儲,則必須將[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件的深度設置為 1 或更大。

此類的某些成員函數調用全域説明器函數,這些函數必須針對`CArray`類的大多數用途進行自定義。 請參考 MFC 巨集與全域部分中的主題[集合類別說明器](../../mfc/reference/collection-class-helpers.md)。

陣列類派生類似於清單派生。

有關如何使用的詳細資訊`CArray`,請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="carrayadd"></a><a name="add"></a>CArray::新增

將新元素添加到陣列的末尾,將陣列增加1。

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定參考此陣列元素的參數類型的樣本參數。

*新元素*<br/>
要添加到此陣列的元素。

### <a name="return-value"></a>傳回值

添加元素的索引。

### <a name="remarks"></a>備註

如果[SetSize](#setsize)`nGrowBy`已使用的值大於 1,則可能會分配額外的記憶體。 但是,上限僅增加 1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

## <a name="carrayappend"></a><a name="append"></a>CArray::追加

調用此成員函數將一個陣列的內容添加到另一個陣列的末尾。

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要追加到陣列的元素的源。

### <a name="return-value"></a>傳回值

第一個附加元素的索引。

### <a name="remarks"></a>備註

陣列必須具有相同的類型。

如有必要,`Append`可以分配額外的記憶體以容納追加到陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

## <a name="carraycarray"></a><a name="carray"></a>CArray:CArray

建構空陣列。

```
CArray();
```

### <a name="remarks"></a>備註

陣列一次增加一個元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

## <a name="carraycopy"></a><a name="copy"></a>CArray::複製

使用此成員函數將一個陣列的元素複製到另一個陣列。

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要複製到陣列的元素的源。

### <a name="remarks"></a>備註

呼叫此成員函數以用另一個陣列的元素覆蓋一個陣列的元素。

`Copy`不釋放記憶體;但是,如有必要,`Copy`可能會分配額外的記憶體以適應複製到陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

## <a name="carrayelementat"></a><a name="elementat"></a>Carray::元素At

返回對陣列中指定元素的臨時引用。

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等於[GetUpperBound](#getupperbound)返回的值的整數索引。

### <a name="return-value"></a>傳回值

對陣列元素的引用。

### <a name="remarks"></a>備註

它用於實現陣列的左側賦值運算符。

### <a name="example"></a>範例

  請參考[GetSize 的範例](#getsize)。

## <a name="carrayfreeextra"></a><a name="freeextra"></a>CArray::免費額外

釋放在陣列增長時分配的任何額外記憶體。

```
void FreeExtra();
```

### <a name="remarks"></a>備註

此函數對陣列的大小或上限沒有影響。

### <a name="example"></a>範例

  請參閱[GetData](#getdata)的範例。

## <a name="carraygetat"></a><a name="getat"></a>Carray:getat

在指定的索引處返回陣列元素。

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
指定陣列元素類型的範本參數。

*nIndex*<br/>
大於或等於 0 且小於或等於[GetUpperBound](#getupperbound)返回的值的整數索引。

### <a name="return-value"></a>傳回值

當前位於此索引的陣列元素。

### <a name="remarks"></a>備註

傳遞負值或大於返回`GetUpperBound`的值的值將導致斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

## <a name="carraygetcount"></a><a name="getcount"></a>CArray:取得計數

返回陣列元素的數量。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

陣列中的項目數目。

### <a name="remarks"></a>備註

調用此方法以檢索陣列中的元素數。 由於索引是零基的,因此大小大於最大索引的 1。 調用此方法將生成與[CArray::getSize](#getsize)方法相同的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

## <a name="carraygetdata"></a><a name="getdata"></a>CArray:取得資料

使用此成員函數可以直接訪問陣列中的元素。

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>參數

*類型*<br/>
指定陣列元素類型的範本參數。

### <a name="return-value"></a>傳回值

指向陣列元素的指標。

### <a name="remarks"></a>備註

如果沒有可用的元素,`GetData`則傳回 null 值。

雖然直接存取陣列的元素可以説明您更快地工作,但呼`GetData`叫 時請謹慎操作 。您犯的任何錯誤都會直接影響陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

## <a name="carraygetsize"></a><a name="getsize"></a>CArray:取得 Size

傳回陣列的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>備註

由於索引是零基的,因此大小大於最大索引的 1。 調用此方法將生成與[CArray::getCount](#getcount)方法相同的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

## <a name="carraygetupperbound"></a><a name="getupperbound"></a>Carray:抓取上部

返回此陣列的當前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>備註

由於陣列索引是零基的,因此此函數傳回的值 1`GetSize`小於 。

條件`GetUpperBound( )`= -1 表示陣列不包含任何元素。

### <a name="example"></a>範例

  請參閱[CArray::getAt](#getat)的範例。

## <a name="carrayinsertat"></a><a name="insertat"></a>Carray::插入At

第一個版本在`InsertAt`數位中的指定索引中插入一個元素(或元素的多個副本)。

```
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CArray* pNewArray);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
可能大於返回`GetUpperBound`的值的整數索引。

*ARG_TYPE*<br/>
指定此陣列中元素類型的範本參數。

*新元素*<br/>
要放置在此陣列中的元素。

*n( N) Count*<br/>
應插入此元素的次數(預設值為1)。

*nStartIndex*<br/>
可能大於[GetUpperBound](#getupperbound)返回的值的整數索引。

*pNewArray*<br/>
另一個包含要添加到此陣列的元素的陣列。

### <a name="remarks"></a>備註

在此過程中,它向上移動(通過增加索引)此索引中的現有元素,並向上移動其上方的所有元素。

第二個版本從*nStartIndex*位置`CArray`開始插入另一個集合中的所有元素。

相反`SetAt`,函數替換一個指定的陣列元素,並且不移動任何元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

## <a name="carrayisempty"></a><a name="isempty"></a>陣列::為空

確定陣列是否為空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果陣列不包含任何元素,則非零;否則 0。

## <a name="carrayoperator-"></a><a name="operator_at"></a>CArray::運算子\[\]

這些下標運算符是[SetAt](#setat)和[GetAt](#getat)函數的便捷替代。

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
指定此陣列中元素類型的範本參數。

*nIndex*<br/>
要訪問的元素的索引。

### <a name="remarks"></a>備註

第一個運算符(稱為非**const**陣列)可以在賦值語句的右側(r 值)或左側(l 值)上使用。 第二個,稱為**const**陣列,只能在右側使用。

庫的調試版本斷言下標(在賦值語句的左側或右側)是否超出邊界。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

## <a name="carrayrelocateelements"></a><a name="relocateelements"></a>CArray::重新置放元素

當陣列應增長或收縮時,將數據重新置放到新緩衝區。

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*pNewData*<br/>
元素陣列的新緩衝區。

*pData*<br/>
元素的舊陣列。

*n( N) Count*<br/>
舊陣列中的元素數。

### <a name="remarks"></a>備註

*pNewData*始終足夠大,可以容納所有*pData*元素。

當陣列應成長或收縮時(當呼叫[SetSize](#setsize)或[FreeExtra](#freeextra)時[),CArray](../../mfc/reference/carray-class.md)實現使用此方法將舊資料複製到新緩衝區。 預設實現僅複製數據。

對於元素包含指向其自己的成員之一的指標或其他結構包含指向其中一個陣列元素的指標的陣列,指標不會以純副本更新。 在這種情況下,您可以通過使用相關類型的實現專業`RelocateElements`化 來更正指標。 您還負責資料複製。

## <a name="carrayremoveall"></a><a name="removeall"></a>Carray::刪除所有

從此陣列移除所有項目。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果數組已為空,則函數仍然有效。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

## <a name="carrayremoveat"></a><a name="removeat"></a>陣列::刪除 AT

刪除從陣列中指定索引開始的一個或多個元素。

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等於[GetUpperBound](#getupperbound)返回的值的整數索引。

*n( N) Count*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

在此過程中,它會向下移動刪除的元素上方的所有元素。 它會遞減陣列的上限,但不釋放記憶體。

如果嘗試刪除的元素多於刪除點上方的陣列中包含的元素,則庫的調試版本斷言。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

## <a name="carraysetat"></a><a name="setat"></a>Carray::Setat

在指定的索引處設置陣列元素。

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等於[GetUpperBound](#getupperbound)返回的值的整數索引。

*ARG_TYPE*<br/>
樣本參數,指定用於引用陣列元素的參數類型。

*新元素*<br/>
要存儲在指定位置的新元素值。

### <a name="remarks"></a>備註

`SetAt`不會導致陣組增長。 如果您希望陣列自動增長,請使用[SetAtGrow。](#setatgrow)

必須確保索引值表示陣列中的有效位置。 如果它超出邊界,則庫的調試版本斷言。

### <a name="example"></a>範例

  請參閱[GetAt](#getat)的範例。

## <a name="carraysetatgrow"></a><a name="setatgrow"></a>Carray:setat增長

在指定的索引處設置陣列元素。

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 的整數索引。

*ARG_TYPE*<br/>
指定陣列元素類型的樣本參數。

*新元素*<br/>
要添加到此陣列的元素。 允許 NULL 值。

### <a name="remarks"></a>備註

如有必要,陣列會自動增長(即,調整上限以適應新元素)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

## <a name="carraysetsize"></a><a name="setsize"></a>CArray::設定大小

建立空陣組或現有陣列的大小;如有必要,分配記憶體。

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>參數

*n 新尺寸*<br/>
新的陣列大小(元素數)。 必須大於或等於 0。

*nGrowBy*<br/>
如果需要增加大小,要分配的最小元素槽數。

### <a name="remarks"></a>備註

如果新大小小於舊大小,則陣列將被截斷,並釋放所有未使用的記憶體。

在開始使用陣列之前,使用此函數設置陣列的大小。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

*nGrowBy*參數在陣列增長時影響內部記憶體分配。 其使用永遠不會影響[GetSize](#getsize)和[GetUpperBound](#getupperbound)報告的陣列大小。 如果使用預設值,MFC 會以計算的方式分配記憶體,以避免記憶體碎片,並優化大多數情況下的效率。

### <a name="example"></a>範例

  請參閱[GetData](#getdata)的範例。

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)<br/>
[集合類別協助程式](../../mfc/reference/collection-class-helpers.md)
