---
title: CStringElementTraitsI 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29df4bd550a5de232b5ced0510e8dbfc68e59d42
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060750"
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI 類別

這個類別提供靜態的函式與儲存在集合類別物件的字串。 類似於[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但是執行不區分大小寫的比較。

## <a name="syntax"></a>語法

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
若要在集合中儲存的資料型別。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|呼叫此靜態函式來比較兩個字串項目相等，忽略大小寫的不同。|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|呼叫此靜態函式來比較兩個字串項目，並忽略大小寫的不同。|
|[CStringElementTraitsI::Hash](#hash)|呼叫此靜態函式來計算雜湊值，指定的字串項目。|

## <a name="remarks"></a>備註

這個類別提供靜態函式，來比較字串，以及如何建立雜湊值。 使用集合類別來儲存字串為基礎的資料時，則這些函式會很有用。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)字串物件時使用處理做為參考。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="compareelements"></a>  CStringElementTraitsI::CompareElements

呼叫此靜態函式來比較兩個字串項目相等，忽略大小寫的不同。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串項目。

*str2*<br/>
第二個字串項目。

### <a name="return-value"></a>傳回值

如果項目相等，false 否則，就會傳回 true。

### <a name="remarks"></a>備註

比較不區分大小寫。

##  <a name="compareelementsordered"></a>  CStringElementTraitsI::CompareElementsOrdered

呼叫此靜態函式來比較兩個字串項目，並忽略大小寫的不同。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個字串項目。

*str2*<br/>
第二個字串項目。

### <a name="return-value"></a>傳回值

若字串相同的零，< 0 如果*str1*是小於*str2*，或 > 0 如果*str1*大於*str2*。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用來執行比較。

### <a name="remarks"></a>備註

比較不區分大小寫。

##  <a name="hash"></a>  CStringElementTraitsI::Hash

呼叫此靜態函式來計算雜湊值，指定的字串項目。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>參數

*str*<br/>
字串項目中。

### <a name="return-value"></a>傳回值

傳回使用字串的內容計算的雜湊值。

##  <a name="inargtype"></a>  CStringElementTraitsI::INARGTYPE

要用於將項目加入至集合的類別物件的資料類型。

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraitsI::OUTARGTYPE

要用來擷取元素的集合類別物件的資料類型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CElementTraitsBase 類別](../../atl/reference/celementtraitsbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits 類別](../../atl/reference/cstringelementtraits-class.md)
