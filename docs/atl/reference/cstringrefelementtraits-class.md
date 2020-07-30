---
title: CStringRefElementTraits 類別
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
ms.openlocfilehash: 6fa8772033a5a82940cf30b2a73d6ea356269d67
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226551"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits 類別

這個類別會提供與集合類別物件中所儲存之字串相關的靜態函式。 字串物件會以參考的形式處理。

## <a name="syntax"></a>語法

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
要儲存在集合中的資料類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|呼叫此靜態函式以比較兩個字串元素是否相等。|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|呼叫此靜態函式以比較兩個字串元素。|
|[CStringRefElementTraits：： Hash](#hash)|呼叫此靜態函式以計算給定字串元素的雜湊值。|

## <a name="remarks"></a>備註

這個類別會提供用來比較字串和建立雜湊值的靜態函數。 使用集合類別來儲存以字串為基礎的資料時，這些函式會很有用。 不同于[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)， `CStringRefElementTraits` 會使 `CString` 引數傳遞為 **`const`** `CString&` 參考。

如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>需求

**標頭：** atlcoll。h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements

呼叫此靜態函式以比較兩個字串元素是否相等。

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>參數

*element1*<br/>
第一個字串元素。

*element2*<br/>
第二個字串元素。

### <a name="return-value"></a>傳回值

如果元素相等，則傳回 true，否則傳回 false。

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered

呼叫此靜態函式以比較兩個字串元素。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串元素。

*str2*<br/>
第二個字串元素。

### <a name="return-value"></a>傳回值

如果字串相同，則為零; 如果*str1*小於*str2*，則 < 0; 如果*str1*大於*str2*，> 則為0。 [CStringT：： Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法是用來執行比較。

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits：： Hash

呼叫此靜態函式以計算給定字串元素的雜湊值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>參數

*字串*<br/>
String 元素。

### <a name="return-value"></a>傳回值

傳回使用字串內容來計算的雜湊值。

## <a name="see-also"></a>另請參閱

[CElementTraitsBase 類別](../../atl/reference/celementtraitsbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
