---
title: CTypedPtrArray 類別
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
ms.openlocfilehash: 080e47746b83b6ff12db9f6df0fc27bcd202bb51
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768681"
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray 類別

為 `CPtrArray` 或 `CObArray`類別的物件提供類型安全「包裝函式」。

## <a name="syntax"></a>語法

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrArray : public BASE_CLASS
```

#### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
基底類別的具類型的指標陣列類別;必須是陣列類別 (`CObArray`或`CPtrArray`)。

*型別*<br/>
基底類別的陣列中儲存的項目型別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTypedPtrArray::Add](#add)|將新項目加入至陣列的結尾。 必要時讓陣列成長|
|[CTypedPtrArray::Append](#append)|將另一個陣列的內容。 必要時讓陣列成長|
|[CTypedPtrArray::Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CTypedPtrArray::ElementAt](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CTypedPtrArray::GetAt](#getat)|傳回給定索引的值。|
|[CTypedPtrArray::InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CTypedPtrArray::SetAt](#setat)|設定給定索引的值；不容許陣列成長。|
|[CTypedPtrArray::SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CTypedPtrArray::operator \[ \]](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

當您使用`CTypedPtrArray`而非`CPtrArray`或`CObArray`，c + + 型別檢查功能，有助於排除不相符的指標類型所造成的錯誤。

颾魤 ㄛ`CTypedPtrArray`包裝函式會執行大部分的轉型，如果您將需要`CObArray`或`CPtrArray`。

因為所有`CTypedPtrArray`函式會以內嵌方式，使用此範本不會不會大幅影響的大小或您的程式碼的速度。

如需有關使用`CTypedPtrArray`，請參閱文章[集合](../../mfc/collections.md)並[樣板架構類別](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

##  <a name="add"></a>  CTypedPtrArray::Add

此成員函式會呼叫`BASE_CLASS` **:: 新增**。

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>參數

*型別*<br/>
指定要加入至陣列元素的類型樣板參數。

*newElement*<br/>
要加入至這個陣列的項目。

### <a name="return-value"></a>傳回值

加入之項目的索引。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::Add](../../mfc/reference/cobarray-class.md#add)。

##  <a name="append"></a>  CTypedPtrArray::Append

此成員函式呼叫`BASE_CLASS`:: Append * *。

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
基底類別的具類型的指標陣列類別;必須是陣列類別 ( [CObArray](../../mfc/reference/cobarray-class.md)或是[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*型別*<br/>
基底類別的陣列中儲存的項目型別。

*src*<br/>
要附加至陣列項目的來源。

### <a name="return-value"></a>傳回值

第一個附加的項目索引。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::Append](../../mfc/reference/cobarray-class.md#append)。

##  <a name="copy"></a>  CTypedPtrArray::Copy

此成員函式會呼叫`BASE_CLASS` **:: 複製**。

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
基底類別的具類型的指標陣列類別;必須是陣列類別 ( [CObArray](../../mfc/reference/cobarray-class.md)或是[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*型別*<br/>
基底類別的陣列中儲存的項目型別。

*src*<br/>
要複製到陣列之項目的來源。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)。

##  <a name="elementat"></a>  CTypedPtrArray::ElementAt

此內嵌函式會呼叫`BASE_CLASS` **:: ElementAt**。

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存此陣列中的項目類型的樣板參數。

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值`BASE_CLASS` **:: GetUpperBound**。

### <a name="return-value"></a>傳回值

所指定的位置處的項目的臨時參考*nIndex*。 這個項目是範本參數所指定之型別的*型別*。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)。

##  <a name="getat"></a>  CTypedPtrArray::GetAt

此內嵌函式會呼叫`BASE_CLASS` **:: GetAt**。

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在陣列中的項目類型的樣板參數。

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值`BASE_CLASS` **:: GetUpperBound**。

### <a name="return-value"></a>傳回值

所指定的位置處的項目副本*nIndex*。 這個項目是範本參數所指定之型別的*型別*。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)

##  <a name="insertat"></a>  CTypedPtrArray::InsertAt

此成員函式會呼叫`BASE_CLASS` **:: InsertAt**。

```
void InsertAt(
    INT_PTR nIndex,
    TYPE newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
可能會大於所傳回的值的整數索引[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*型別*<br/>
基底類別的陣列中儲存的項目型別。

*newElement*<br/>
要放在此陣列中的物件指標。 A *newElement*的值**NULL**允許。

*nCount*<br/>
次數，此項目應該插入 （預設值為 1）。

*nStartIndex*<br/>
可能會大於所傳回的值的整數索引`CObArray::GetUpperBound`。

*BASE_CLASS*<br/>
基底類別的具類型的指標陣列類別;必須是陣列類別 ( [CObArray](../../mfc/reference/cobarray-class.md)或是[CPtrArray](../../mfc/reference/cptrarray-class.md))。

*pNewArray*<br/>
另一個陣列，包含要加入至這個陣列的項目。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)。

##  <a name="operator_at"></a>  CTypedPtrArray::operator [ ]

這些內嵌的運算子呼叫`BASE_CLASS` **:: 運算子 []**。

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>參數

*型別*<br/>
指定儲存在陣列中的項目類型的樣板參數。

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值`BASE_CLASS` **:: GetUpperBound**。

### <a name="remarks"></a>備註

陣列未呼叫的第一個運算子**const**，可用的權限 （右值） 或指派陳述式左邊 （左值）。 第二個，叫用**const**陣列，可以使用只在右邊。

偵錯版本的程式庫判斷提示的註標 （請在左邊或右邊則在指派陳述式） 是否超出範圍。

##  <a name="setat"></a>  CTypedPtrArray::SetAt

此成員函式會呼叫`BASE_CLASS` **:: SetAt**。

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*型別*<br/>
基底類別的陣列中儲存的項目型別。

*ptr*<br/>
要插入 nIndex 陣列中元素的指標。 允許 NULL 值。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)。

##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow

此成員函式會呼叫`BASE_CLASS` **:: SetAtGrow**。

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 的整數索引。

*型別*<br/>
基底類別的陣列中儲存的項目型別。

*newElement*<br/>
要加入至這個陣列的物件指標。 A **NULL**允許值。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray 類別](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)
