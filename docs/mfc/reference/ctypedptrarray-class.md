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
ms.openlocfilehash: db24e3992e5db70895ccc2908dba108de843bcdc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215942"
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
具類型指標陣列類別的基類;必須是陣列類別（ `CObArray` 或 `CPtrArray` ）。

*TYPE*<br/>
儲存在基類陣列中的元素類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CTypedPtrArray：： Add](#add)|將新的專案加入至陣列的結尾。 視需要成長陣列|
|[CTypedPtrArray：： Append](#append)|將一個陣列的內容加入至另一個陣列的結尾。 視需要成長陣列|
|[CTypedPtrArray：： Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CTypedPtrArray：： Parameters.alternatefilters.elementat](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CTypedPtrArray：： GetAt](#getat)|傳回給定索引的值。|
|[CTypedPtrArray：： InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CTypedPtrArray：： SetAt](#setat)|設定給定索引的值；不容許陣列成長。|
|[CTypedPtrArray：： SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CTypedPtrArray：： operator \[\]](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

當您使用 `CTypedPtrArray` 而不是 `CPtrArray` 或時 `CObArray` ，c + + 類型檢查功能有助於消除因指標類型不相符而造成的錯誤。

此外， `CTypedPtrArray` 如果您使用或，包裝函式會執行大部分需要的轉換 `CObArray` `CPtrArray` 。

由於所有函式 `CTypedPtrArray` 都是內嵌的，因此使用此範本並不會大幅影響程式碼的大小或速度。

如需使用的詳細資訊 `CTypedPtrArray` ，請參閱文章[集合](../../mfc/collections.md)和以[範本為基礎的類別](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`BASE_CLASS`

`CTypedPtrArray`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="ctypedptrarrayadd"></a><a name="add"></a>CTypedPtrArray：： Add

此成員函式會呼叫 `BASE_CLASS` **：： Add**。

```
INT_PTR Add(TYPE newElement);
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定要加入至陣列的元素類型。

*newElement*<br/>
要加入至此陣列的元素。

### <a name="return-value"></a>傳回值

已加入之元素的索引。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： Add](../../mfc/reference/cobarray-class.md#add)。

## <a name="ctypedptrarrayappend"></a><a name="append"></a>CTypedPtrArray：： Append

此成員函式會呼叫 `BASE_CLASS` ：： Append * *。

```
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
具類型指標陣列類別的基類;必須是陣列類別（ [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*TYPE*<br/>
儲存在基類陣列中的元素類型。

*src*<br/>
要附加至陣列之元素的來源。

### <a name="return-value"></a>傳回值

第一個附加元素的索引。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： Append](../../mfc/reference/cobarray-class.md#append)。

## <a name="ctypedptrarraycopy"></a><a name="copy"></a>CTypedPtrArray：： Copy

此成員函式會呼叫 `BASE_CLASS` **：： Copy**。

```cpp
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
具類型指標陣列類別的基類;必須是陣列類別（ [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*TYPE*<br/>
儲存在基類陣列中的元素類型。

*src*<br/>
要複製到陣列之元素的來源。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： Copy](../../mfc/reference/cobarray-class.md#copy)。

## <a name="ctypedptrarrayelementat"></a><a name="elementat"></a>CTypedPtrArray：： Parameters.alternatefilters.elementat

這個內嵌函數會呼叫 `BASE_CLASS` **：： parameters.alternatefilters.elementat**。

```
TYPE& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定儲存在此陣列中的元素類型。

*nIndex*<br/>
大於或等於0，且小於或等於 `BASE_CLASS` **：： system.array.getupperbound**所傳回之值的整數索引。

### <a name="return-value"></a>傳回值

*NIndex*所指定之位置的專案暫時參考。 此元素屬於範本參數*類型*所指定的類型。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： parameters.alternatefilters.elementat](../../mfc/reference/cobarray-class.md#elementat)。

## <a name="ctypedptrarraygetat"></a><a name="getat"></a>CTypedPtrArray：： GetAt

這個內嵌函數會呼叫 `BASE_CLASS` **：： GetAt**。

```
TYPE GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定儲存在陣列中的元素類型。

*nIndex*<br/>
大於或等於0，且小於或等於 `BASE_CLASS` **：： system.array.getupperbound**所傳回之值的整數索引。

### <a name="return-value"></a>傳回值

*NIndex*所指定之位置的元素複本。 此元素屬於範本參數*類型*所指定的類型。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： GetAt](../../mfc/reference/cobarray-class.md#getat)

## <a name="ctypedptrarrayinsertat"></a><a name="insertat"></a>CTypedPtrArray：： InsertAt

此成員函式會呼叫 `BASE_CLASS` **：： InsertAt**。

```cpp
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
可能大於[CObArray：： system.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)所傳回之值的整數索引。

*TYPE*<br/>
儲存在基類陣列中的元素類型。

*newElement*<br/>
要放在這個陣列中的物件指標。 允許**Null**值的*newElement* 。

*nCount*<br/>
此元素應該插入的次數（預設為1）。

*nStartIndex*<br/>
可能大於所傳回之值的整數索引 `CObArray::GetUpperBound` 。

*BASE_CLASS*<br/>
具類型指標陣列類別的基類;必須是陣列類別（ [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md)）。

*pNewArray*<br/>
另一個陣列，其中包含要加入至此陣列的元素。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： InsertAt](../../mfc/reference/cobarray-class.md#insertat)。

## <a name="ctypedptrarrayoperator--"></a><a name="operator_at"></a>CTypedPtrArray：： operator []

這些內嵌運算子會呼叫 `BASE_CLASS` **：： operator []**。

```
TYPE& operator[ ](int_ptr nindex);
TYPE operator[ ](int_ptr nindex) const;
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定儲存在陣列中的元素類型。

*nIndex*<br/>
大於或等於0，且小於或等於 `BASE_CLASS` **：： system.array.getupperbound**所傳回之值的整數索引。

### <a name="remarks"></a>備註

第一個運算子（針對 not 的陣列呼叫 **`const`** ）可用於指派語句的右邊（右值）或左邊（左值）。 第二個（針對 **`const`** 陣列叫用）只能用在右邊。

如果注標（在指派語句的左邊或右邊）超出範圍，則為該程式庫的 Debug 版本。

## <a name="ctypedptrarraysetat"></a><a name="setat"></a>CTypedPtrArray：： SetAt

此成員函式會呼叫 `BASE_CLASS` **：： SetAt**。

```cpp
void SetAt(
    INT_PTR nIndex,
    TYPE ptr);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於[CObArray：： system.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)所傳回之值的整數索引。

*TYPE*<br/>
儲存在基類陣列中的元素類型。

*ptr*<br/>
要插入 nIndex 之陣列中的元素指標。 允許 Null 值。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： SetAt](../../mfc/reference/cobarray-class.md#setat)。

## <a name="ctypedptrarraysetatgrow"></a><a name="setatgrow"></a>CTypedPtrArray：： SetAtGrow

此成員函式會呼叫 `BASE_CLASS` **：： SetAtGrow**。

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    TYPE newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0的整數索引。

*TYPE*<br/>
儲存在基類陣列中的元素類型。

*newElement*<br/>
要加入至這個陣列的物件指標。 允許**Null**值。

### <a name="remarks"></a>備註

如需更詳細的備註，請參閱[CObArray：： SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPtrArray 類別](../../mfc/reference/cptrarray-class.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)
