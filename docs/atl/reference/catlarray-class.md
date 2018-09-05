---
title: CAtlArray 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f09bafd0bbda8a64b7a60fe6cacf996106385787
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753008"
---
# <a name="catlarray-class"></a>CAtlArray 類別

這個類別會實作陣列物件。

## <a name="syntax"></a>語法

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>參數

*E*  
陣列中儲存之資料的類型。

*ETraits*  
程式碼，用來複製或移動項目。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[[新增]](#add)|呼叫這個方法來新增元素至陣列物件。|
|[附加](#append)|呼叫這個方法，以加入另一個陣列的內容。|
|[AssertValid](#assertvalid)|呼叫這個方法來確認陣列物件有效。|
|[CAtlArray](#catlarray)|建構函式。|
|[~ CAtlArray](#dtor)|解構函式。|
|[複製](#copy)|呼叫這個方法來複製到另一個陣列的項目。|
|[FreeExtra](#freeextra)|呼叫這個方法，以從陣列中移除任何空的項目。|
|[GetAt](#getat)|呼叫這個方法來擷取陣列物件中的單一項目。|
|[GetCount](#getcount)|呼叫這個方法來傳回儲存在陣列中的項目數目。|
|[GetData](#getdata)|呼叫這個方法來傳回陣列中的第一個元素的指標。|
|[InsertArrayAt](#insertarrayat)|呼叫這個方法來插入另一個陣列。|
|[InsertAt](#insertat)|陣列物件呼叫這個方法，以插入新項目 （或多個項目複本）。|
|[IsEmpty](#isempty)|呼叫這個方法來測試是否為空陣列。|
|[RemoveAll](#removeall)|呼叫這個方法來移除陣列物件中的所有項目。|
|[RemoveAt](#removeat)|呼叫這個方法，以從陣列中移除一或多個項目。|
|[SetAt](#setat)|呼叫此方法以設定項目的值的陣列物件中。|
|[SetAtGrow](#setatgrow)|呼叫此方法以設定項目的值在陣列物件中，展開所需的陣列。|
|[SetCount](#setcount)|呼叫此方法以設定陣列物件的大小。|

### <a name="operators"></a>運算子

|||
|-|-|
|[運算子&#91;&#93;](#operator_at)|呼叫此運算子來傳回陣列中項目的參考。|  

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE](#inargtype)|要用於將項目加入至陣列的資料類型。|
|[OUTARGTYPE](#outargtype)|要用來擷取陣列中的項目資料型別。|

## <a name="remarks"></a>備註

`CAtlArray` 提供方法來建立和管理的使用者定義型別項目陣列。 雖然類似標準 C 陣列，`CAtlArray`物件可以動態壓縮和視需要成長。 陣列索引一律會啟動在位置 0，並可以固定的或允許加入新項目時，依序展開上限。

陣列的項目，ATL 類別數目很少[CSimpleArray](../../atl/reference/csimplearray-class.md)可用。

`CAtlArray` 與 MFC 的密切相關`CArray`類別，並能在 MFC 專案中，儘管不序列化支援。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="add"></a>  CAtlArray::Add

呼叫這個方法來新增元素至陣列物件。

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>參數

*項目*  
要加入至陣列的項目。

### <a name="return-value"></a>傳回值

傳回加入之項目的索引。

### <a name="remarks"></a>備註

新的項目會加入至陣列的結尾。 如果沒有任何項目提供，加入空白項目;也就是陣列會增加的大小，就好像已加入實際的項目。 如果作業失敗， [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) E_OUTOFMEMORY 的引數呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

##  <a name="append"></a>  CAtlArray::Append

呼叫這個方法，以加入另一個陣列的內容。

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>參數

*aSrc*  
要附加的陣列。

### <a name="return-value"></a>傳回值

傳回第一個附加的項目索引。

### <a name="remarks"></a>備註

提供的陣列中的項目會加入至現有陣列的結尾。 如有必要，則會配置記憶體，以容納新的項目。

陣列必須是相同的型別，並不是可附加至其本身的陣列。

在偵錯組建 ATLASSERT 如果就會引發`CAtlArray`引數不是有效的陣列或如果*aSrc*指的是相同的物件。 在發行組建中的引數無效，可能會導致無法預期的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

##  <a name="assertvalid"></a>  CAtlArray::AssertValid

呼叫這個方法來確認陣列物件有效。

```
void AssertValid() const;
```

### <a name="remarks"></a>備註

如果陣列物件不是有效的 ATLASSERT 會擲回判斷提示。 這個方法是在定義 _DEBUG 時，才提供使用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

##  <a name="catlarray"></a>  CAtlArray::CAtlArray

建構函式。

```
CAtlArray() throw();
```

### <a name="remarks"></a>備註

初始化陣列的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

##  <a name="dtor"></a>  CAtlArray:: ~ CAtlArray

解構函式。

```
~CAtlArray() throw();
```

### <a name="remarks"></a>備註

釋放任何陣列物件所使用的資源。

##  <a name="copy"></a>  CAtlArray::Copy

呼叫這個方法來複製到另一個陣列的項目。

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>參數

*aSrc*  
要複製到陣列之項目的來源。

### <a name="remarks"></a>備註

呼叫這個方法來覆寫的一個陣列的項目與另一個陣列的項目。 如有必要，則會配置記憶體，以容納新的項目。 您不可能將陣列的元素複製到本身。

如果要保留現有陣列的內容，請使用[CAtlArray::Append](#append)改。

在偵錯組建 ATLASSERT 若系統將產生的現有`CAtlArray`物件不是有效的或者如果*aSrc*指的是相同的物件。 在發行組建中的引數無效，可能會導致無法預期的行為。

> [!NOTE]
> `CAtlArray::Copy` 不支援使用建立的項目所組成的陣列[CAutoPtr](../../atl/reference/cautoptr-class.md)類別。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

##  <a name="freeextra"></a>  CAtlArray::FreeExtra

呼叫這個方法，以從陣列中移除任何空的項目。

```
void FreeExtra() throw();
```

### <a name="remarks"></a>備註

移除任何空的項目，但大小和陣列的上限維持不變。

在偵錯組建中，如果 CAtlArray 物件無效，或如果陣列超過大小上限，就會引發 ATLASSERT。

##  <a name="getat"></a>  CAtlArray::GetAt

呼叫這個方法，以從陣列物件中擷取單一項目。

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>參數

*iElement*  
要傳回之陣列元素的索引值。

### <a name="return-value"></a>傳回值

傳回所需的陣列元素的參考。

### <a name="remarks"></a>備註

在偵錯組建 ATLASSERT 如果就會引發*iElement*超過陣列中的項目數。 在發行組建中無效的引數可能會導致無法預期的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

##  <a name="getcount"></a>  CAtlArray::GetCount

呼叫這個方法來傳回儲存在陣列中的項目數目。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回儲存在陣列中的項目數目。

### <a name="remarks"></a>備註

因為陣列中的第一個項目是在位置 0，所傳回的值`GetCount`永遠為 1 大於最大的索引。

### <a name="example"></a>範例

範例，請參閱[CAtlArray::GetAt](#getat)。

##  <a name="getdata"></a>  CAtlArray::GetData

呼叫這個方法來傳回陣列中的第一個元素的指標。

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>傳回值

傳回儲存在陣列中的第一個項目之記憶體位置的指標。 如果有任何項目，則會傳回 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

##  <a name="inargtype"></a>  CAtlArray::INARGTYPE

要用於將項目加入至陣列的資料類型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt

呼叫這個方法來插入另一個陣列。

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>參數

*iStart*  
陣列是要插入的索引。

*paNew*  
要插入的陣列。

### <a name="remarks"></a>備註

從陣列的項目*paNew*複製到陣列物件，開始於項目*iStart*。 現有的陣列項目會移至避免遭到覆寫。

在偵錯組建 ATLASSERT 如果就會引發`CAtlArray`物件不是有效的或者如果*paNew*指標為 NULL 或無效。

> [!NOTE]
> `CAtlArray::InsertArrayAt` 不支援使用建立的項目所組成的陣列[CAutoPtr](../../atl/reference/cautoptr-class.md)類別。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

##  <a name="insertat"></a>  CAtlArray::InsertAt

陣列物件呼叫這個方法，以插入新項目 （或多個項目複本）。

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>參數

*iElement*  
索引中的項目或項目會插入。

*項目*  
要插入的元素值。

*nCount*  
若要新增的項目數目。

### <a name="remarks"></a>備註

一或多個項目插入陣列索引處開始*iElement*。 現有的項目會移至避免遭到覆寫。

在偵錯組建 ATLASSERT 若系統將產生`CAtlArray`物件無效，要加入的項目數為零，或合併的項目數太大，要包含的陣列。 在零售組建中傳遞無效的參數可能會造成無法預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

##  <a name="isempty"></a>  CAtlArray::IsEmpty

呼叫這個方法來測試是否為空陣列。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果陣列是空的 false 否則，就會傳回 true。

### <a name="remarks"></a>備註

是稱為陣列，如果它不包含任何項目是空的。 因此，即使陣列會包含空的項目，它是不空的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

##  <a name="operator_at"></a>  CAtlArray::operator]

呼叫此運算子來傳回陣列中項目的參考。

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>參數

*iElement*  
要傳回之陣列元素的索引值。

### <a name="return-value"></a>傳回值

傳回所需的陣列元素的參考。

### <a name="remarks"></a>備註

執行類似的功能[CAtlArray::GetAt](#getat)。 不同於 MFC 類別[CArray](../../mfc/reference/carray-class.md)，這個運算子不能取代[CAtlArray::SetAt](#setat)。

在偵錯組建 ATLASSERT 如果就會引發*iElement*超過陣列中的項目總數。 在零售組建中，無效的參數可能會造成無法預期的結果。

##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE

要用來擷取陣列中的項目資料型別。

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

##  <a name="removeall"></a>  CAtlArray::RemoveAll

呼叫這個方法來移除陣列物件中的所有項目。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

從陣列物件中移除所有項目。

這個方法會呼叫[CAtlArray::SetCount](#setcount)調整陣列的大小和後續釋放已配置的記憶體。

### <a name="example"></a>範例

範例，請參閱[CAtlArray::IsEmpty](#isempty)。

##  <a name="removeat"></a>  CAtlArray::RemoveAt

呼叫這個方法，以從陣列中移除一或多個項目。

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>參數

*iElement*  
要移除之第一個項目的索引。

*nCount*  
要移除的項目數目。

### <a name="remarks"></a>備註

從陣列中移除一或多個項目。 任何其餘的項目會向下移動。 上限就會減少，但呼叫之前，不釋放記憶體[CAtlArray::FreeExtra](#freeextra)為止。

在偵錯組建 ATLASSERT 如果就會引發`CAtlArray`物件不是有效的或如果合併的總計*iElement*和*nCount*超過陣列中的項目總數。 在零售組建中，無效的參數可能會造成無法預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

##  <a name="setat"></a>  CAtlArray::SetAt

呼叫此方法以設定項目的值的陣列物件中。

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>參數

*iElement*  
指向要設定之陣列元素的索引。

*項目*  
指定的項目新值。

### <a name="remarks"></a>備註

在偵錯組建 ATLASSERT 如果就會引發*iElement*超過陣列中的項目數。 在零售組建中，無效的參數可能會導致無法預期的結果。

### <a name="example"></a>範例

範例，請參閱[CAtlArray::GetAt](#getat)。

##  <a name="setcount"></a>  CAtlArray::SetCount

呼叫此方法以設定陣列物件的大小。

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>參數

*nNewSize*  
陣列所需的大小。

*nGrowBy*  
用來判斷的值將緩衝區的大小。 -1 值會導致使用內部導出的值。

### <a name="return-value"></a>傳回值

如果陣列不成功的調整大小，則為 false，則傳回 true。

### <a name="remarks"></a>備註

陣列可以增加或減少的大小。 如果增加，額外的空白項目會加入至陣列。 如果減少，以最大索引的項目將被刪除，並釋放記憶體。

這個方法可用於使用之前，先設定陣列的大小。 如果`SetCount`未使用的新增項目程序-執行後續的記憶體配置和 — 會降低效能，並讓記憶體分段。

### <a name="example"></a>範例

範例，請參閱[CAtlArray::GetData](#getdata)。

##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow

呼叫此方法以設定項目的值在陣列物件中，展開所需的陣列。

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>參數

*iElement*  
指向要設定之陣列元素的索引。

*項目*  
指定的項目新值。

### <a name="remarks"></a>備註

取代索引所指向的項目的值。 如果*iElement*大於目前大小的陣列，陣列就會自動增加使用的呼叫來[CAtlArray::SetCount](#setcount)。 在偵錯組建 ATLASSERT 若系統將產生`CAtlArray`物件無效。 在零售組建中，無效的參數可能會造成無法預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>另請參閱

[MMXSwarm 範例](../../visual-cpp-samples.md)   
[DynamicConsumer 範例](../../visual-cpp-samples.md)   
[UpdatePV 範例](../../visual-cpp-samples.md)   
[跑馬燈範例](../../visual-cpp-samples.md)   
[CArray 類別](../../mfc/reference/carray-class.md)   
[類別概觀](../../atl/atl-class-overview.md)
