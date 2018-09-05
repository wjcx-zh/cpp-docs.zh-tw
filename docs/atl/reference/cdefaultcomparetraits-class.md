---
title: CDefaultCompareTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4983984c8bf1cad2996818625091b60cdb732a9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758553"
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits 類別

這個類別會提供預設項目比較函式。

## <a name="syntax"></a>語法

```
template<typename T>  
class CDefaultCompareTraits
```

#### <a name="parameters"></a>參數

*T*  
若要在集合中儲存的資料型別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|（靜態）呼叫此函式來比較兩個項目相等。|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|（靜態）呼叫此函式可判斷的更高和較低的項目。|

## <a name="remarks"></a>備註

這個類別包含兩個靜態函式來比較集合類別物件中儲存的項目。 這個類別會利用[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements

呼叫此函式來比較兩個項目相等。

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>參數

*element1*  
第一個元素。

*element2*  
第二個項目中。

### <a name="return-value"></a>傳回值

如果項目相等，false 否則，就會傳回 true。

### <a name="remarks"></a>備註

此函式的預設實作是等號 (**==**) 運算子。 針對簡單的資料類型以外的物件，此函式可能需要覆寫。

##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered

呼叫此函式可判斷的更高和較低的項目。

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>參數

*element1*  
第一個元素。

*element2*  
第二個項目中。

### <a name="return-value"></a>傳回值

傳回整數，根據下表：

|條件|傳回值|
|---------------|------------------|
|*element1* < *element2*|<0|
|*element1* == *element2*|0|
|*element1* > *element2*|>0|

### <a name="remarks"></a>備註

此函式的預設實作會使用**==**， **\<**，以及**>** 運算子。 針對簡單的資料類型以外的物件，此函式可能需要覆寫。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
