---
title: CStringElementtraits 類別
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 078cfd5ff93bfcd8acc747904ea05e6a2e762bc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330626"
---
# <a name="cstringelementtraits-class"></a>CStringElementtraits 類別

此類提供存儲`CString`物件的集合類使用的靜態函數。

## <a name="syntax"></a>語法

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合中的數據類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[弦元素::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|
|[弦元素::OUTARGTYPE](#outargtype)|用於從集合類物件檢索元素的數據類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[弦元素::比較元素](#compareelements)|(靜態)調用此函數以比較兩個字串元素以表示相等。|
|[弦元素::比較元素排序](#compareelementsordered)|(靜態)呼叫此函數以比較兩個字串元素。|
|[弦元素::複製元素](#copyelements)|(靜態)調用此函數以複製`CString`儲存在集合類物件中的元素。|
|[弦樂元素:哈希](#hash)|(靜態)呼叫此函數以計算給定字串元素的哈希值。|
|[弦元素::重新置放元素](#relocateelements)|(靜態)調用此函數以重新定位`CString`儲存在集合類物件中的元素。|

## <a name="remarks"></a>備註

此類提供用於複製、移動和比較字串以及創建哈希值的靜態函數。 當使用集合類存儲基於字串的數據時,這些函數非常有用。 當需要不區分大小寫的比較時,請使用[CStringElementTraitsI。](../../atl/reference/cstringelementtraitsi-class.md) 當字串物件要作為引用處理時,請使用[CStringRefElementTraits。](../../atl/reference/cstringrefelementtraits-class.md)

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** cstringt.h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a>弦元素::比較元素

調用此靜態函數以比較兩個字串元素以獲得相等性。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串元素。

*str2*<br/>
第二個字串元素。

### <a name="return-value"></a>傳回值

如果元素相等,則返回 true,否則為 false。

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>弦元素::比較元素排序

呼叫此靜態函數以比較兩個字串元素。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串元素。

*str2*<br/>
第二個字串元素。

### <a name="return-value"></a>傳回值

如果字串相同,則為零,如果*str1*小於*str2,* 則< 0;如果*str1*大於*str2,* 則> 0。 [CStringT::比較](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用於執行比較。

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a>弦元素::複製元素

呼叫此靜態函數以複製`CString`儲存在集合類物件中的元素。

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
指向將接收複製數據的第一個元素的指標。

*pSrc*<br/>
指向要複製的第一個元素的指標。

*n 元素*<br/>
要複製的項目數目。

### <a name="remarks"></a>備註

源元素和目標元素不應重疊。

## <a name="cstringelementtraitshash"></a><a name="hash"></a>弦樂元素:哈希

呼叫此靜態函數以計算給定字串元素的哈希值。

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>參數

*Str*<br/>
字串元素。

### <a name="return-value"></a>傳回值

傳回使用字串內容計算的哈希值。

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a>弦元素::INARGTYPE

用於向集合類物件添加元素的數據類型。

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a>弦元素::OUTARGTYPE

用於從集合類物件檢索元素的數據類型。

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>弦元素::重新置放元素

調用此靜態函數以重新定位`CString`儲存在集合類物件中的元素。

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
指向將接收重新置放數據的第一個元素的指標。

*pSrc*<br/>
指向要重新置放的第一個元素的指標。

*n 元素*<br/>
要重新置放的元素數。

### <a name="remarks"></a>備註

此靜態函數稱為[memmove,](../../c-runtime-library/reference/memmove-wmemmove.md)對於大多數數據類型來說,這就足夠了。 如果要移動的物件包含指向其自己的成員的指標,則需要重寫此靜態函數。

## <a name="see-also"></a>另請參閱

[元素基礎類](../../atl/reference/celementtraitsbase-class.md)<br/>
[弦元素功能I類](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
