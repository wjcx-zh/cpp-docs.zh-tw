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
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779842"
---
# <a name="carray-class"></a>CArray 類別

支援類似 C 陣列，但可以動態地減少或增加視的陣列。

## <a name="syntax"></a>語法

```
template <class TYPE, class ARG_TYPE = const TYPE&>
class CArray : public CObject
```

#### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在陣列中的物件類型的樣板參數。 *型別*是參數，由`CArray`。

*ARG_TYPE*<br/>
指定用來存取儲存在陣列中的物件的引數類型的樣板參數。 通常參考*型別*。 *Arg_type 這個*是參數，傳遞至`CArray`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CArray::CArray](#carray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CArray::Add](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CArray::Append](#append)|將其他陣列附加至的陣列;必要時讓陣列成長|
|[CArray::Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CArray::ElementAt](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CArray::FreeExtra](#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CArray::GetAt](#getat)|傳回給定索引的值。|
|[CArray::GetCount](#getcount)|取得此陣列中項目的數目。|
|[CArray::GetData](#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CArray::GetSize](#getsize)|取得此陣列中項目的數目。|
|[CArray::GetUpperBound](#getupperbound)|傳回最大的有效索引。|
|[CArray::InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CArray::IsEmpty](#isempty)|判斷是否為空陣列。|
|[CArray::RemoveAll](#removeall)|從此陣列移除所有項目。|
|[CArray::RemoveAt](#removeat)|移除特定索引處的項目。|
|[CArray::SetAt](#setat)|設定給定索引的值；不容許陣列成長。|
|[CArray::SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CArray::SetSize](#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator&#91;&#93;](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

陣列索引一律從開始位置 0。 您可以決定是否要修正的上限，或啟用展開，當您新增超過目前的繫結的項目陣列。 記憶體配置，連續的上限，即使某些項目都是 null。

> [!NOTE]
>  調整大小的大部分方法`CArray`物件，或新增項目，它會使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)移動項目。 這會是問題，因為`memcpy_s`任何需要的物件所要呼叫的建構函式與不相容。 如果中的項目`CArray`與不相容`memcpy_s`，您必須建立新`CArray`的適當的大小。 然後您必須使用[carray:: Copy](#copy)並[CArray::SetAt](#setat)用來填入新陣列，因為這些方法會使用指派運算子，而不是`memcpy_s`。

如同 C 陣列，存取時間`CArray`索引的項目為常數，而且是獨立的陣列大小。

> [!TIP]
>  使用陣列之前, 使用[SetSize](#setsize)建立其大小，並為它配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果您需要個別的項目陣列中的傾印，您必須設定的深度[CDumpContext](../../mfc/reference/cdumpcontext-class.md)為 1 或更大的物件。

全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分使用`CArray`類別。 請參閱主題[集合類別 Helper](../../mfc/reference/collection-class-helpers.md) MFC 巨集和全域變數一節。

陣列類別衍生，就像是清單衍生。

如需有關如何使用`CArray`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CArray`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

##  <a name="add"></a>  CArray::Add

加入新元素的陣列，陣列成長 1 結尾。

```
INT_PTR Add(ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定的引數參考此陣列中的項目類型的樣板參數。

*newElement*<br/>
要加入至這個陣列的項目。

### <a name="return-value"></a>傳回值

加入之項目的索引。

### <a name="remarks"></a>備註

如果[SetSize](#setsize)已`nGrowBy`可能配置大於 1，則額外的記憶體值。 不過，只有 1 將增加上限。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]

##  <a name="append"></a>  Carray:: Append

呼叫此成員函式，加入另一個陣列的內容。

```
INT_PTR Append(const CArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要附加至陣列項目的來源。

### <a name="return-value"></a>傳回值

第一個附加的項目索引。

### <a name="remarks"></a>備註

陣列必須是相同的型別。

如有必要，`Append`可能會配置額外的記憶體來容納附加至陣列的項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]

##  <a name="carray"></a>  CArray::CArray

建構空陣列。

```
CArray();
```

### <a name="remarks"></a>備註

陣列會增加一個項目，一次。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]

##  <a name="copy"></a>  CArray::Copy

使用此成員函式複製到另一個陣列的項目。

```
void Copy(const CArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要複製到陣列之項目的來源。

### <a name="remarks"></a>備註

呼叫此成員函式，以覆寫另一個陣列元素的一個陣列項目。

`Copy` 不會釋放記憶體;不過，如果有必要，`Copy`可能會配置額外的記憶體來容納的項目複製到陣列。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]

##  <a name="elementat"></a>  CArray::ElementAt

傳回指定的項目陣列中的臨時參考。

```
TYPE& ElementAt(INT_PTR nIndex);
const TYPE& ElementAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。

### <a name="return-value"></a>傳回值

陣列項目的參考。

### <a name="remarks"></a>備註

它用來實作陣列的左邊的指派運算子。

### <a name="example"></a>範例

  範例，請參閱[GetSize](#getsize)。

##  <a name="freeextra"></a>  CArray::FreeExtra

釋放任何額外的記憶體配置時已成長的陣列。

```
void FreeExtra();
```

### <a name="remarks"></a>備註

此函式無效的大小或陣列的上限。

### <a name="example"></a>範例

  範例，請參閱[GetData](#getdata)。

##  <a name="getat"></a>  CArray::GetAt

傳回指定索引處的陣列元素。

```
TYPE& GetAt(INT_PTR nIndex);
const TYPE& GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定的陣列元素的類型樣板參數。

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。

### <a name="return-value"></a>傳回值

目前在此索引陣列項目。

### <a name="remarks"></a>備註

傳遞負數的值所傳回的值大於`GetUpperBound`會導致失敗的判斷提示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]

##  <a name="getcount"></a>  CArray::GetCount

傳回陣列元素數目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

陣列中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法來擷取陣列中的項目數。 因為是以零起始的索引，大小為 1 大於最大的索引。 呼叫這個方法會產生相同結果[CArray::GetSize](#getsize)方法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]

##  <a name="getdata"></a>  CArray::GetData

您可以使用此成員函式來直接存取陣列中的項目。

```
const TYPE* GetData() const;
TYPE* GetData();
```

### <a name="parameters"></a>參數

*型別*<br/>
指定的陣列元素的類型樣板參數。

### <a name="return-value"></a>傳回值

陣列元素的指標。

### <a name="remarks"></a>備註

如果沒有項目可供使用，`GetData`傳回 null 值。

而直接存取陣列的項目可協助您更快速地運作，請呼叫時使用注意`GetData`; 您直接提出任何錯誤會影響您陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]

##  <a name="getsize"></a>  CArray::GetSize

傳回陣列的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>備註

因為是以零起始的索引，大小為 1 大於最大的索引。 呼叫這個方法會產生相同結果[CArray::GetCount](#getcount)方法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]

##  <a name="getupperbound"></a>  CArray::GetUpperBound

傳回目前的上限，此陣列。

```
INT_PTR GetUpperBound() const;
```

### <a name="remarks"></a>備註

因為是以零為起始的陣列索引，此函數會傳回 1 的值小於`GetSize`。

條件`GetUpperBound( )`=-1 表示陣列是否包含任何項目。

### <a name="example"></a>範例

  範例，請參閱[CArray::GetAt](#getat)。

##  <a name="insertat"></a>  CArray::InsertAt

第一版`InsertAt`陣列中指定索引處插入一個項目 （或多個項目複本）。

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
可能會大於所傳回的值的整數索引`GetUpperBound`。

*ARG_TYPE*<br/>
此陣列中指定的項目類型的樣板參數。

*newElement*<br/>
要放在這個陣列的項目。

*nCount*<br/>
次數，此項目應該插入 （預設值為 1）。

*nStartIndex*<br/>
可能會大於所傳回的值的整數索引[GetUpperBound](#getupperbound)。

*pNewArray*<br/>
另一個陣列，包含要加入至這個陣列的項目。

### <a name="remarks"></a>備註

在過程中，它會往上移動這個索引，並在現有的項目移位其上方的所有項目 （依遞增的索引）。

第二個版本會將所有項目插入從另一個`CArray`集合，從開始*nStartIndex*位置。

`SetAt`函式，相較之下，取代一個指定的陣列項目，並不會不位移任何項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]

##  <a name="isempty"></a>  CArray::IsEmpty

判斷是否為空陣列。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

非零值，如果陣列不包含任何項目;否則為 0。

##  <a name="operator_at"></a>  CArray::operator \[\]

這些註標運算子會很方便的替代[SetAt](#setat)並[GetAt](#getat)函式。

```
TYPE& operator[](int_ptr nindex);
const TYPE& operator[](int_ptr nindex) const;
```

### <a name="parameters"></a>參數

*型別*<br/>
此陣列中指定的項目類型的樣板參數。

*nIndex*<br/>
若要存取的項目索引。

### <a name="remarks"></a>備註

陣列未呼叫的第一個運算子**const**，可用於上的權限 （右值） 或指派陳述式左邊 （左值）。 第二個，呼叫**const**陣列可能只能用在右邊。

偵錯版本的程式庫判斷提示的註標 （請在左邊或右邊則在指派陳述式） 是否超出範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]

##  <a name="relocateelements"></a>  CArray::RelocateElements

當陣列應該成長或壓縮時，請重新資料放置到新的緩衝區。

```
template<class TYPE, class ARG_TYPE>
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,
    const TYPE* pData,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*pNewData*<br/>
新的緩衝區陣列的項目。

*pData*<br/>
項目的舊的陣列。

*nCount*<br/>
舊的陣列中的項目數目。

### <a name="remarks"></a>備註

*pNewData*一律為足以容納所有*pData*項目。

[CArray](../../mfc/reference/carray-class.md)實作會使用這個方法將舊的資料複製到新的緩衝區，當陣列應該成長或壓縮時 (當[SetSize](#setsize)或是[FreeExtra](#freeextra)稱為)。 預設實作只會複製資料。

陣列項目包含它自己的成員，其中的指標，或另一個結構包含的其中一個陣列元素的指標，指標中不會更新一般的複製。 在此情況下，您可以更正指標實作的特製化`RelocateElements`與相關的型別。 您也會負責將資料複製。

##  <a name="removeall"></a>  CArray::RemoveAll

從此陣列移除所有項目。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果已經為空陣列，此函式仍能運作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]

##  <a name="removeat"></a>  CArray::RemoveAt

移除陣列中的指定索引處開始的一或多個項目。

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。

*nCount*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

在過程中，它會進入關閉已移除的項目上方的所有項目。 它遞減右上角的陣列繫結，但不會釋放記憶體。

如果您嘗試移除比上述移除點陣列中包含的項目，然後判斷提示的程式庫的偵錯版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]

##  <a name="setat"></a>  CArray::SetAt

設定指定索引處的陣列項目。

```
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。

*ARG_TYPE*<br/>
指定用來參考陣列元素的引數的類型樣板參數。

*newElement*<br/>
新的項目值儲存在指定的位置。

### <a name="remarks"></a>備註

`SetAt` 不會造成要成長的陣列。 使用[SetAtGrow](#setatgrow)如果您想要自動成長的陣列。

您必須確定您的索引值代表陣列中的有效位置。 如果它超出範圍時，偵錯版本的程式庫判斷提示。

### <a name="example"></a>範例

  範例，請參閱[GetAt](#getat)。

##  <a name="setatgrow"></a>  CArray::SetAtGrow

設定指定索引處的陣列項目。

```
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 的整數索引。

*ARG_TYPE*<br/>
指定陣列中的項目類型的樣板參數。

*newElement*<br/>
要加入至這個陣列的項目。 允許 NULL 值。

### <a name="remarks"></a>備註

陣列在必要時自動成長 （亦即，以容納新的項目調整上限）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]

##  <a name="setsize"></a>  CArray::SetSize

建立空的或現有陣列; 的大小如有必要，請配置記憶體。

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>參數

*nNewSize*<br/>
新陣列的大小 （數字的項目）。 必須是大於或等於 0。

*nGrowBy*<br/>
如果是必要的大小增加配置的項目位置的數目下限。

### <a name="remarks"></a>備註

如果新的大小小於舊的大小，然後陣列會被截斷，並釋放所有未使用的記憶體。

此函式可用於開始使用陣列之前，設定您陣列的大小。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

*NGrowBy*參數會影響內部記憶體配置，而陣列成長。 其用途並不會影響陣列大小所回報[GetSize](#getsize)並[GetUpperBound](#getupperbound)。 如果使用預設值，MFC 會配置記憶體，以避免記憶體分散情形，並將效益最大化，在大部分情況下的計算的方式。

### <a name="example"></a>範例

  範例，請參閱[GetData](#getdata)。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)<br/>
[集合類別協助程式](../../mfc/reference/collection-class-helpers.md)
