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
ms.openlocfilehash: 40dbfb822e71309e9675aba14d46d333ffa4ee06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373269"
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
類型化指標清單類的基類;必須指定針清單類別(`CObList``CPtrList`或 。

*類型*<br/>
儲存在基類別清單中的元素的類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTypedPtrlist::新增頭](#addhead)|將元素(或其他清單中的所有元素)添加到列表的頭部(製作新頭)。|
|[CTypedPtrlist::新增尾數](#addtail)|將元素(或其他清單中的所有元素)添加到清單的尾部(製作新尾部)。|
|[CTypedPtrlist::取得At](#getat)|獲取給定位置的元素。|
|[CTypedPtrlist:取得頭](#gethead)|返回清單的頭元素(不能為空)。|
|[CTypedPtrList::取得下一個](#getnext)|獲取下一個反覆運算元素。|
|[CTypedPtrList:GetPrev](#getprev)|獲取用於反覆運算的前一個元素。|
|[CTypedPtrlist:GetTail](#gettail)|返回清單的尾部元素(不能為空)。|
|[CTypedPtrlist::刪除頭](#removehead)|從清單的頭部中移除元素。|
|[CTypedPtrlist::刪除尾翼](#removetail)|從清單尾部中移除元素。|
|[CTypedPtrlist::SetAt](#setat)|將元素設置在給定位置。|

## <a name="remarks"></a>備註

使用`CTypedPtrList``CObList`而不是`CPtrList`或時,C++類型檢查工具有助於消除由不匹配的指標類型引起的錯誤。

此外,`CTypedPtrList`包裝器執行使用`CObList``CPtrList`或時所需的大部分強制轉換。

由於所有`CTypedPtrList`函數都是內聯的,因此使用此範本不會顯著影響代碼的大小或速度。

派生自的清單`CObList`可以序列化,但派生`CPtrList`自 的清單不能。

當 `CTypedPtrList` 物件被刪除，或當它的項目被移除時，只會移除指標，而非它們參考的實體。

有關`CTypedPtrList`使用的詳細資訊,請參閱文章[集合](../../mfc/collections.md)與[基於樣本的類別](../../mfc/template-based-classes.md)。

## <a name="example"></a>範例

本範例建立`CTypedPtrList`的實體,新增物件,將清單序列化到磁碟,然後刪除該物件:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrlist::新增頭

此成員函數呼叫`BASE_CLASS` **::AddHead**。

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>參數

*類型*<br/>
儲存在基類別清單中的元素的類型。

*新元素*<br/>
要添加到此清單的物件指標。 允許 NULL 值。

*BASE_CLASS*<br/>
類型化指標清單類的基類;必須是指針清單類[(CObList](../../mfc/reference/coblist-class.md)或[CPtrList)。](../../mfc/reference/cptrlist-class.md)

*pNewlist*<br/>
指向另一個[CTypedPtrList 物件的指標](../../mfc/reference/ctypedptrlist-class.md)。 *pNewList*中的元素將添加到此清單中。

### <a name="return-value"></a>傳回值

第一個版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>備註

第一個版本在列表的頭部之前添加新元素。 第二個版本在頭之前添加另一個元素清單。

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrlist::新增尾數

此成員函數呼叫`BASE_CLASS` **::AddTail**。

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>參數

*類型*<br/>
儲存在基類別清單中的元素的類型。

*新元素*<br/>
要添加到此清單的物件指標。 允許 NULL 值。

*BASE_CLASS*<br/>
類型化指標清單類的基類;必須是指針清單類[(CObList](../../mfc/reference/coblist-class.md)或[CPtrList)。](../../mfc/reference/cptrlist-class.md)

*pNewlist*<br/>
指向另一個[CTypedPtrList 物件的指標](../../mfc/reference/ctypedptrlist-class.md)。 *pNewList*中的元素將添加到此清單中。

### <a name="return-value"></a>傳回值

第一個版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>備註

第一個版本在清單尾號後添加新元素。 第二個版本在清單尾號之後添加另一個元素清單。

## <a name="ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrlist::取得At

位置類型的變數是清單的鍵。

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定存儲在清單中的元素的類型。

*位置*<br/>
由上一個`GetHeadPosition``Find`或成員函數調用返回的定位值。

### <a name="return-value"></a>傳回值

如果清單通過指向`const CTypedPtrList`的指標訪問,則`GetAt`返回範本參數*TYPE*指定的類型的指標。 這允許函數僅在賦值語句的右側使用,從而保護清單不進行修改。

如果直接或通過指向的指標訪問清單`CTypedPtrList`,則`GetAt`返回對範本參數*TYPE*指定的類型的指標的引用。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

它與索引不同,並且不能自己對位置值進行操作。 `GetAt`檢索與`CObject`給定位置關聯的指標。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

此內聯函數呼叫`BASE_CLASS` **::GetAt**。

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrlist:取得頭

獲取表示此列表頭元素的指標。

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定存儲在清單中的元素的類型。

### <a name="return-value"></a>傳回值

如果清單通過指向`const CTypedPtrList`的指標訪問,則`GetHead`返回範本參數*TYPE*指定的類型的指標。 這允許函數僅在賦值語句的右側使用,從而保護清單不進行修改。

如果直接或通過指向的指標訪問清單`CTypedPtrList`,則`GetHead`返回對範本參數*TYPE*指定的類型的指標的引用。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

在調用`GetHead`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)驗證清單是否包含元素。

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList::取得下一個

取得*r定位*識別的清單元素,然後將*r 定位*設定到清單中下一個條目的" 位置"

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
指定此清單中包含的元素類型的樣本參數。

*r 定位*<br/>
對前`GetNext``GetHeadPosition`一個成員函數調用返回的"位置"值的引用。

### <a name="return-value"></a>傳回值

如果清單通過指向`const CTypedPtrList`的指標訪問,則`GetNext`返回範本參數*TYPE*指定的類型的指標。 這允許函數僅在賦值語句的右側使用,從而保護清單不進行修改。

如果直接或通過指向的指標訪問清單`CTypedPtrList`,則`GetNext`返回對範本參數*TYPE*指定的類型的指標的引用。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

如果使用呼叫`GetNext``GetHeadPosition`或[CPtrList 建立](../../mfc/reference/coblist-class.md#find)初始位置,則可以在轉寄的發單迴圈中使用:尋找 。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

如果檢索到的元素是清單中的最後一個元素,則*rValue*的新值將設置為 NULL。

可以在反覆運算期間刪除元素。 請參閱[COblist 的範例::刪除At。](../../mfc/reference/coblist-class.md#removeat)

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList:GetPrev

取得*rPosition*識別的清單元素,然後將*r 定位*設定到清單中上一個條目的" 位置"

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
指定此清單中包含的元素類型的樣本參數。

*r 定位*<br/>
對前`GetPrev`一個成員或其他成員函數調用返回的定位值的引用。

### <a name="return-value"></a>傳回值

如果清單通過指向`const CTypedPtrList`的指標訪問,則`GetPrev`返回範本參數*TYPE*指定的類型的指標。 這允許函數僅在賦值語句的右側使用,從而保護清單不進行修改。

如果直接或通過指向的指標訪問清單`CTypedPtrList`,則`GetPrev`返回對範本參數*TYPE*指定的類型的指標的引用。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

如果使用`GetPrev`調`GetTailPosition`用`Find`或 建立初始位置,則可以在反向反覆運算迴圈中使用。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

如果檢索到的元素是清單中的第一個元素,則*rValue*的新值將設置為 NULL。

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrlist:GetTail

獲取表示此列表頭元素的指標。

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定存儲在清單中的元素的類型。

### <a name="return-value"></a>傳回值

如果清單通過指向`const CTypedPtrList`的指標訪問,則`GetTail`返回範本參數*TYPE*指定的類型的指標。 這允許函數僅在賦值語句的右側使用,從而保護清單不進行修改。

如果直接或通過指向的指標訪問清單`CTypedPtrList`,則`GetTail`返回對範本參數*TYPE*指定的類型的指標的引用。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

在調用`GetTail`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)驗證清單是否包含元素。

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrlist::刪除頭

從清單的頭部刪除元素並返回它。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定存儲在清單中的元素的類型。

### <a name="return-value"></a>傳回值

以前位於清單頭的指標。 此指標的類型由範本參數*TYPE*指定。

### <a name="remarks"></a>備註

在調用`RemoveHead`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)驗證清單是否包含元素。

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrlist::刪除尾翼

從清單的尾部刪除元素並返回它。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定存儲在清單中的元素的類型。

### <a name="return-value"></a>傳回值

以前位於清單尾部分的指標。 此指標的類型由範本參數*TYPE*指定。

### <a name="remarks"></a>備註

在調用`RemoveTail`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)驗證清單是否包含元素。

## <a name="ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrlist::SetAt

此成員函數呼叫`BASE_CLASS` **::SetAt**。

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>參數

*Pos*<br/>
要設置的元素的位置。

*類型*<br/>
儲存在基類別清單中的元素的類型。

*新元素*<br/>
要寫入清單的物件指標。

### <a name="remarks"></a>備註

位置類型的變數是清單的鍵。 它與索引不同,並且不能自己對位置值進行操作。 `SetAt`將物件指標寫入清單中的指定位置。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

有關更詳細的註解,請參閱[COblist::setat](../../mfc/reference/coblist-class.md#setat)。

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPtrList 類別](../../mfc/reference/cptrlist-class.md)<br/>
[CObList 類別](../../mfc/reference/coblist-class.md)
