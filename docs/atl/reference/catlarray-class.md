---
title: CAtlArray 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: c4a4cd509a5d3078c6587ba7b29179a68912a258
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833838"
---
# <a name="catlarray-class"></a>CAtlArray 類別

這個類別會執行陣列物件。

## <a name="syntax"></a>語法

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

### <a name="parameters"></a>參數

*Pci-e*<br/>
陣列中儲存之資料的類型。

*ETraits*<br/>
用來複製或移動元素的程式碼。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|函式|描述|
|-|-|
|[加入](#add)|呼叫這個方法，將專案加入至陣列物件。|
|[Append](#append)|呼叫這個方法，將某個陣列的內容加入至另一個陣列的結尾。|
|[AssertValid](#assertvalid)|呼叫這個方法來確認陣列物件是否有效。|
|[CAtlArray](#catlarray)|建構函式。|
|[~ CAtlArray](#dtor)|解構函式。|
|[複製](#copy)|呼叫這個方法，將某個陣列的元素複製到另一個陣列。|
|[FreeExtra](#freeextra)|呼叫這個方法，從陣列中移除任何空白元素。|
|[GetAt](#getat)|呼叫這個方法，以從陣列物件中取出單一元素。|
|[GetCount](#getcount)|呼叫這個方法，以傳回儲存在陣列中的元素數目。|
|[GetData](#getdata)|呼叫這個方法，以傳回陣列中第一個元素的指標。|
|[InsertArrayAt](#insertarrayat)|呼叫這個方法，將一個陣列插入另一個陣列。|
|[InsertAt](#insertat)|呼叫這個方法，以將新的專案插入 (或元素的多個複本) 至陣列物件。|
|[IsEmpty](#isempty)|呼叫這個方法以測試陣列是否為空的。|
|[RemoveAll](#removeall)|呼叫這個方法，以移除陣列物件中的所有元素。|
|[RemoveAt](#removeat)|呼叫這個方法，從陣列中移除一個或多個元素。|
|[SetAt](#setat)|呼叫這個方法來設定陣列物件中的元素值。|
|[SetAtGrow](#setatgrow)|呼叫這個方法來設定陣列物件中的元素值，並視需要展開陣列。|
|[SetCount](#setcount)|呼叫這個方法來設定陣列物件的大小。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[運算子 &#91;&#93;](#operator_at)|呼叫這個運算子，以傳回陣列中元素的參考。|

### <a name="typedefs"></a>Typedefs

|Typedef|描述|
|-|-|
|[INARGTYPE](#inargtype)|要用於將專案加入至陣列的資料類型。|
|[OUTARGTYPE](#outargtype)|用來從陣列中取得元素的資料類型。|

## <a name="remarks"></a>備註

`CAtlArray` 提供建立和管理使用者定義型別之元素陣列的方法。 雖然類似于標準 C 陣列， `CAtlArray` 物件也可以視需要動態壓縮和成長。 陣列索引一律會從位置0開始，而上限則可以固定，也可以在加入新元素時進行擴充。

針對具有少量元素的陣列，可以使用 ATL 類別 [CSimpleArray](../../atl/reference/csimplearray-class.md) 。

`CAtlArray` 與 MFC 的類別密切相關， `CArray` 而且可以在 mfc 專案中運作，雖然沒有序列化支援。

如需詳細資訊，請參閱 [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>規格需求

**標頭：** atlcoll。h

## <a name="catlarrayadd"></a><a name="add"></a> CAtlArray：： Add

呼叫這個方法，將專案加入至陣列物件。

```cpp
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>參數

*元素*<br/>
要加入至陣列的元素。

### <a name="return-value"></a>傳回值

傳回已加入之元素的索引。

### <a name="remarks"></a>備註

新的元素會加入至陣列的結尾。 如果未提供任何元素，則會加入空的元素;亦即，陣列的大小會隨著實際的元素加入而增加。 如果作業失敗，則會使用引數 E_OUTOFMEMORY 來呼叫 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a> CAtlArray：： Append

呼叫這個方法，將某個陣列的內容加入至另一個陣列的結尾。

```cpp
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>參數

*aSrc*<br/>
要附加的陣列。

### <a name="return-value"></a>傳回值

傳回第一個附加元素的索引。

### <a name="remarks"></a>備註

提供的陣列中的元素會加入至現有陣列的結尾。 必要時，會配置記憶體以容納新的元素。

陣列必須是相同的類型，而且不能將陣列附加至本身。

在 debug 組建中，如果 `CAtlArray` 引數不是有效的陣列，或 *aSrc* 參考相同的物件，就會引發 ATLASSERT。 在發行組建中，不正確引數可能會導致無法預期的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a> CAtlArray：： AssertValid

呼叫這個方法來確認陣列物件是否有效。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>備註

如果陣列物件無效，ATLASSERT 就會擲回判斷提示。 只有在定義 _DEBUG 時，才能使用這個方法。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a> CAtlArray：： CAtlArray

建構函式。

```cpp
CAtlArray() throw();
```

### <a name="remarks"></a>備註

初始化陣列物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a> CAtlArray：： ~ CAtlArray

解構函式。

```cpp
~CAtlArray() throw();
```

### <a name="remarks"></a>備註

釋出陣列物件所使用的任何資源。

## <a name="catlarraycopy"></a><a name="copy"></a> CAtlArray：： Copy

呼叫這個方法，將某個陣列的元素複製到另一個陣列。

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>參數

*aSrc*<br/>
要複製到陣列的元素來源。

### <a name="remarks"></a>備註

呼叫這個方法，以另一個陣列的元素覆寫一個陣列的元素。 必要時，會配置記憶體以容納新的元素。 不可能將陣列的元素複製到本身。

如果要保留陣列的現有內容，請改用 [CAtlArray：： Append](#append) 。

在 debug 組建中，如果現有的 `CAtlArray` 物件無效，或 *aSrc* 參考相同的物件，就會引發 ATLASSERT。 在發行組建中，不正確引數可能會導致無法預期的行為。

> [!NOTE]
> `CAtlArray::Copy` 不支援由以 [CAutoPtr](../../atl/reference/cautoptr-class.md) 類別建立的元素組成的陣列。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a> CAtlArray：： FreeExtra

呼叫這個方法，從陣列中移除任何空白元素。

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>備註

移除任何空白元素，但陣列的大小和上限保持不變。

在偵錯工具組建中，如果 CAtlArray 物件無效，或是陣列會超過其大小上限時，就會引發 ATLASSERT。

## <a name="catlarraygetat"></a><a name="getat"></a> CAtlArray：： GetAt

呼叫這個方法，以從陣列物件中抓取單一元素。

```cpp
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>參數

*iElement*<br/>
要傳回的陣列元素的索引值。

### <a name="return-value"></a>傳回值

傳回所需陣列元素的參考。

### <a name="remarks"></a>備註

在 debug 組建中，如果 *iElement* 超過陣列中的元素數目，就會引發 ATLASSERT。 在發行組建中，不正確引數可能會導致無法預期的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a> CAtlArray：： GetCount

呼叫這個方法，以傳回儲存在陣列中的元素數目。

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回儲存在陣列中的元素數目。

### <a name="remarks"></a>備註

因為陣列中的第一個元素位於位置0，所以傳回的值 `GetCount` 一律為1大於最大的索引。

### <a name="example"></a>範例

請參閱 [CAtlArray：： GetAt](#getat)的範例。

## <a name="catlarraygetdata"></a><a name="getdata"></a> CAtlArray：：：：的

呼叫這個方法，以傳回陣列中第一個元素的指標。

```cpp
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>傳回值

傳回儲存陣列中第一個元素之記憶體位置的指標。 如果沒有可用的元素，則會傳回 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a> CAtlArray：： INARGTYPE

要用於將專案加入至陣列的資料類型。

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a> CAtlArray：： InsertArrayAt

呼叫這個方法，將一個陣列插入另一個陣列。

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>參數

*iStart*<br/>
要插入陣列的索引。

*paNew*<br/>
要插入的陣列。

### <a name="remarks"></a>備註

陣列 *paNew* 中的專案會複製到陣列物件，從元素 *iStart*開始。 將會移動現有的陣列元素，以避免遭到覆寫。

在 debug 組建中，如果 `CAtlArray` 物件無效，或 *paNew* 指標為 Null 或無效，就會引發 ATLASSERT。

> [!NOTE]
> `CAtlArray::InsertArrayAt` 不支援由以 [CAutoPtr](../../atl/reference/cautoptr-class.md) 類別建立的元素組成的陣列。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a> CAtlArray：： InsertAt

呼叫這個方法，以將新的專案插入 (或元素的多個複本) 至陣列物件。

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>參數

*iElement*<br/>
要插入元素或元素的索引。

*元素*<br/>
要插入的元素或元素的值。

*nCount*<br/>
要加入的元素數目。

### <a name="remarks"></a>備註

從索引 *iElement*開始，將一個或多個元素插入陣列中。 將會移動現有的專案，以避免遭到覆寫。

在偵錯工具組建中，如果 `CAtlArray` 物件無效、要加入的元素數目為零，或元素的組合數目太大而無法包含的陣列，將會引發 ATLASSERT。 在零售組建中，傳遞不正確參數可能會導致無法預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a> CAtlArray：： IsEmpty

呼叫這個方法以測試陣列是否為空的。

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果陣列是空的，則傳回 true，否則傳回 false。

### <a name="remarks"></a>備註

如果陣列不包含任何元素，則會被視為空白。 因此，即使陣列包含空的元素，也不會是空的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a> CAtlArray：： operator []

呼叫這個運算子，以傳回陣列中元素的參考。

```cpp
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>參數

*iElement*<br/>
要傳回的陣列元素的索引值。

### <a name="return-value"></a>傳回值

傳回所需陣列元素的參考。

### <a name="remarks"></a>備註

對 [CAtlArray：： GetAt](#getat)執行類似的函數。 不同于 MFC 類別 [CArray](../../mfc/reference/carray-class.md)，這個運算子不能用來取代 [CAtlArray：： SetAt](#setat)。

在 debug 組建中，如果 *iElement* 超過陣列中的專案總數，就會引發 ATLASSERT。 在零售組建中，不正確參數可能會導致無法預期的結果。

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a> CAtlArray：： OUTARGTYPE

用來從陣列中取得元素的資料類型。

```cpp
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a> CAtlArray：： RemoveAll

呼叫這個方法，以移除陣列物件中的所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

從陣列物件移除所有元素。

這個方法會呼叫 [CAtlArray：： SetCount](#setcount) 來調整陣列的大小，然後再釋放任何配置的記憶體。

### <a name="example"></a>範例

請參閱 [CAtlArray：： IsEmpty](#isempty)的範例。

## <a name="catlarrayremoveat"></a><a name="removeat"></a> CAtlArray：： RemoveAt

呼叫這個方法，從陣列中移除一個或多個元素。

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>參數

*iElement*<br/>
要移除之第一個元素的索引。

*nCount*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

從陣列中移除一個或多個元素。 任何剩餘的元素都會向下移動。 上限是遞減的，但在呼叫 [CAtlArray：： FreeExtra](#freeextra) 之前，不會釋放記憶體。

在偵錯工具組建中，如果 `CAtlArray` 物件無效，或 *IElement* 和 *nCount* 的組合總計超過陣列中的元素總數時，就會引發 ATLASSERT。 在零售組建中，不正確參數可能會導致無法預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a> CAtlArray：： SetAt

呼叫這個方法來設定陣列物件中的元素值。

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>參數

*iElement*<br/>
指向要設定之陣列元素的索引。

*元素*<br/>
指定之項目的新值。

### <a name="remarks"></a>備註

在 debug 組建中，如果 *iElement* 超過陣列中的元素數目，就會引發 ATLASSERT。 在零售組建中，不正確參數可能會導致無法預期的結果。

### <a name="example"></a>範例

請參閱 [CAtlArray：： GetAt](#getat)的範例。

## <a name="catlarraysetcount"></a><a name="setcount"></a> CAtlArray：： SetCount

呼叫這個方法來設定陣列物件的大小。

```cpp
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>參數

*nNewSize*<br/>
陣列的必要大小。

*nGrowBy*<br/>
用來決定緩衝區大小的值。 值-1 會導致使用內部計算的值。

### <a name="return-value"></a>傳回值

如果成功調整陣列的大小，則傳回 true，否則傳回 false。

### <a name="remarks"></a>備註

可以增加或減少陣列的大小。 如果增加，則會將額外的空白元素新增至陣列。 如果減少，則會刪除具有最大索引的元素，並釋放記憶體。

使用這個方法來設定陣列的大小，然後再使用它。 如果 `SetCount` 未使用，則加入專案的程式（以及後續執行的記憶體配置）將會降低效能和片段記憶體。

### <a name="example"></a>範例

請參閱 [CAtlArray：：](#getdata)的範例。

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a> CAtlArray：： SetAtGrow

呼叫這個方法來設定陣列物件中的元素值，並視需要展開陣列。

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>參數

*iElement*<br/>
指向要設定之陣列元素的索引。

*元素*<br/>
指定之項目的新值。

### <a name="remarks"></a>備註

取代索引所指向之元素的值。 如果 *iElement* 大於陣列目前的大小，則會使用 [CAtlArray：： SetCount](#setcount)的呼叫來自動增加陣列。 在 debug 組建中，如果物件無效，則會引發 ATLASSERT `CAtlArray` 。 在零售組建中，不正確參數可能會導致無法預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>另請參閱

[MMXSwarm 範例](../../overview/visual-cpp-samples.md)<br/>
[DynamicConsumer 範例](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 範例](../../overview/visual-cpp-samples.md)<br/>
[天棚範例](../../overview/visual-cpp-samples.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
