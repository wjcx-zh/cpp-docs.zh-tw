---
title: CAtlList 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 15830a30e8236a13f3911d1b84d3727d3246fc0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226668"
---
# <a name="catllist-class"></a>CAtlList 類別

這個類別會提供建立和管理清單物件的方法。

## <a name="syntax"></a>語法

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>參數

*版*<br/>
元素類型。

*ETraits*<br/>
用來複製或移動元素的程式碼。 如需詳細資訊，請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|建構函式。|
|[CAtlList：： ~ CAtlList](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|呼叫這個方法，將元素加入至清單的開頭。|
|[CAtlList::AddHeadList](#addheadlist)|呼叫這個方法，將現有的清單新增至清單的開頭。|
|[CAtlList：： AddTail](#addtail)|呼叫這個方法，將元素新增至此清單的結尾。|
|[CAtlList::AddTailList](#addtaillist)|呼叫這個方法，將現有的清單新增至這個清單的結尾。|
|[CAtlList::AssertValid](#assertvalid)|呼叫這個方法來確認清單是否有效。|
|[CAtlList：： Find](#find)|呼叫這個方法，以在清單中搜尋指定的專案。|
|[CAtlList：： FindIndex](#findindex)|呼叫這個方法，以取得指定索引值的元素位置。|
|[CAtlList：： GetAt](#getat)|呼叫這個方法，以傳回清單中指定位置的元素。|
|[CAtlList：： GetCount](#getcount)|呼叫這個方法，以傳回清單中的物件數目。|
|[CAtlList::GetHead](#gethead)|呼叫這個方法，以傳回位於清單開頭的專案。|
|[CAtlList::GetHeadPosition](#getheadposition)|呼叫這個方法以取得清單標頭的位置。|
|[CAtlList：： GetNext](#getnext)|呼叫這個方法，以傳回清單中的下一個元素。|
|[CAtlList::GetPrev](#getprev)|呼叫這個方法，以傳回清單中的上一個專案。|
|[CAtlList::GetTail](#gettail)|呼叫這個方法，以傳回清單結尾的元素。|
|[CAtlList::GetTailPosition](#gettailposition)|呼叫這個方法，以取得清單結尾的位置。|
|[CAtlList：： InsertAfter](#insertafter)|呼叫這個方法，將新的專案插入清單中指定的位置之後。|
|[CAtlList：： InsertBefore](#insertbefore)|呼叫這個方法，將新的專案插入清單中指定的位置之前。|
|[CAtlList：： IsEmpty](#isempty)|呼叫這個方法，以判斷清單是否為空的。|
|[CAtlList::MoveToHead](#movetohead)|呼叫這個方法，將指定的專案移至清單的開頭。|
|[CAtlList::MoveToTail](#movetotail)|呼叫這個方法，將指定的專案移至清單的結尾。|
|[CAtlList：： RemoveAll](#removeall)|呼叫這個方法，從清單中移除所有元素。|
|[CAtlList：： RemoveAt](#removeat)|呼叫這個方法，從清單中移除單一元素。|
|[CAtlList::RemoveHead](#removehead)|呼叫這個方法，以移除清單開頭的專案。|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|呼叫這個方法，以移除清單開頭的專案，而不傳回值。|
|[CAtlList::RemoveTail](#removetail)|呼叫這個方法，以移除清單結尾的元素。|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|呼叫這個方法，以移除清單結尾的專案，而不傳回值。|
|[CAtlList：： SetAt](#setat)|呼叫這個方法，在清單中的指定位置設定元素的值。|
|[CAtlList::SwapElements](#swapelements)|呼叫這個方法以交換清單中的元素。|

## <a name="remarks"></a>備註

`CAtlList`類別支援順序或依值存取之非唯一物件的排序清單。 `CAtlList`清單的行為與雙向連結清單類似。 每個清單都有一個標頭和結尾，而新的專案（或某些案例中的清單）可以加入至清單的任一端，或在特定專案之前或之後插入。

大部分的 `CAtlList` 方法會利用位置值。 方法會使用這個值來參考儲存元素的實際記憶體位置，而不應該直接計算或預測。 如果需要存取清單中的第*n*個元素，則方法[CAtlList：： FindIndex](#findindex)會傳回給定索引的對應位置值。 [CAtlList：： GetNext](#getnext)和[CAtlList：： GetPrev](#getprev)方法可以用來逐一查看清單中的物件。

如需 ATL 可用之集合類別的詳細資訊，請參閱[Atl 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll。h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

呼叫這個方法，將元素加入至清單的開頭。

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>參數

*元素*<br/>
新的元素。

### <a name="return-value"></a>傳回值

傳回新加入元素的位置。

### <a name="remarks"></a>備註

如果使用第一個版本，則會使用預設的函式（而不是其複製的程式）來建立空的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

呼叫這個方法，將現有的清單新增至清單的開頭。

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>參數

*plNew*<br/>
要加入的清單。

### <a name="remarks"></a>備註

*PlNew*所指向的清單會插入至現有清單的開頭。 在 [偵錯工具] 組建中，如果*plNew*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList：： AddTail

呼叫這個方法，將元素新增至此清單的結尾。

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>參數

*元素*<br/>
要加入的項目。

### <a name="return-value"></a>傳回值

傳回新加入元素的位置。

### <a name="remarks"></a>備註

如果使用第一個版本，則會使用預設的函式（而不是其複製的程式）來建立空的元素。 元素會新增至清單結尾，因此它現在會變成結尾。 這個方法可以與空白清單搭配使用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

呼叫這個方法，將現有的清單新增至這個清單的結尾。

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>參數

*plNew*<br/>
要加入的清單。

### <a name="remarks"></a>備註

*PlNew*所指向的清單會插入清單物件中的最後一個元素（如果有的話）之後。 因此， *plNew*清單中的最後一個元素會變成結尾。 在 [偵錯工具] 組建中，如果*plNew*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

呼叫這個方法來確認清單是否有效。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>備註

在 [偵錯工具] 組建中，如果清單物件無效，就會發生判斷提示失敗。 空白清單必須同時指向 Null，且不是空白的清單必須同時指向有效位址的開頭和結尾，才有效。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

建構函式。

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

物件的構造函式 `CAtlList` 。 區塊大小是在需要新元素時所配置的記憶體數量的量值。 較大的區塊大小會減少對記憶體配置常式的呼叫，但會使用更多資源。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList：： ~ CAtlList

解構函式。

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>備註

釋放所有配置的資源，包括呼叫[CAtlList：： RemoveAll](#removeall) ，以移除清單中的所有元素。

在 [偵錯工具] 組建中，如果清單仍包含呼叫之後的某些元素，就會發生判斷提示失敗 `RemoveAll` 。

## <a name="catllistfind"></a><a name="find"></a>CAtlList：： Find

呼叫這個方法，以在清單中搜尋指定的專案。

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>參數

*元素*<br/>
要在清單中找到的元素。

*posStartAfter*<br/>
搜尋的開始位置。 如果未指定任何值，則會以 head 元素開頭進行搜尋。

### <a name="return-value"></a>傳回值

如果找到，則傳回元素的位置值，否則傳回 Null。

### <a name="remarks"></a>備註

在 [偵錯工具] 組建中，如果清單物件無效，或*posStartAfter*值超出範圍，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList：： FindIndex

呼叫這個方法，以取得指定索引值的元素位置。

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>參數

*iElement*<br/>
必要清單元素的以零為起始的索引。

### <a name="return-value"></a>傳回值

傳回對應的位置值，如果*iElement*超出範圍，則傳回 Null。

### <a name="remarks"></a>備註

這個方法會傳回對應到指定索引值的位置，允許存取清單中的第*n*個元素。

在 [偵錯工具] 組建中，如果清單物件無效，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList：： GetAt

呼叫這個方法，以傳回清單中指定位置的元素。

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
指定特定元素的位置值。

### <a name="return-value"></a>傳回值

元素的參考或複本。

### <a name="remarks"></a>備註

如果清單為，則會傳回 **`const`** `GetAt` 元素的複本。 這可讓方法僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetAt` 元素的參考。 這可讓方法在指派語句的任一端使用，因此可修改清單專案。

在 debug 組建中，如果*pos*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： FindIndex](#findindex)的範例。

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList：： GetCount

呼叫這個方法，以傳回清單中的物件數目。

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回清單中項目的數目。

### <a name="example"></a>範例

請參閱[CAtlList：： Find](#find)的範例。

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

呼叫這個方法，以傳回位於清單開頭的專案。

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>傳回值

傳回位於清單開頭之專案的參考或複本。

### <a name="remarks"></a>備註

如果清單為 **`const`** ，會 `GetHead` 在清單的開頭傳回元素的複本。 這可讓方法僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetHead` 位於清單開頭之元素的參考。 這可讓方法在指派語句的任一端使用，因此可修改清單專案。

在 [偵錯工具] 組建中，如果清單的標頭指向 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： AddHead](#addhead)的範例。

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

呼叫這個方法以取得清單標頭的位置。

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>傳回值

傳回對應于清單開頭之元素的位置值。

### <a name="remarks"></a>備註

如果清單是空的，傳回的值會是 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList：： GetNext

呼叫這個方法，以傳回清單中的下一個元素。

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
先前呼叫 `GetNext` 、 [CAtlList：： GetHeadPosition](#getheadposition)或其他方法所傳回的位置值 `CAtlList` 。

### <a name="return-value"></a>傳回值

如果清單為，則會傳回 **`const`** `GetNext` 清單下一個元素的複本。 這可讓方法僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetNext` 清單下一個元素的參考。 這可讓方法在指派語句的任一端使用，因此可修改清單專案。

### <a name="remarks"></a>備註

位置計數器*pos*會更新以指向清單中的下一個元素，如果沒有其他元素，則為 Null。 在 debug 組建中，如果*pos*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： GetHeadPosition](#getheadposition)的範例。

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

呼叫這個方法，以傳回清單中的上一個專案。

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
先前呼叫 `GetPrev` 、 [CAtlList：： GetTailPosition](#gettailposition)或其他方法所傳回的位置值 `CAtlList` 。

### <a name="return-value"></a>傳回值

如果清單為，會傳回 **`const`** `GetPrev` 清單元素的複本。 這可讓方法僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetPrev` 清單元素的參考。 這可讓方法在指派語句的任一端使用，因此可修改清單專案。

### <a name="remarks"></a>備註

位置計數器*pos*會更新以指向清單中的上一個專案，如果沒有其他元素，則為 Null。 在 debug 組建中，如果*pos*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： GetTailPosition](#gettailposition)的範例。

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

呼叫這個方法，以傳回清單結尾的元素。

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>傳回值

傳回位於清單結尾之元素的參考或複本。

### <a name="remarks"></a>備註

如果清單為 **`const`** ，會 `GetTail` 在清單的開頭傳回元素的複本。 這可讓方法僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetTail` 位於清單開頭之元素的參考。 這可讓方法在指派語句的任一端使用，因此可修改清單專案。

在「偵錯工具組建」中，如果清單的結尾指向 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： AddTail](#addtail)的範例。

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

呼叫這個方法，以取得清單結尾的位置。

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>傳回值

傳回對應于清單結尾之元素的位置值。

### <a name="remarks"></a>備註

如果清單是空的，傳回的值會是 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

當元素做為輸入引數傳遞時，所使用的類型。

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList：： InsertAfter

呼叫這個方法，將新的專案插入清單中指定的位置之後。

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>參數

*採購*<br/>
位置值，在此之後會插入新的元素。

*元素*<br/>
要插入的元素。

### <a name="return-value"></a>傳回值

傳回新元素的位置值。

### <a name="remarks"></a>備註

在 [偵錯工具] 組建中，如果清單無效、插入失敗，或是嘗試在結尾後面插入元素，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList：： InsertBefore

呼叫這個方法，將新的專案插入清單中指定的位置之前。

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>參數

*採購*<br/>
新的元素會插入此位置值之前的清單。

*元素*<br/>
要插入的元素。

### <a name="return-value"></a>傳回值

傳回新元素的位置值。

### <a name="remarks"></a>備註

在 debug build 中，如果清單無效、插入失敗，或是嘗試在標頭之前插入元素，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList：： IsEmpty

呼叫這個方法，以判斷清單是否為空的。

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果清單未包含任何物件，則傳回 true，否則傳回 false。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

呼叫這個方法，將指定的專案移至清單的開頭。

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
要移動之元素的位置值。

### <a name="remarks"></a>備註

指定的元素會從其目前的位置移至清單的開頭。 在 debug 組建中，如果*pos*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

呼叫這個方法，將指定的專案移至清單的結尾。

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
要移動之元素的位置值。

### <a name="remarks"></a>備註

指定的元素會從其目前的位置移至清單的結尾。 在 debug 組建中，如果*pos*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： MoveToHead](#movetohead)的範例。

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList：： RemoveAll

呼叫這個方法，從清單中移除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

這個方法會從清單中移除所有專案，並釋放已配置的記憶體。 在偵錯工具組建中，如果所有專案都不會被刪除，或是清單結構已損毀，就會引發 ATLASSERT。

### <a name="example"></a>範例

請參閱[CAtlList：： IsEmpty](#isempty)的範例。

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList：： RemoveAt

呼叫這個方法，從清單中移除單一元素。

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
要移除之元素的位置值。

### <a name="remarks"></a>備註

已移除*pos*所參考的元素，並釋放記憶體。 您可以使用 `RemoveAt` 移除清單的開頭或結尾。

在 [偵錯工具] 組建中，如果清單無效或移除專案導致清單存取不屬於清單結構的記憶體，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

呼叫這個方法，以移除清單開頭的專案。

```cpp
E RemoveHead();
```

### <a name="return-value"></a>傳回值

傳回位於清單開頭的專案。

### <a name="remarks"></a>備註

標頭專案會從清單中刪除，而且會釋放記憶體。 會傳回元素的複本。 在 [偵錯工具] 組建中，如果清單是空的，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

呼叫這個方法，以移除清單開頭的專案，而不傳回值。

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>備註

標頭專案會從清單中刪除，而且會釋放記憶體。 在 [偵錯工具] 組建中，如果清單是空的，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： IsEmpty](#isempty)的範例。

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

呼叫這個方法，以移除清單結尾的元素。

```cpp
E RemoveTail();
```

### <a name="return-value"></a>傳回值

傳回位於清單結尾的元素。

### <a name="remarks"></a>備註

結尾元素會從清單中刪除，而且會釋放記憶體。 會傳回元素的複本。 在 [偵錯工具] 組建中，如果清單是空的，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

呼叫這個方法，以移除清單結尾的專案，而不傳回值。

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>備註

結尾元素會從清單中刪除，而且會釋放記憶體。 在 [偵錯工具] 組建中，如果清單是空的，就會發生判斷提示失敗。

### <a name="example"></a>範例

請參閱[CAtlList：： IsEmpty](#isempty)的範例。

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList：： SetAt

呼叫這個方法，在清單中的指定位置設定元素的值。

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>參數

*採購*<br/>
對應至要變更之專案的位置值。

*元素*<br/>
新的元素值。

### <a name="remarks"></a>備註

以*元素*取代現有的值。 在 debug 組建中，如果*pos*等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

呼叫這個方法以交換清單中的元素。

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>參數

*pos1*<br/>
第一個位置值。

*pos2*<br/>
第二個位置值。

### <a name="remarks"></a>備註

交換指定之兩個位置的元素。 在 [偵錯工具] 組建中，如果任一位置值等於 Null，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>另請參閱

[CList 類別](../../mfc/reference/clist-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
