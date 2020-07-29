---
title: CList 類別
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 7ba85445e3aba1df853d7d3666c92fdabdfa3970
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182872"
---
# <a name="clist-class"></a>CList 類別

支援可循序或依值存取之非唯一物件的排序清單。

## <a name="syntax"></a>語法

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CList：： CList](#clist)|建立空的已排序清單。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CList：： AddHead](#addhead)|將專案（或另一個清單中的所有元素）新增至清單的開頭（建立新的標頭）。|
|[CList：： AddTail](#addtail)|將專案（或另一個清單中的所有專案）新增至清單的結尾（建立新的結尾）。|
|[CList：： Find](#find)|取得指標值所指定之元素的位置。|
|[CList：： FindIndex](#findindex)|取得以零為基底的索引所指定之元素的位置。|
|[CList：： GetAt](#getat)|取得指定位置的元素。|
|[CList：： GetCount](#getcount)|傳回此清單中的元素數目。|
|[CList：： GetHead](#gethead)|傳回清單的標頭元素（不可以是空的）。|
|[CList：： GetHeadPosition](#getheadposition)|傳回清單 head 元素的位置。|
|[CList：： GetNext](#getnext)|取得用於反覆運算的下一個專案。|
|[CList：： GetPrev](#getprev)|取得上一個反覆運算的元素。|
|[CList：： GetSize](#getsize)|傳回此清單中的元素數目。|
|[CList：： GetTail](#gettail)|傳回清單的尾元素（不可以是空的）。|
|[CList：： GetTailPosition](#gettailposition)|傳回清單結尾元素的位置。|
|[CList：： InsertAfter](#insertafter)|在指定的位置之後插入新的元素。|
|[CList::InsertBefore](#insertbefore)|在指定的位置之前插入新的元素。|
|[CList：： IsEmpty](#isempty)|測試空白清單條件（沒有元素）。|
|[CList：： RemoveAll](#removeall)|移除此清單中的所有元素。|
|[CList：： RemoveAt](#removeat)|從此清單中移除專案（依位置指定）。|
|[CList：： RemoveHead](#removehead)|將專案從清單的開頭移除。|
|[CList：： RemoveTail](#removetail)|從清單的結尾移除元素。|
|[CList：： SetAt](#setat)|設定指定位置的元素。|

#### <a name="parameters"></a>參數

*TYPE*<br/>
儲存在清單中的物件類型。

*ARG_TYPE*<br/>
用來參考儲存在清單中之物件的類型。 可以是參考。

## <a name="remarks"></a>備註

`CList`清單的行為就像雙向連結清單一樣。

「位置」類型的變數是清單的索引鍵。 您可以使用位置變數做為反覆運算器，依序和以書簽的形式來瀏覽清單。 不過，位置與索引並不相同。

在清單標頭、結尾和已知的位置，插入元素非常快速。 依照值或索引來查詢元素時，必須進行順序搜尋。 如果清單很長，則此搜尋可能會變慢。

如果您需要清單中個別元素的傾印，您必須將傾印內容的深度設定為1或更大。

這個類別的某些成員函式會呼叫全域 helper 函式，而這些函式必須針對類別的大部分使用進行自訂 `CList` 。 請參閱「宏和 Globals」一節中的[集合類別](../../mfc/reference/collection-class-helpers.md)協助程式。

如需有關使用的詳細資訊 `CList` ，請參閱文章[集合](../../mfc/collections.md)。

## <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList：： AddHead

將新的專案或專案清單加入至此清單的開頭。

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*newElement*<br/>
新的元素。

*pNewList*<br/>
另一個清單的指標 `CList` 。 *PNewList*中的專案將會新增至此清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

此清單在作業之前可以是空的。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList：： AddTail

將新的專案或專案清單加入至這個清單的結尾。

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*newElement*<br/>
要加入這份清單中的項目。

*pNewList*<br/>
另一個清單的指標 `CList` 。 *PNewList*中的專案將會新增至此清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

此清單在作業之前可以是空的。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList：： CList

建立空的已排序清單。

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
擴充清單的記憶體配置資料細微性。

### <a name="remarks"></a>備註

隨著清單成長，記憶體會以*nBlockSize*專案的單位來配置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CList：： Find

依序搜尋清單，尋找符合指定*searchValue*的第一個元素。

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*searchValue*<br/>
要在清單中尋找的值。

*startAfter*<br/>
搜尋的開始位置。 如果未指定任何值，則會以 head 元素開頭進行搜尋。

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果找不到物件，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CList：： FindIndex

會使用*nIndex*的值當做清單中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要尋找之清單元素的以零為起始的索引。

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果*nIndex*為負數或太大，則為 Null。

### <a name="remarks"></a>備註

它會從清單的開頭開始進行順序掃描，而在第*n*個元素上停止。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList：： GetAt

取得指定位置的清單元素。

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定清單中的物件類型。

*移動*<br/>
要取得的元素清單中的位置。

### <a name="return-value"></a>傳回值

請參閱的傳回值描述 `GetHead` 。

### <a name="remarks"></a>備註

`GetAt`傳回與指定位置相關聯的元素（或專案的參考）。 它與索引並不相同，而且您無法自行操作位置值。 「位置」類型的變數是清單的索引鍵。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

### <a name="example"></a>範例

  請參閱[CList：： GetHeadPosition](#getheadposition)的範例。

## <a name="clistgetcount"></a><a name="getcount"></a>CList：： GetCount

取得此清單中的元素數目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

包含元素計數的整數值。

### <a name="remarks"></a>備註

呼叫這個方法將會產生與[CList：： GetSize](#getsize)方法相同的結果。

### <a name="example"></a>範例

  請參閱[CList：： RemoveHead](#removehead)的範例。

## <a name="clistgethead"></a><a name="gethead"></a>CList：： GetHead

取得此清單的標頭專案（或 head 元素的參考）。

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定清單中的物件類型。

### <a name="return-value"></a>傳回值

如果清單為 **`const`** ，會 `GetHead` 在清單的開頭傳回元素的複本。 這可讓函式僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetHead` 位於清單開頭之元素的參考。 這可讓函式在指派語句的任一端使用，因此可修改清單專案。

### <a name="remarks"></a>備註

在呼叫之前，您必須先確定清單不是空的 `GetHead` 。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](#isempty)來驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList：： GetHeadPosition

取得此清單之 head 元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果清單是空的，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList：： GetNext

取得*rPosition*所識別的清單元素，然後將*rPosition*設定為清單中下一個專案的位置值。

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定清單中元素的類型。

*rPosition*<br/>
先前 `GetNext` 、 [GetHeadPosition](#getheadposition)或其他成員函式呼叫所傳回之位置值的參考。

### <a name="return-value"></a>傳回值

如果清單為，會傳回 **`const`** `GetNext` 清單元素的複本。 這可讓函式僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetNext` 清單元素的參考。 這可讓函式在指派語句的任一端使用，因此可修改清單專案。

### <a name="remarks"></a>備註

`GetNext`如果您透過呼叫或來建立初始位置，則可以在正向反復專案迴圈中使用 `GetHeadPosition` `Find` 。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

如果所抓取的專案是清單中的最後一個，則的新值 `rPosition` 會設為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList：： GetPrev

取得所識別的清單元素 `rPosition` ，然後將設定 `rPosition` 為清單中上一個專案的位置值。

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定清單中元素的類型。

*rPosition*<br/>
先前 `GetPrev` 或其他成員函式呼叫所傳回之位置值的參考。

### <a name="return-value"></a>傳回值

如果清單為 **`const`** ，會 `GetPrev` 在清單的開頭傳回元素的複本。 這可讓函式僅用於指派語句的右邊，並防止修改清單。

如果清單不是，則會傳回 **`const`** `GetPrev` 清單元素的參考。 這可讓函式在指派語句的任一端使用，因此可修改清單專案。

### <a name="remarks"></a>備註

`GetPrev`如果您透過呼叫或來建立初始位置，可以在反向反復專案迴圈中使用 `GetTailPosition` `Find` 。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

如果抓取的專案是清單中的第一個元素，則*rPosition*的新值會設定為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CList：： GetSize

傳回清單元素的數目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

清單中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法，以取出清單中的專案數。  呼叫這個方法將會產生與[CList：： GetCount](#getcount)方法相同的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CList：： GetTail

取得 `CObject` 表示此清單之尾元素的指標。

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定清單中元素的類型。

### <a name="return-value"></a>傳回值

請參閱[GetHead](../../mfc/reference/coblist-class.md#gethead)的傳回值描述。

### <a name="remarks"></a>備註

在呼叫之前，您必須先確定清單不是空的 `GetTail` 。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)來驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CList：： GetTailPosition

取得此清單結尾元素的位置;如果清單是空的，則為 Null。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果清單是空的，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList：： InsertAfter

在指定位置的專案之後，將元素加入此清單。

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*移動*<br/>
先前的 `GetNext` 、 `GetPrev` 或 `Find` 成員函式呼叫所傳回的位置值。

*ARG_TYPE*<br/>
範本參數，指定清單元素的類型。

*newElement*<br/>
要加入這份清單中的項目。

### <a name="return-value"></a>傳回值

可用於反覆項目或清單項目擷取的 POSITION 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList：： InsertBefore

將項目加入這份清單中相同項目之前的指定位置。

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*移動*<br/>
先前的 `GetNext` 、 `GetPrev` 或 `Find` 成員函式呼叫所傳回的位置值。

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*newElement*<br/>
要加入這份清單中的項目。

### <a name="return-value"></a>傳回值

可用於反覆項目或清單項目擷取的 POSITION 值。

### <a name="remarks"></a>備註

如果*position*為 Null，則會將元素插入清單的開頭。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList：： IsEmpty

指出此清單是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果此清單是空的，則為非零;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList：： RemoveAll

移除此清單中的所有元素，並釋出相關聯的記憶體。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

如果清單已經是空的，就不會產生任何錯誤。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList：： RemoveAt

從這個清單中移除指定的專案。

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>參數

*移動*<br/>
要從清單中移除之元素的位置。

### <a name="remarks"></a>備註

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CList：： RemoveHead

將專案從清單的開頭移除，並傳回其指標。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定清單中元素的類型。

### <a name="return-value"></a>傳回值

先前位於清單開頭的專案。

### <a name="remarks"></a>備註

在呼叫之前，您必須先確定清單不是空的 `RemoveHead` 。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](#isempty)來驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CList：： RemoveTail

從清單的結尾移除元素，並傳回其指標。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定清單中元素的類型。

### <a name="return-value"></a>傳回值

位於清單結尾的元素。

### <a name="remarks"></a>備註

在呼叫之前，您必須先確定清單不是空的 `RemoveTail` 。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](#isempty)來驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList：： SetAt

「位置」類型的變數是清單的索引鍵。

```cpp
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*採購*<br/>
要設定之元素的位置。

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*newElement*<br/>
要加入至清單的元素。

### <a name="remarks"></a>備註

它與索引並不相同，而且您無法自行操作位置值。 `SetAt`將元素寫入清單中的指定位置。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMap 類別](../../mfc/reference/cmap-class.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)
