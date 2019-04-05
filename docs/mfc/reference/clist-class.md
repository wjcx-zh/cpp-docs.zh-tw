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
ms.openlocfilehash: 383222e4892bccc653f010ce4939bca23f2adc93
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780947"
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

|名稱|描述|
|----------|-----------------|
|[CList::CList](#clist)|建構空的已排序的清單。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CList::AddHead](#addhead)|將 （讓新的標頭） 清單的標頭中的項目 （或另一個清單中的所有項目）。|
|[CList::AddTail](#addtail)|將 （讓新的結尾） 的清單結尾的項目 （或另一個清單中的所有項目）。|
|[CList::Find](#find)|取得指標值所指定項目的位置。|
|[CList::FindIndex](#findindex)|取得項目以零為起始的索引所指定的位置。|
|[CList::GetAt](#getat)|取得的項目中指定的位置。|
|[CList::GetCount](#getcount)|這份清單中傳回的項目數。|
|[CList::GetHead](#gethead)|傳回 （不能是空的） 清單的標頭的項目。|
|[CList::GetHeadPosition](#getheadposition)|傳回清單的標頭項目的位置。|
|[CList::GetNext](#getnext)|取得逐一查看的下一個項目。|
|[CList::GetPrev](#getprev)|取得逐一查看的上一個項目。|
|[CList::GetSize](#getsize)|這份清單中傳回的項目數。|
|[CList::GetTail](#gettail)|傳回 （不能是空的） 清單的結尾項目。|
|[CList::GetTailPosition](#gettailposition)|傳回清單的結尾元素的位置。|
|[CList::InsertAfter](#insertafter)|之後，指定位置插入新項目。|
|[CList::InsertBefore](#insertbefore)|插入新項目指定的位置之前。|
|[CList::IsEmpty](#isempty)|空白清單條件 （沒有項目） 的測試。|
|[CList::RemoveAll](#removeall)|從這個清單中移除所有項目。|
|[CList::RemoveAt](#removeat)|從這個位置所指定的清單中移除項目。|
|[CList::RemoveHead](#removehead)|移除清單的標頭中的項目。|
|[CList::RemoveTail](#removetail)|移除清單結尾的項目。|
|[CList::SetAt](#setat)|設定的項目中指定的位置。|

#### <a name="parameters"></a>參數

*TYPE*<br/>
儲存在清單中的物件型別。

*ARG_TYPE*<br/>
用來參考儲存在清單中的物件類型。 可以是參考。

## <a name="remarks"></a>備註

`CList` 清單的行為類似雙向連結清單。

位置類型的變數是索引鍵的清單。 您可以使用位置的變數為迭代器，來周遊清單，以循序方式，以及書籤，以便保留圖形的位置。 位置不是相同的索引，不過。

插入項目是非常快速，在清單開頭、 結尾，在和的已知位置。 值或索引來查閱元素必須循序搜尋。 此搜尋可能會很慢，如果清單很長的。

如果您需要個別的項目清單中的傾印，您必須設定為 1 或更高的傾印內容的深度。

全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分使用`CList`類別。 請參閱[集合類別 Helper](../../mfc/reference/collection-class-helpers.md) "巨集和全域變數 」 一節。

如需有關使用`CList`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

##  <a name="addhead"></a>  CList::AddHead

將此清單的標頭中的新項目或項目清單。

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*newElement*<br/>
新的項目。

*pNewList*<br/>
另一個指標`CList`清單。 中的項目*pNewList*會新增至清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

清單可以是空的作業之前。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

##  <a name="addtail"></a>  CList::AddTail

這份清單的結尾加入新項目或項目清單。

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
另一個指標`CList`清單。 中的項目*pNewList*會新增至清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

清單可以是空的作業之前。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

##  <a name="clist"></a>  CList::CList

建構空的已排序的清單。

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
用於擴充清單的記憶體配置資料粒度。

### <a name="remarks"></a>備註

隨著清單時，配置記憶體的單位*nBlockSize*項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

##  <a name="find"></a>  CList::Find

搜尋以循序方式來尋找符合指定的第一個元素的清單*searchValue*。

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*searchValue*<br/>
要在清單中找到的值。

*startAfter*<br/>
搜尋開始位置。 如果未不指定任何值，標頭項目將會開始搜尋。

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果找不到物件，則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

##  <a name="findindex"></a>  CList::FindIndex

會使用值*nIndex*為清單中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要找的清單項目以零為起始的索引。

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果*nIndex*為負數或太大。

### <a name="remarks"></a>備註

從清單中，停止上的開頭開始循序掃描*n*個項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

##  <a name="getat"></a>  CList::GetAt

取得清單項目中指定的位置。

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
樣板參數清單中指定的物件類型。

*位置*<br/>
要取得的項目清單中的位置。

### <a name="return-value"></a>傳回值

請參閱的傳回值描述`GetHead`。

### <a name="remarks"></a>備註

`GetAt` 傳回項目 （或參考的項目） 相關聯的指定位置。 它不相同索引中，而且您無法處理您自己的位置值。 位置類型的變數是索引鍵的清單。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

### <a name="example"></a>範例

  範例，請參閱[CList::GetHeadPosition](#getheadposition)。

##  <a name="getcount"></a>  CList::GetCount

這份清單中取得的項目數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

整數值，其中包含項目計數。

### <a name="remarks"></a>備註

呼叫這個方法會產生相同結果[CList::GetSize](#getsize)方法。

### <a name="example"></a>範例

  範例，請參閱[CList::RemoveHead](#removehead)。

##  <a name="gethead"></a>  CList::GetHead

取得此清單的標頭項目 （或前端的項目參考）。

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>參數

*TYPE*<br/>
樣板參數清單中指定的物件類型。

### <a name="return-value"></a>傳回值

如果清單是**const**，`GetHead`傳回一份清單的開頭處的項目。 這可讓函式只能用在指派陳述式的右邊，並防止修改的清單。

如果清單不是**const**，`GetHead`傳回位於清單頂端的項目參考。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`GetHead`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](#isempty)若要驗證清單包含項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

##  <a name="getheadposition"></a>  CList::GetHeadPosition

取得此清單的標頭項目的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果清單是空的則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

##  <a name="getnext"></a>  CList::GetNext

取得所識別的清單項目*rPosition*，然後設定*rPosition*位置值的清單中的下一個項目。

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
樣板參數清單中指定的項目類型。

*rPosition*<br/>
前一個位置值的參考`GetNext`， [GetHeadPosition](#getheadposition)，或其他成員函式呼叫。

### <a name="return-value"></a>傳回值

如果清單是**const**，`GetNext`傳回一份清單的項目。 這可讓函式只能用在指派陳述式的右邊，並防止修改的清單。

如果清單不是**const**，`GetNext`傳回之清單項目的參考。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您可以使用`GetNext`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetHeadPosition`或`Find`。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

如果擷取的項目是在清單中，最後一則新值`rPosition`設為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

##  <a name="getprev"></a>  CList::GetPrev

取得所識別的清單項目`rPosition`，然後設定`rPosition`先前的項目清單中的位置值。

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
樣板參數清單中指定的項目類型。

*rPosition*<br/>
前一個位置值的參考`GetPrev`或其他成員函式呼叫。

### <a name="return-value"></a>傳回值

如果清單是**const**，`GetPrev`傳回一份清單的開頭處的項目。 這可讓函式只能用在指派陳述式的右邊，並防止修改的清單。

如果清單不是**const**，`GetPrev`傳回之清單項目的參考。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您可以使用`GetPrev`反向反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetTailPosition`或`Find`。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

如果擷取的項目是在清單中，第一則新值*rPosition*設為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

##  <a name="getsize"></a>  CList::GetSize

傳回清單項目數目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

清單中的項目數。

### <a name="remarks"></a>備註

呼叫這個方法來擷取在清單中的項目數。  呼叫這個方法會產生相同結果[CList::GetCount](#getcount)方法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

##  <a name="gettail"></a>  CList::GetTail

取得`CObject`指標，表示此清單的結尾項目。

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
樣板參數清單中指定的項目類型。

### <a name="return-value"></a>傳回值

請參閱的傳回值描述[GetHead](../../mfc/reference/coblist-class.md#gethead)。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`GetTail`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)若要驗證清單包含項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

##  <a name="gettailposition"></a>  CList::GetTailPosition

取得此清單的結尾元素的位置如果清單是空的則為 NULL。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果清單是空的則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

##  <a name="insertafter"></a>  CList::InsertAfter

將這份清單的項目之後的指定位置處的項目。

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
傳回先前的位置值`GetNext`， `GetPrev`，或`Find`成員函式呼叫。

*ARG_TYPE*<br/>
指定的清單項目類型的樣板參數。

*newElement*<br/>
要加入這份清單中的項目。

### <a name="return-value"></a>傳回值

可用於反覆項目或清單項目擷取位置值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

##  <a name="insertbefore"></a>  CList::InsertBefore

將項目加入這份清單中相同項目之前的指定位置。

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
傳回先前的位置值`GetNext`， `GetPrev`，或`Find`成員函式呼叫。

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*newElement*<br/>
要加入這份清單中的項目。

### <a name="return-value"></a>傳回值

可用於反覆項目或清單項目擷取位置值。

### <a name="remarks"></a>備註

如果*位置*是 NULL 時，項目插入清單的標頭。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

##  <a name="isempty"></a>  CList::IsEmpty

指出此清單是否包含任何項目。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果這份清單是空的則為非零否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

##  <a name="removeall"></a>  CList::RemoveAll

從這個清單中移除所有項目，並釋放相關聯的記憶體。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果清單已經是空的則會不產生任何錯誤。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

##  <a name="removeat"></a>  CList::RemoveAt

從這個清單中移除指定的項目。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>參數

*位置*<br/>
要從清單中移除之項目的位置。

### <a name="remarks"></a>備註

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

##  <a name="removehead"></a>  CList::RemoveHead

移除清單的標頭中的項目，並傳回的指標。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>參數

*TYPE*<br/>
樣板參數清單中指定的項目類型。

### <a name="return-value"></a>傳回值

先前在清單的標頭項目。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`RemoveHead`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](#isempty)若要驗證清單包含項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

##  <a name="removetail"></a>  CList::RemoveTail

移除清單結尾的項目，並傳回的指標。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>參數

*TYPE*<br/>
樣板參數清單中指定的項目類型。

### <a name="return-value"></a>傳回值

原本在清單結尾的項目。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`RemoveTail`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](#isempty)若要驗證清單包含項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

##  <a name="setat"></a>  CList::SetAt

位置類型的變數是索引鍵的清單。

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*pos*<br/>
要設定之項目的位置。

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*newElement*<br/>
要加入至清單的項目。

### <a name="remarks"></a>備註

它不相同索引中，而且您無法處理您自己的位置值。 `SetAt` 寫入至指定的位置清單中的項目。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMap 類別](../../mfc/reference/cmap-class.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)
