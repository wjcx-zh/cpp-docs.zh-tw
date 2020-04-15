---
title: CStringRefelementtraits 類別
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: b4dd76b9592b255a1553be3ca7a249f58fb2672e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330574"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefelementtraits 類別

此類提供與集合類物件中存儲的字串相關的靜態函數。 字串物件作為引用處理。

## <a name="syntax"></a>語法

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合中的數據類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStringRefElement::比較元素](#compareelements)|調用此靜態函數以比較兩個字串元素以獲得相等性。|
|[CStringRefElement::比較元素排序](#compareelementsordered)|呼叫此靜態函數以比較兩個字串元素。|
|[弦樂元素:哈希](#hash)|呼叫此靜態函數以計算給定字串元素的哈希值。|

## <a name="remarks"></a>備註

此類提供用於比較字串和創建哈希值的靜態函數。 當使用集合類存儲基於字串的數據時,這些函數非常有用。 與[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)和[CStringElementTraitsI 不同](../../atl/reference/cstringelementtraitsi-class.md)`CStringRefElementTraits``CString`, 這些參數作為**const**`CString&`引用傳遞。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[元素庫](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElement::比較元素

調用此靜態函數以比較兩個字串元素以獲得相等性。

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>參數

*元素1*<br/>
第一個字串元素。

*元素2*<br/>
第二個字串元素。

### <a name="return-value"></a>傳回值

如果元素相等,則返回 true,否則為 false。

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElement::比較元素排序

呼叫此靜態函數以比較兩個字串元素。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串元素。

*str2*<br/>
第二個字串元素。

### <a name="return-value"></a>傳回值

如果字串相同,則為零,如果*str1*小於*str2,* 則< 0;如果*str1*大於*str2,* 則> 0。 [CStringT::比較](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用於執行比較。

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>弦樂元素:哈希

呼叫此靜態函數以計算給定字串元素的哈希值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>參數

*Str*<br/>
字串元素。

### <a name="return-value"></a>傳回值

傳回使用字串內容計算的哈希值。

## <a name="see-also"></a>另請參閱

[元素基礎類](../../atl/reference/celementtraitsbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
