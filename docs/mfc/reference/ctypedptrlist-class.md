---
title: CTypedPtrList 類別
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 9233e83a08fde87c15be5cc1c42a2f1dd3b56511
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324502"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList 類別

為 `CPtrList`類別的物件提供類型安全「包裝函式」。

## <a name="syntax"></a>語法

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
基底類別的具類型的指標 list 類別;必須是指標清單類別 (`CObList`或`CPtrList`)。

*型別*<br/>
基底類別清單中所儲存的項目型別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|將 （讓新的標頭） 清單的標頭中的項目 （或另一個清單中的所有項目）。|
|[CTypedPtrList::AddTail](#addtail)|將 （讓新的結尾） 的清單結尾的項目 （或另一個清單中的所有項目）。|
|[CTypedPtrList::GetAt](#getat)|取得的項目中指定的位置。|
|[CTypedPtrList::GetHead](#gethead)|傳回 （不能是空的） 清單的標頭的項目。|
|[CTypedPtrList::GetNext](#getnext)|取得逐一查看的下一個項目。|
|[CTypedPtrList::GetPrev](#getprev)|取得逐一查看的上一個項目。|
|[CTypedPtrList::GetTail](#gettail)|傳回 （不能是空的） 清單的結尾項目。|
|[CTypedPtrList::RemoveHead](#removehead)|移除清單的標頭中的項目。|
|[CTypedPtrList::RemoveTail](#removetail)|移除清單結尾的項目。|
|[CTypedPtrList::SetAt](#setat)|設定的項目中指定的位置。|

## <a name="remarks"></a>備註

當您使用`CTypedPtrList`而非`CObList`或是`CPtrList`、C++型別檢查功能，有助於排除不相符的指標類型所造成的錯誤。

颾魤 ㄛ`CTypedPtrList`包裝函式會執行大部分的轉型，如果您將需要`CObList`或`CPtrList`。

因為所有`CTypedPtrList`函式會以內嵌方式，使用此範本不會不會大幅影響的大小或您的程式碼的速度。

清單衍生自`CObList`可以序列化，但衍生自`CPtrList`無法。

當 `CTypedPtrList` 物件被刪除，或當它的項目被移除時，只會移除指標，而非它們參考的實體。

如需有關使用`CTypedPtrList`，請參閱文章[集合](../../mfc/collections.md)並[樣板架構類別](../../mfc/template-based-classes.md)。

## <a name="example"></a>範例

此範例中建立的執行個體`CTypedPtrList`、 加入一個物件，將序列化至磁碟，清單，然後刪除物件：

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

##  <a name="addhead"></a>  CTypedPtrList::AddHead

此成員函式會呼叫`BASE_CLASS` **:: AddHead**。

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>參數

*型別*<br/>
基底類別清單中所儲存的項目型別。

*newElement*<br/>
要新增至此清單的物件指標。 允許 NULL 值。

*BASE_CLASS*<br/>
基底類別的具類型的指標 list 類別;必須是指標清單類別 ( [CObList](../../mfc/reference/coblist-class.md)或是[CPtrList](../../mfc/reference/cptrlist-class.md))。

*pNewList*<br/>
另一個指標[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)物件。 中的項目*pNewList*會新增至清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

第一個版本將加入新項目清單的標頭之前。 第二個版本將加入另一個清單之前標頭項目。

##  <a name="addtail"></a>  CTypedPtrList::AddTail

此成員函式會呼叫`BASE_CLASS` **:: AddTail**。

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>參數

*型別*<br/>
基底類別清單中所儲存的項目型別。

*newElement*<br/>
要新增至此清單的物件指標。 允許 NULL 值。

*BASE_CLASS*<br/>
基底類別的具類型的指標 list 類別;必須是指標清單類別 ( [CObList](../../mfc/reference/coblist-class.md)或是[CPtrList](../../mfc/reference/cptrlist-class.md))。

*pNewList*<br/>
另一個指標[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)物件。 中的項目*pNewList*會新增至清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

第一個版本會將新項目加入清單結尾之後。 第二個版本會將另一個清單項目加入清單結尾之後。

##  <a name="getat"></a>  CTypedPtrList::GetAt

位置類型的變數是索引鍵的清單。

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在清單中的項目類型的樣板參數。

*position*<br/>
傳回先前的位置值`GetHeadPosition`或`Find`成員函式呼叫。

### <a name="return-value"></a>傳回值

如果清單透過指標來存取`const CTypedPtrList`，然後`GetAt`會傳回範本參數所指定之型別的指標*型別*。 這可讓函式只能用在指派陳述式的右邊，並因此防止修改的清單。

如果清單直接或透過指標存取`CTypedPtrList`，然後`GetAt`會傳回範本參數所指定之類型的指標的參考*型別*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

它不相同索引中，而且您無法處理您自己的位置值。 `GetAt` 擷取`CObject`相關聯的指定位置的指標。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

此內嵌函式會呼叫`BASE_CLASS` **:: GetAt**。

##  <a name="gethead"></a>  CTypedPtrList::GetHead

取得表示標頭的項目，此清單的指標。

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在清單中的項目類型的樣板參數。

### <a name="return-value"></a>傳回值

如果清單透過指標來存取`const CTypedPtrList`，然後`GetHead`會傳回範本參數所指定之型別的指標*型別*。 這可讓函式只能用在指派陳述式的右邊，並因此防止修改的清單。

如果清單直接或透過指標存取`CTypedPtrList`，然後`GetHead`會傳回範本參數所指定之類型的指標的參考*型別*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`GetHead`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)若要驗證清單包含項目。

##  <a name="getnext"></a>  CTypedPtrList::GetNext

取得所識別的清單項目*rPosition*，然後設定*rPosition*位置值的清單中的下一個項目。

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定此清單中包含的項目類型的樣板參數。

*rPosition*<br/>
前一個位置值的參考`GetNext`， `GetHeadPosition`，或其他成員函式呼叫。

### <a name="return-value"></a>傳回值

如果清單透過指標來存取`const CTypedPtrList`，然後`GetNext`會傳回範本參數所指定之型別的指標*型別*。 這可讓函式只能用在指派陳述式的右邊，並因此防止修改的清單。

如果清單直接或透過指標存取`CTypedPtrList`，然後`GetNext`會傳回範本參數所指定之類型的指標的參考*型別*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您可以使用`GetNext`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetHeadPosition`或是[CPtrList::Find](../../mfc/reference/coblist-class.md#find)。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

如果擷取的項目是在清單中，最後一則新值*rPosition*設為 NULL。

您可在反覆運算期間移除項目。 範例，請參閱[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)。

##  <a name="getprev"></a>  CTypedPtrList::GetPrev

取得所識別的清單項目*rPosition*，然後設定*rPosition*先前的項目清單中的位置值。

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定此清單中包含的項目類型的樣板參數。

*rPosition*<br/>
前一個位置值的參考`GetPrev`或其他成員函式呼叫。

### <a name="return-value"></a>傳回值

如果清單透過指標來存取`const CTypedPtrList`，然後`GetPrev`會傳回範本參數所指定之型別的指標*型別*。 這可讓函式只能用在指派陳述式的右邊，並因此防止修改的清單。

如果清單直接或透過指標存取`CTypedPtrList`，然後`GetPrev`會傳回範本參數所指定之類型的指標的參考*型別*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您可以使用`GetPrev`反向反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetTailPosition`或`Find`。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

如果擷取的項目是在清單中，第一則新值*rPosition*設為 NULL。

##  <a name="gettail"></a>  CTypedPtrList::GetTail

取得表示標頭的項目，此清單的指標。

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在清單中的項目類型的樣板參數。

### <a name="return-value"></a>傳回值

如果清單透過指標來存取`const CTypedPtrList`，然後`GetTail`會傳回範本參數所指定之型別的指標*型別*。 這可讓函式只能用在指派陳述式的右邊，並因此防止修改的清單。

如果清單直接或透過指標存取`CTypedPtrList`，然後`GetTail`會傳回範本參數所指定之類型的指標的參考*型別*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`GetTail`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)若要驗證清單包含項目。

##  <a name="removehead"></a>  CTypedPtrList::RemoveHead

移除清單的標頭中的項目，並傳回它。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在清單中的項目類型的樣板參數。

### <a name="return-value"></a>傳回值

先前位於清單頂端的指標。 此指標為範本參數所指定的型別*型別*。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`RemoveHead`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)若要驗證清單包含項目。

##  <a name="removetail"></a>  CTypedPtrList::RemoveTail

移除清單結尾的項目，並傳回它。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在清單中的項目類型的樣板參數。

### <a name="return-value"></a>傳回值

先前位於清單結尾的指標。 此指標為範本參數所指定的型別*型別*。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`RemoveTail`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)若要驗證清單包含項目。

##  <a name="setat"></a>  CTypedPtrList::SetAt

此成員函式會呼叫`BASE_CLASS` **:: SetAt**。

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>參數

*pos*<br/>
要設定之項目的位置。

*型別*<br/>
基底類別清單中所儲存的項目型別。

*newElement*<br/>
要寫入至清單的物件指標。

### <a name="remarks"></a>備註

位置類型的變數是索引鍵的清單。 它不相同索引中，而且您無法處理您自己的位置值。 `SetAt` 寫入指定的位置清單中的物件指標。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

如需詳細註解，請參閱[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPtrList 類別](../../mfc/reference/cptrlist-class.md)<br/>
[CObList 類別](../../mfc/reference/coblist-class.md)
