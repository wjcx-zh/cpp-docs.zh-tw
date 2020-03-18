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
ms.openlocfilehash: f82dbf7dce2e14bf760bb76d23d23f667797ee0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418857"
---
# <a name="carray-class"></a>CArray 類別

支援類似 C 陣列的陣列，但可以視需要動態地減少和成長。

## <a name="syntax"></a>語法

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定儲存在陣列中的物件類型。 *類型*是 `CArray`所傳回的參數。

*ARG_TYPE*<br/>
範本參數，指定用來存取儲存在陣列中之物件的引數類型。 通常是*類型*的參考。 *ARG_TYPE*是傳遞給 `CArray`的參數。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CArray：： CArray](#carray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CArray：： Add](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CArray：： Append](#append)|將另一個陣列附加至陣列;視需要成長陣列|
|[CArray：： Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CArray：： Parameters.alternatefilters.elementat](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CArray：： FreeExtra](#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CArray：： GetAt](#getat)|傳回給定索引的值。|
|[CArray：： GetCount](#getcount)|取得此陣列中項目的數目。|
|[CArray：：操作](#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CArray：： GetSize](#getsize)|取得此陣列中項目的數目。|
|[CArray：： System.array.getupperbound](#getupperbound)|傳回最大的有效索引。|
|[CArray：： InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CArray：： IsEmpty](#isempty)|判斷陣列是否為空的。|
|[CArray：： RemoveAll](#removeall)|從此陣列移除所有項目。|
|[CArray：： RemoveAt](#removeat)|移除特定索引處的項目。|
|[CArray：： SetAt](#setat)|設定給定索引的值；不容許陣列成長。|
|[CArray：： SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CArray：： SetSize](#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

陣列索引一律從位置0開始。 您可以決定是否要修正上限，或在您加入超出目前系結的元素時，讓陣列展開。 記憶體會連續配置給上限，即使某些元素是 null 也一樣。

> [!NOTE]
>  大部分的方法會調整 `CArray` 物件的大小，或將專案加入其中，使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)來移動元素。 這是一個問題，因為 `memcpy_s` 與需要呼叫此函式的任何物件不相容。 如果 `CArray` 中的專案與 `memcpy_s`不相容，您必須建立適當大小的新 `CArray`。 接著，您必須使用[CArray：： Copy](#copy)和[CArray：： SetAt](#setat)來填入新的陣列，因為這些方法會使用指派運算子，而不是 `memcpy_s`。

如同 C 陣列，`CArray` 索引元素的存取時間是常數，而且與陣列大小無關。

> [!TIP]
>  使用陣列之前，請使用[SetSize](#setsize)來建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果您需要陣列中個別元素的傾印，您必須將[CDumpCoNtext](../../mfc/reference/cdumpcontext-class.md)物件的深度設定為1或更大。

這個類別的某些成員函式會呼叫全域 helper 函式，而這些函式必須針對 `CArray` 類別的大部分使用進行自訂。 請參閱 MFC 宏和全域區段中的[集合類別](../../mfc/reference/collection-class-helpers.md)協助程式主題。

陣列類別衍生類似于清單衍生。

如需如何使用 `CArray`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

##  <a name="add"></a>CArray：： Add

將新的專案加入至陣列的結尾，並將陣列增加1。

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
範本參數，指定參考此陣列中元素的引數類型。

*newElement*<br/>
要加入至此陣列的元素。

### <a name="return-value"></a>傳回值

已加入之元素的索引。

### <a name="remarks"></a>備註

如果[SetSize](#setsize)與大於1的 `nGrowBy` 值搭配使用，則可能會配置額外的記憶體。 不過，上限只會增加1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>CArray：： Append

呼叫這個成員函式，將一個陣列的內容加入至另一個陣列的結尾。

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要附加至陣列之元素的來源。

### <a name="return-value"></a>傳回值

第一個附加元素的索引。

### <a name="remarks"></a>備註

陣列必須是相同的類型。

如有必要，`Append` 可能會配置額外的記憶體，以容納附加至陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>CArray：： CArray

建構空陣列。

```
CArray();
```

### <a name="remarks"></a>備註

陣列會一次增加一個元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>CArray：： Copy

使用此成員函式，將某個陣列的元素複製到另一個。

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要複製到陣列之元素的來源。

### <a name="remarks"></a>備註

呼叫這個成員函式，以另一個陣列的元素覆寫某個陣列的元素。

`Copy` 無法釋放記憶體;不過，如有必要，`Copy` 可能會配置額外的記憶體，以容納複製到陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>CArray：： Parameters.alternatefilters.elementat

傳回陣列中所指定專案的暫存參考。

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於[system.array.getupperbound](#getupperbound)所傳回之值的整數索引。

### <a name="return-value"></a>傳回值

陣列元素的參考。

### <a name="remarks"></a>備註

它是用來實作為陣列的左端指派運算子。

### <a name="example"></a>範例

  請參閱[GetSize](#getsize)的範例。

##  <a name="freeextra"></a>CArray：： FreeExtra

釋放陣列成長時所配置的任何額外記憶體。

```
void FreeExtra();
```

### <a name="remarks"></a>備註

此函式不會影響陣列的大小或上限。

### <a name="example"></a>範例

  請參閱[「程式」的範例](#getdata)。

##  <a name="getat"></a>CArray：： GetAt

傳回指定索引處的陣列元素。

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定陣列元素的類型。

*nIndex*<br/>
大於或等於0，且小於或等於[system.array.getupperbound](#getupperbound)所傳回之值的整數索引。

### <a name="return-value"></a>傳回值

目前位於此索引的陣列元素。

### <a name="remarks"></a>備註

傳遞負值或大於 `GetUpperBound` 所傳回之值的值，會導致失敗的判斷提示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>CArray：： GetCount

傳回陣列元素的數目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

陣列中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法來抓取陣列中的元素數目。 因為索引是以零為起始，所以大小為1，大於最大的索引。 呼叫這個方法將會產生與[CArray：： GetSize](#getsize)方法相同的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>CArray：：操作

使用這個成員函式，取得陣列中元素的直接存取權。

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定陣列元素的類型。

### <a name="return-value"></a>傳回值

陣列元素的指標。

### <a name="remarks"></a>備註

如果沒有可用的元素，`GetData` 會傳回 null 值。

雖然直接存取陣列的元素可以協助您更快速地工作，但在呼叫 `GetData`時請務必小心。您所做的任何錯誤都會直接影響陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>CArray：： GetSize

傳回陣列的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>備註

因為索引是以零為起始，所以大小為1，大於最大的索引。 呼叫這個方法將會產生與[CArray：： GetCount](#getcount)方法相同的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>CArray：： System.array.getupperbound

傳回這個陣列的目前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>備註

因為陣列索引是以零為基底，所以此函式會傳回小於 `GetSize`的值1。

條件 `GetUpperBound( )` =-1 表示陣列未包含任何元素。

### <a name="example"></a>範例

  請參閱[CArray：： GetAt](#getat)的範例。

##  <a name="insertat"></a>CArray：： InsertAt

第一個版本的 `InsertAt` 會在陣列中的指定索引處插入一個專案（或多個元素複本）。

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
可能大於 `GetUpperBound`所傳回之值的整數索引。

*ARG_TYPE*<br/>
範本參數，指定此陣列中元素的類型。

*newElement*<br/>
要放置在這個陣列中的元素。

*nCount*<br/>
此元素應該插入的次數（預設為1）。

*nStartIndex*<br/>
可能大於[system.array.getupperbound](#getupperbound)所傳回之值的整數索引。

*pNewArray*<br/>
另一個陣列，其中包含要加入至此陣列的元素。

### <a name="remarks"></a>備註

在此程式中，它會在此索引上轉移現有的專案（藉由遞增索引），並向上移動其上方的所有元素。

第二個版本會從*nStartIndex*位置開始，插入另一個 `CArray` 集合中的所有元素。

相反地，`SetAt` 函式會取代一個指定的陣列元素，而不會將任何元素移位。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>CArray：： IsEmpty

判斷陣列是否為空的。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果陣列不包含任何元素，則為非零。否則為0。

##  <a name="operator_at"></a>CArray：： operator \[\]

這些注標運算子是[SetAt](#setat)和[GetAt](#getat)函數的方便替代。

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定此陣列中元素的類型。

*nIndex*<br/>
要存取之元素的索引。

### <a name="remarks"></a>備註

第一個運算子（針對不是**const**的陣列呼叫）可用於指派語句的右邊（右值）或左邊（左值）。 第二個（針對**const**陣列呼叫）只能用在右邊。

如果注標（在指派語句的左邊或右邊）超出範圍，則為該程式庫的 Debug 版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>CArray：： RelocateElements

當陣列應該增加或縮小時，將資料重新放置到新的緩衝區。

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
舊的元素陣列。

*nCount*<br/>
舊陣列中的元素數目。

### <a name="remarks"></a>備註

*pNewData*一律夠大，足以容納所有的*pData*元素。

當陣列應該增加或縮小（呼叫[SetSize](#setsize)或[FreeExtra](#freeextra)時）時， [CArray](../../mfc/reference/carray-class.md)執行會使用這個方法將舊資料複製到新的緩衝區。 預設的執行只會複製資料。

若為數組，其中的元素包含其中一個成員的指標，或另一個結構包含其中一個陣列元素的指標，則不會以純複製更新指標。 在此情況下，您可以藉由使用相關類型來執行 `RelocateElements` 的特製化來更正指標。 您也會負責資料複製。

##  <a name="removeall"></a>CArray：： RemoveAll

從此陣列移除所有項目。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果陣列已經是空的，函數仍然可以運作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>CArray：： RemoveAt

從陣列中的指定索引處開始移除一或多個元素。

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於[system.array.getupperbound](#getupperbound)所傳回之值的整數索引。

*nCount*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

在進程中，它會向下移動已移除專案上方的所有元素。 它會遞減陣列的上限，但不會釋放記憶體。

如果您嘗試移除超過移除點上方陣列中所包含的更多元素，則會進行程式庫判斷提示的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>CArray：： SetAt

設定指定索引處的陣列元素。

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於[system.array.getupperbound](#getupperbound)所傳回之值的整數索引。

*ARG_TYPE*<br/>
範本參數，指定用於參考陣列元素的引數類型。

*newElement*<br/>
要儲存在指定位置的新元素值。

### <a name="remarks"></a>備註

`SetAt` 不會造成陣列成長。 如果您想要讓陣列自動成長，請使用[SetAtGrow](#setatgrow) 。

您必須確定您的索引值代表陣列中的有效位置。 如果超出範圍，則為程式庫判斷提示的調試版本。

### <a name="example"></a>範例

  請參閱[GetAt](#getat)的範例。

##  <a name="setatgrow"></a>CArray：： SetAtGrow

設定指定索引處的陣列元素。

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0的整數索引。

*ARG_TYPE*<br/>
範本參數，指定陣列中元素的類型。

*newElement*<br/>
要加入至此陣列的元素。 允許 Null 值。

### <a name="remarks"></a>備註

如有必要，陣列會自動成長（也就是會調整上限以容納新的元素）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>CArray：： SetSize

建立空白或現有陣列的大小;視需要配置記憶體。

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>參數

*nNewSize*<br/>
新的陣列大小（元素數目）。 必須大於或等於 0。

*nGrowBy*<br/>
如果需要增加大小，要配置的元素位置數目下限。

### <a name="remarks"></a>備註

如果新的大小小於舊的大小，則會截斷陣列，並釋放所有未使用的記憶體。

開始使用陣列之前，請使用此函式來設定陣列的大小。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

當陣列正在成長時， *nGrowBy*參數會影響內部記憶體配置。 其使用方式永遠不會影響[GetSize](#getsize)和[system.array.getupperbound](#getupperbound)所報告的陣列大小。 如果使用預設值，MFC 會以計算的方式配置記憶體，以避免記憶體分散，並在大多數情況下將效率優化。

### <a name="example"></a>範例

  請參閱[「程式」的範例](#getdata)。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)<br/>
[集合類別協助程式](../../mfc/reference/collection-class-helpers.md)
