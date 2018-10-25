---
title: CStringElementTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51e612e889c06b8736e13e3c0fe04baf07b11a9b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078280"
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits 類別

這個類別會提供使用儲存的集合類別的靜態函式`CString`物件。

## <a name="syntax"></a>語法

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>參數

*T*<br/>
若要在集合中儲存的資料型別。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|（靜態）呼叫此函式來比較兩個字串項目相等。|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|（靜態）呼叫此函式來比較兩個字串項目。|
|[CStringElementTraits::CopyElements](#copyelements)|（靜態）呼叫此函式來複製`CString`集合類別物件中儲存的項目。|
|[CStringElementTraits::Hash](#hash)|（靜態）呼叫此函式來計算雜湊值，指定的字串項目。|
|[CStringElementTraits::RelocateElements](#relocateelements)|（靜態）呼叫此函式來重新放置`CString`集合類別物件中儲存的項目。|

## <a name="remarks"></a>備註

這個類別提供靜態函式，如複製、 移動和比較字串，以及如何建立雜湊值。 使用集合類別來儲存字串為基礎的資料時，則這些函式會很有用。 使用[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)需要不區分大小寫的比較時。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)字串物件時處理做為參考。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** cstringt.h

##  <a name="compareelements"></a>  CStringElementTraits::CompareElements

呼叫此靜態函式來比較兩個字串項目相等。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串項目。

*str2*<br/>
第二個字串項目。

### <a name="return-value"></a>傳回值

如果項目相等，false 否則，就會傳回 true。

##  <a name="compareelementsordered"></a>  CStringElementTraits::CompareElementsOrdered

呼叫此靜態函式來比較兩個字串元素。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串項目。

*str2*<br/>
第二個字串項目。

### <a name="return-value"></a>傳回值

若字串相同的零，< 0 如果*str1*是小於*str2*，或 > 0 如果*str1*大於*str2*。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用來執行比較。

##  <a name="copyelements"></a>  CStringElementTraits::CopyElements

呼叫此靜態函式來複製`CString`集合類別物件中儲存的項目。

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
將接收複製的資料的第一個元素的指標。

*pSrc*<br/>
若要複製的第一個元素的指標。

*nElements*<br/>
要複製的項目數目。

### <a name="remarks"></a>備註

不應該重疊的來源和目的地的項目。

##  <a name="hash"></a>  CStringElementTraits::Hash

呼叫此靜態函式來計算雜湊值，指定的字串項目。

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>參數

*str*<br/>
字串項目中。

### <a name="return-value"></a>傳回值

傳回使用字串的內容計算的雜湊值。

##  <a name="inargtype"></a>  CStringElementTraits::INARGTYPE

要用於將項目加入至集合的類別物件的資料類型。

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraits::OUTARGTYPE

要用來擷取元素的集合類別物件的資料類型。

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CStringElementTraits::RelocateElements

呼叫此靜態函式來重新放置`CString`集合類別物件中儲存的項目。

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
將會收到重新定位的資料的第一個元素的指標。

*pSrc*<br/>
重新定位之第一個元素的指標。

*nElements*<br/>
若要重新配置的元素數目。

### <a name="remarks"></a>備註

此靜態函式會呼叫[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，即足以應付大部分的資料類型。 如果要移動的物件包含其本身的成員的指標，此靜態函式必須覆寫。

## <a name="see-also"></a>另請參閱

[CElementTraitsBase 類別](../../atl/reference/celementtraitsbase-class.md)<br/>
[CStringElementTraitsI 類別](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
