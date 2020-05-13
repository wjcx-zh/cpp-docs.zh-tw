---
title: 弦元素功能I類
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 32980e19443cb17a3a688c85ff21195c60ed2124
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330595"
---
# <a name="cstringelementtraitsi-class"></a>弦元素功能I類

此類提供與集合類物件中存儲的字串相關的靜態函數。 它類似於[CStringElementTraits,](../../atl/reference/cstringelementtraits-class.md)但執行不區分大小寫的比較。

## <a name="syntax"></a>語法

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合中的數據類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[弦元素特徵I::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|
|[弦元素特徵I:OUTARGTYPE](#outargtype)|用於從集合類物件檢索元素的數據類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[弦元素特徵I:比較元素](#compareelements)|呼叫此靜態函數以比較兩個字串元素以實現相等性,忽略情況下的差異。|
|[弦元素特徵I::比較元素排序](#compareelementsordered)|呼叫此靜態函數以比較兩個字串元素,忽略情況下的差異。|
|[弦樂元素:哈希](#hash)|呼叫此靜態函數以計算給定字串元素的哈希值。|

## <a name="remarks"></a>備註

此類提供用於比較字串和創建哈希值的靜態函數。 當使用集合類存儲基於字串的數據時,這些函數非常有用。 當要處理字串物件作為引用處理時,請使用[CStringRefElementTraits。](../../atl/reference/cstringrefelementtraits-class.md)

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[元素庫](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a>弦元素特徵I:比較元素

呼叫此靜態函數以比較兩個字串元素以實現相等性,忽略情況下的差異。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串元素。

*str2*<br/>
第二個字串元素。

### <a name="return-value"></a>傳回值

如果元素相等,則返回 true,否則為 false。

### <a name="remarks"></a>備註

比較不區分大小寫。

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>弦元素特徵I::比較元素排序

呼叫此靜態函數以比較兩個字串元素,忽略情況下的差異。

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

### <a name="remarks"></a>備註

比較不區分大小寫。

## <a name="cstringelementtraitsihash"></a><a name="hash"></a>弦樂元素:哈希

呼叫此靜態函數以計算給定字串元素的哈希值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>參數

*Str*<br/>
字串元素。

### <a name="return-value"></a>傳回值

傳回使用字串內容計算的哈希值。

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a>弦元素特徵I::INARGTYPE

用於向集合類物件添加元素的數據類型。

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a>弦元素特徵I:OUTARGTYPE

用於從集合類物件檢索元素的數據類型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[元素基礎類](../../atl/reference/celementtraitsbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CStringElementtraits 類別](../../atl/reference/cstringelementtraits-class.md)
