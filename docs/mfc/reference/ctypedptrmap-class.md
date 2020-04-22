---
title: CTypedPtrMap 類別
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: 410f0101fd0f8cda271fe0f2353b06b9e8d773b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754372"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap 類別

為指標對應類別 `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`和 `CMapStringToPtr`的物件提供類型安全「包裝函式」。

## <a name="syntax"></a>語法

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
類型化指標映射類的基類;必須是指針`CMapPtrToPtr`映射類`CMapWordToPtr``CMapStringToPtr``CMapPtrToWord`(、、、 或)。

*關鍵*<br/>
用作映射鍵的物件的類。

*價值*<br/>
存儲在地圖中的物件的類。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTypedPtrMap::取得NextAssoc](#getnextassoc)|獲取下一個反覆運算元素。|
|[CTypedPtrMap::尋找](#lookup)|傳`KEY`回基於`VALUE`的 。|
|[CTypedPtrMap:: 刪除鍵](#removekey)|刪除由鍵指定的元素。|
|[CTypedPtrMap::SetAt](#setat)|將元素插入到地圖中;如果找到匹配的鍵,則替換現有元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CTypedPtrMap::運算子\[\]](#operator_at)|將元素插入到地圖中。|

## <a name="remarks"></a>備註

使用`CTypedPtrMap`時,C++類型檢查工具有助於消除由不匹配的指標類型引起的錯誤。

由於所有`CTypedPtrMap`函數都是內聯的,因此使用此範本不會顯著影響代碼的大小或速度。

有關`CTypedPtrMap`使用的詳細資訊,請參閱文章[集合](../../mfc/collections.md)與[基於樣本的類別](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a>CTypedPtrMap::取得NextAssoc

在 中檢索地圖`rNextPosition`元素 ,`rNextPosition`然後更新 以引用地圖中的下一個元素。

```cpp
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*r 定位*<br/>
指定對上一個`GetNextAssoc``BASE_CLASS`或 **:: GetStart位置**呼叫傳回的定位值的引用。

*關鍵*<br/>
指定地圖鍵類型的範本參數。

*rKey*<br/>
指定檢索到的元素的返回鍵。

*價值*<br/>
指定地圖值類型的範本參數。

*rValue*<br/>
指定檢索到的元素的返回值。

### <a name="remarks"></a>備註

此函數對於反覆運算地圖中的所有元素最有用。 請注意,位置序列不一定與鍵值序列相同。

如果檢索到的元素是地圖中的最後一個元素,則的新`rNextPosition`值將設置為 NULL。

此內聯函數呼叫`BASE_CLASS` **::GetNextAssoc**。

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a>CTypedPtrMap::尋找

`Lookup`使用哈希演演演算法快速查找具有完全匹配的鍵的映射元素。

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
指定此映射類的基類的範本參數。

*key*<br/>
要抬起來的元素的鍵。

*價值*<br/>
指定此對應中儲存的值類型的樣本參數。

*rValue*<br/>
指定檢索到的元素的返回值。

### <a name="return-value"></a>傳回值

如果找到元素,則非零;否則 0。

### <a name="remarks"></a>備註

此內聯函數呼叫`BASE_CLASS` **::尋找**。

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a>CTypedPtrMap::運算符 |

此運算元只能在賦值語句(l值)的左側使用。

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>參數

*價值*<br/>
指定此對應中儲存的值類型的樣本參數。

*BASE_CLASS*<br/>
指定此映射類的基類的範本參數。

*key*<br/>
要在地圖中備份或創建的元素的鍵。

### <a name="remarks"></a>備註

如果沒有具有指定鍵的地圖元素,則創建新元素。 沒有等效於此運算符的「右側」(r 值),因為在地圖中可能找不到鍵。 使用`Lookup`成員函數進行元素檢索。

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a>CTypedPtrMap:: 刪除鍵

此成員函數呼叫`BASE_CLASS` **::刪除鍵**。

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
指定地圖鍵類型的範本參數。

*key*<br/>
要刪除的元素的鍵。

### <a name="return-value"></a>傳回值

如果發現並成功刪除條目,則非零;否則 0。

### <a name="remarks"></a>備註

有關更詳細的註解,請參閱[CMapStringToOb:::刪除鍵](../../mfc/reference/cmapstringtoob-class.md#removekey)。

## <a name="ctypedptrmapsetat"></a><a name="setat"></a>CTypedPtrMap::SetAt

此成員函數呼叫`BASE_CLASS` **::SetAt**。

```cpp
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
指定地圖鍵類型的範本參數。

*key*<br/>
指定新值的鍵值。

*newValue*<br/>
指定作為新元素值的物件指標。

### <a name="remarks"></a>備註

有關更詳細的註解,請參閱[CMapStringToOb::setat](../../mfc/reference/cmapstringtoob-class.md#setat)。

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 類別](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 類別](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr 類別](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr 類別](../../mfc/reference/cmapstringtoptr-class.md)
