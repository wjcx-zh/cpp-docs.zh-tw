---
title: CAtlarray 類別
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
ms.openlocfilehash: 607af2adaa3ef28a768812f3c811eb2ed3169ad9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748787"
---
# <a name="catlarray-class"></a>CAtlarray 類別

此類實現陣列物件。

## <a name="syntax"></a>語法

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>參數

*E*<br/>
陣列中儲存之資料的類型。

*埃特格*<br/>
複製或移動元素的代碼。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[加入](#add)|呼叫此方法以向陣列物件添加元素。|
|[附加](#append)|呼叫此方法將一個陣列的內容添加到另一個陣列的末尾。|
|[斷言有效](#assertvalid)|調用此方法以確認陣列物件是否有效。|
|[克拉拉](#catlarray)|建構函式。|
|[*CAtlarray](#dtor)|解構函式。|
|[複製](#copy)|呼叫此方法將一個陣列的元素複製到另一個陣列。|
|[免費額外](#freeextra)|呼叫此方法從陣列中刪除任何空元素。|
|[GetAt](#getat)|調用此方法從陣列對數組物件檢索單個元素。|
|[GetCount](#getcount)|調用此方法以返回存儲在陣列中的元素數。|
|[GetData](#getdata)|調用此方法以返回指向陣列中第一個元素的指標。|
|[插入Arrayat](#insertarrayat)|呼叫此方法將一個陣列插入到另一個陣列中。|
|[插入At](#insertat)|調用此方法以將新元素(或元素的多個副本)插入陣列物件。|
|[是空的](#isempty)|調用此方法以測試陣列是否為空。|
|[全部刪除](#removeall)|呼叫此方法從陣列物件中刪除所有元素。|
|[RemoveAt](#removeat)|呼叫此方法從陣列中刪除一個或多個元素。|
|[Setat](#setat)|呼叫此方法以設定陣列中元素的值。|
|[SetAt增長](#setatgrow)|調用此方法以設置陣列中元素的值,根據需要展開陣列。|
|[設定計數](#setcount)|呼叫此方法以設定陣列物件的大小。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算子 &#91;&#93;](#operator_at)|呼叫此運算符以返回對陣列中元素的引用。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARG型](#inargtype)|用於向陣列添加元素的資料類型。|
|[出型](#outargtype)|用於從陣列檢索元素的數據類型。|

## <a name="remarks"></a>備註

`CAtlArray`提供了創建和管理使用者定義類型元素陣列的方法。 儘管與標準 C 陣列`CAtlArray`類似, 但物件可以根據需要動態收縮和成長。 陣列索引始終從位置 0 開始,並且上邊界可以固定,或者允許在添加新元素時展開。

對於具有少量元素的陣列,可以使用 ATL 類[CSimplearray。](../../atl/reference/csimplearray-class.md)

`CAtlArray`與 MFC`CArray`的類別密切相關,將在 MFC 專案中工作,儘管沒有序列化支援。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="catlarrayadd"></a><a name="add"></a>克拉拉:添加

呼叫此方法以向陣列物件添加元素。

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>參數

*元素*<br/>
要添加到陣列的元素。

### <a name="return-value"></a>傳回值

返回添加元素的索引。

### <a name="remarks"></a>備註

新元素將添加到陣列的末尾。 如果未提供任何元素,則添加空元素;如果未提供任何元素,則添加空元素。也就是說,陣列的大小增加,就像添加了實際元素一樣。 如果操作失敗,則使用參數E_OUTOFMEMORY調用[AtlThrow。](debugging-and-error-reporting-global-functions.md#atlthrow)

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray::附加

呼叫此方法將一個陣列的內容添加到另一個陣列的末尾。

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>參數

*阿斯爾克*<br/>
要追加的陣列。

### <a name="return-value"></a>傳回值

返回第一個附加元素的索引。

### <a name="remarks"></a>備註

提供陣列中的元素將添加到現有陣列的末尾。 如有必要,將分配記憶體以適應新元素。

陣列必須具有相同的類型,並且無法將陣列追加到自身。

在除錯產生中,如果參數不是有效的陣列或`CAtlArray`*aSrc*引用同一物件,則將引發 ATLASSERT。 在發佈版本中,無效參數可能導致不可預知的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlarray::斷言有效

調用此方法以確認陣列物件是否有效。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>備註

如果陣列對象無效,ATLASSERT 將引發斷言。 僅當定義了_DEBUG時,此方法才可用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>克拉拉:克拉拉

建構函式。

```
CAtlArray() throw();
```

### <a name="remarks"></a>備註

初始化陣列物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlarray:_CAtlarray

解構函式。

```
~CAtlArray() throw();
```

### <a name="remarks"></a>備註

釋放陣列對象使用的任何資源。

## <a name="catlarraycopy"></a><a name="copy"></a>卡拉拉:複製

呼叫此方法將一個陣列的元素複製到另一個陣列。

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>參數

*阿斯爾克*<br/>
要複製到陣列的元素的源。

### <a name="remarks"></a>備註

呼叫此方法用另一個陣列的元素覆蓋一個陣列的元素。 如有必要,將分配記憶體以適應新元素。 無法將陣列的元素複製到自身。

如果要保留陣列的現有內容,請使用[CAtlArray:::附加](#append)。

在調試生成中,如果現有`CAtlArray`物件無效,或者*aSrc*引用同一物件,則將引發 ATLASSERT。 在發佈版本中,無效參數可能導致不可預知的行為。

> [!NOTE]
> `CAtlArray::Copy`不支援由[CAutoPtr](../../atl/reference/cautoptr-class.md)類創建的元素組成的陣列。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlarray:免費額外

呼叫此方法從陣列中刪除任何空元素。

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>備註

刪除任何空元素,但陣列的大小和上限保持不變。

在調試生成中,如果 CAtlArray 物件無效,或者陣列將超過其最大大小,將引發 ATLASSERT。

## <a name="catlarraygetat"></a><a name="getat"></a>克拉拉::獲取At

調用此方法從陣列對數組物件檢索單個元素。

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>參數

*i 元素*<br/>
要返回的陣列元素的索引值。

### <a name="return-value"></a>傳回值

返回對所需陣列元素的引用。

### <a name="remarks"></a>備註

在調試生成中,如果*iElement*超過陣列中的元素數,將引發 ATLASSERT。 在發佈版本中,無效的參數可能會導致不可預知的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlarray:取得計數

調用此方法以返回存儲在陣列中的元素數。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

返回存儲在陣列中的元素數。

### <a name="remarks"></a>備註

由於陣列中的第一個元素位於位置 0,因此`GetCount`返回的值始終大於最大索引 1。

### <a name="example"></a>範例

請參閱[CAtlArray 的範例::GetAt](#getat)。

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlarray:抓取資料

調用此方法以返回指向陣列中第一個元素的指標。

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>傳回值

返回指向存儲陣列中第一個元素的記憶體位置的指標。 如果沒有可用的元素,則傳回 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>克拉拉::INARGTYPE

用於向陣列添加元素的資料類型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>克拉拉::插入Arrayat

呼叫此方法將一個陣列插入到另一個陣列中。

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>參數

*i 開始*<br/>
要插入陣列的索引。

*paNew*<br/>
要插入的陣列。

### <a name="remarks"></a>備註

陣列*paNew*中的元素從元素*iStart*開始複製到陣列物件中。 移動現有陣列元素以避免被覆蓋。

在除錯產生中,如果`CAtlArray`物件無效,或者如果*paNew*指標為 NULL 或無效,將引發 ATLASSERT。

> [!NOTE]
> `CAtlArray::InsertArrayAt`不支援由[CAutoPtr](../../atl/reference/cautoptr-class.md)類創建的元素組成的陣列。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>克拉拉::插入At

調用此方法以將新元素(或元素的多個副本)插入陣列物件。

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>參數

*i 元素*<br/>
要插入元素或元素的索引。

*元素*<br/>
要插入的元素或元素的值。

*n( N) Count*<br/>
要添加的元素數。

### <a name="remarks"></a>備註

從索引*iElement*開始,將一個或多個元素插入陣列。 移動現有元素以避免被覆蓋。

在除錯產生中,如果`CAtlArray`物件無效、要添加的元素數為零或組合的元素數太大,陣列無法包含,則將引發 ATLASSERT。 在零售版本中,傳遞無效參數可能會導致不可預知的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>克拉拉::空

調用此方法以測試陣列是否為空。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果陣列為空,則返回true,否則為 false。

### <a name="remarks"></a>備註

如果陣列不包含任何元素,則該陣列表示為空。 因此,即使數組包含空元素,它也不為空。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray::運算符 |

呼叫此運算符以返回對陣列中元素的引用。

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>參數

*i 元素*<br/>
要返回的陣列元素的索引值。

### <a name="return-value"></a>傳回值

返回對所需陣列元素的引用。

### <a name="remarks"></a>備註

執行與[CAtlArray 類似的功能::getAt](#getat)。 與 MFC 類[CArray](../../mfc/reference/carray-class.md)不同,此運算符不能用作[CAtlArray:setAt](#setat)的替代品。

在調試生成中,如果*iElement*超過陣列中的元素總數,將引發 ATLASSERT。 在零售生成中,無效參數可能會導致不可預知的結果。

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>克拉拉::OUTARGTYPE

用於從陣列檢索元素的數據類型。

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlarray:刪除所有

呼叫此方法從陣列物件中刪除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

從陣列物件中移除所有元素。

此方法調用[CAtlArray::SetCount](#setcount)以調整陣列的大小,然後釋放任何分配的記憶體。

### <a name="example"></a>範例

請參考[CAtlArray 的範例::是空的](#isempty)。

## <a name="catlarrayremoveat"></a><a name="removeat"></a>克拉拉::刪除At

呼叫此方法從陣列中刪除一個或多個元素。

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>參數

*i 元素*<br/>
要刪除的第一個元素的索引。

*n( N) Count*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

從陣列中移除一個或多個元素。 任何剩餘元素都向下移動。 上限將遞減,但在調用[CAtlArray:::FreeExtra](#freeextra)之前不會釋放記憶體。

在除錯產生中,如果`CAtlArray`物件無效,或者如果*iElement*和*nCount*的總和超過陣列中的元素總數,則將引發 ATLASSERT。 在零售版本中,無效參數可能會導致不可預知的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>克拉拉::Setat

呼叫此方法以設定陣列中元素的值。

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>參數

*i 元素*<br/>
指向要設置的陣組元素的索引。

*元素*<br/>
指定之項目的新值。

### <a name="remarks"></a>備註

在調試生成中,如果*iElement*超過陣列中的元素數,將引發 ATLASSERT。 在零售生成中,無效參數可能會導致不可預知的結果。

### <a name="example"></a>範例

請參閱[CAtlArray 的範例::GetAt](#getat)。

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlarray::設定計數

呼叫此方法以設定陣列物件的大小。

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>參數

*n 新尺寸*<br/>
陣列所需的大小。

*nGrowBy*<br/>
用於確定使緩衝區有多大的值。 值 -1 會導致使用內部計算的值。

### <a name="return-value"></a>傳回值

如果陣列成功調整大小,則返回 true,否則為 false。

### <a name="remarks"></a>備註

陣列的大小可以增加或減小。 如果增加,則向陣列中添加額外的空元素。 如果減少,將刪除索引最大的元素並釋放記憶體。

使用此方法在使用陣列之前設置陣列的大小。 如果不`SetCount`使用,添加元素的過程(以及執行的後續記憶體分配)將降低性能和片段記憶體。

### <a name="example"></a>範例

請參考[CAtlArray 的範例::抓取資料](#getdata)。

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlarray:setat增長

調用此方法以設置陣列中元素的值,根據需要展開陣列。

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>參數

*i 元素*<br/>
指向要設置的陣組元素的索引。

*元素*<br/>
指定之項目的新值。

### <a name="remarks"></a>備註

替換索引指向的元素的值。 如果*iElement*大於陣列的當前大小,則使用對[CAtlArray::setCount](#setcount)的調用會自動增加陣列。 在除錯產生中,如果物件無效,`CAtlArray`將引發 ATLASSERT。 在零售版本中,無效參數可能會導致不可預知的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>另請參閱

[MMXSwarm 樣品](../../overview/visual-cpp-samples.md)<br/>
[動態消費者範例](../../overview/visual-cpp-samples.md)<br/>
[更新PV範例](../../overview/visual-cpp-samples.md)<br/>
[選取方塊範例](../../overview/visual-cpp-samples.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
