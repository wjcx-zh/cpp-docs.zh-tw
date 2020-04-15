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
ms.openlocfilehash: a996bca471ce82a7c2adaaad67670ddef417eda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373285"
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
類型化指標數組類的基類;必須是陣列類別`CObArray`(`CPtrArray`或 。

*類型*<br/>
存儲在基類陣列中的元素的類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTypedPtrarray:: 新增](#add)|向陣列的末尾添加新元素。 如有必要,增大陣列|
|[CTypedPtrarray::追加](#append)|將一個陣列的內容添加到另一個陣列的末尾。 如有必要,增大陣列|
|[CTypedPtrarray:: 複製](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CTypedPtrarray::元素At](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CTypedPtrarray::取得At](#getat)|傳回給定索引的值。|
|[CTypedPtrarray::插入At](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CTypedPtrarray::SetAt](#setat)|設定給定索引的值；不容許陣列成長。|
|[CTypedPtrarray::SetAt增長](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CTypedPtrarray::運算子\[\]](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

使用`CTypedPtrArray``CPtrArray`而不是`CObArray`或時,C++類型檢查工具有助於消除由不匹配的指標類型引起的錯誤。

此外,`CTypedPtrArray`包裝器執行使用`CObArray``CPtrArray`或時所需的大部分強制轉換。

由於所有`CTypedPtrArray`函數都是內聯的,因此使用此範本不會顯著影響代碼的大小或速度。

有關`CTypedPtrArray`使用的詳細資訊,請參閱文章[集合](../../mfc/collections.md)與[基於樣本的類別](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrarray:: 新增

此成員函數呼叫`BASE_CLASS` **::新增**。

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>參數

*類型*<br/>
指定要添加到陣列的元素類型的範本參數。

*新元素*<br/>
要添加到此陣列的元素。

### <a name="return-value"></a>傳回值

添加元素的索引。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray:::添加](../../mfc/reference/cobarray-class.md#add)。

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrarray::追加

此成員函數調用`BASE_CLASS`::附加_。

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
類型化指標數組類的基類;必須是陣列類[(CObarray](../../mfc/reference/cobarray-class.md)或[CPtrArray)。](../../mfc/reference/cptrarray-class.md)

*類型*<br/>
存儲在基類陣列中的元素的類型。

*src*<br/>
要追加到陣列的元素的源。

### <a name="return-value"></a>傳回值

第一個附加元素的索引。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray:::附加 。](../../mfc/reference/cobarray-class.md#append)

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrarray:: 複製

此成員函數呼叫`BASE_CLASS` **::複製**。

```
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
類型化指標數組類的基類;必須是陣列類[(CObarray](../../mfc/reference/cobarray-class.md)或[CPtrArray)。](../../mfc/reference/cptrarray-class.md)

*類型*<br/>
存儲在基類陣列中的元素的類型。

*src*<br/>
要複製到陣列的元素的源。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray:::複製](../../mfc/reference/cobarray-class.md#copy)。

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrarray::元素At

此內聯函數呼叫`BASE_CLASS` **::ElementAt**。

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>參數

*類型*<br/>
指定存儲在此陣列中的元素類型的範本參數。

*nIndex*<br/>
大於或等於 0 且小於或`BASE_CLASS`等於 **::getUpperBound**返回的值的整數索引。

### <a name="return-value"></a>傳回值

對*nIndex*指定位置的元素的臨時引用。 此元素的類型由範本參數*TYPE*指定。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray::elementat](../../mfc/reference/cobarray-class.md#elementat)。

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrarray::取得At

此內聯函數呼叫`BASE_CLASS` **::GetAt**。

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定存儲在陣列中的元素的類型。

*nIndex*<br/>
大於或等於 0 且小於或`BASE_CLASS`等於 **::getUpperBound**返回的值的整數索引。

### <a name="return-value"></a>傳回值

*在 nIndex*指定的位置的元素的複本。 此元素的類型由範本參數*TYPE*指定。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray::GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrarray::插入At

此成員函數呼叫`BASE_CLASS` **::InsertAt**。

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
可能大於 CObarray 傳回的值的整數索引[::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*類型*<br/>
存儲在基類陣列中的元素的類型。

*新元素*<br/>
要放置在此陣列中的物件指標。 允許*新的*值**NULL**元素。

*n( N) Count*<br/>
應插入此元素的次數(預設值為1)。

*nStartIndex*<br/>
可能大於返回`CObArray::GetUpperBound`的值的整數索引。

*BASE_CLASS*<br/>
類型化指標數組類的基類;必須是陣列類[(CObarray](../../mfc/reference/cobarray-class.md)或[CPtrArray)。](../../mfc/reference/cptrarray-class.md)

*pNewArray*<br/>
另一個包含要添加到此陣列的元素的陣列。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray::插入 At](../../mfc/reference/cobarray-class.md#insertat)。

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrarray::運算符 |

這些內聯運算子呼叫`BASE_CLASS` **:: 運算子 ***。

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定存儲在陣列中的元素的類型。

*nIndex*<br/>
大於或等於 0 且小於或`BASE_CLASS`等於 **::getUpperBound**返回的值的整數索引。

### <a name="remarks"></a>備註

第一個運算符(稱為非**const**陣列)可以在賦值語句的右側(r 值)或左側(l 值)上使用。 第二個調用為**const**陣列,只能在右側使用。

庫的調試版本斷言下標(在賦值語句的左側或右側)是否超出邊界。

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrarray::SetAt

此成員函數呼叫`BASE_CLASS` **::SetAt**。

```
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等於 CObArray 傳回的值的整數索引[::getUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。

*類型*<br/>
存儲在基類陣列中的元素的類型。

*Ptr*<br/>
指向要在 nIndex 的陣列中插入的元素的指標。 允許 NULL 值。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray::setat](../../mfc/reference/cobarray-class.md#setat)。

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrarray::SetAt增長

此成員函數呼叫`BASE_CLASS` **::SetAtGrow**。

```
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 的整數索引。

*類型*<br/>
存儲在基類陣列中的元素的類型。

*新元素*<br/>
要添加到此陣列的物件指標。 允許**NULL**值。

### <a name="remarks"></a>備註

有關更詳細的註釋,請參閱[CObarray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray 類別](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)
