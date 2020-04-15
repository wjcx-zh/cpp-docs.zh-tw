---
title: CDefault 比較功能類別
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: 8262800ef613424c37c53931d97dd4b1b1a71321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327067"
---
# <a name="cdefaultcomparetraits-class"></a>CDefault 比較功能類別

此類提供預設元素比較函數。

## <a name="syntax"></a>語法

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合中的數據類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[預設比較特徵::比較元素](#compareelements)|(靜態)調用此函數以比較兩個元素以實現相等性。|
|[預設比較特徵:比較元素排序](#compareelementsordered)|(靜態)調用此函數以確定更大和更小的元素。|

## <a name="remarks"></a>備註

此類包含兩個靜態函數,用於比較存儲在集合類物件中的元素。 此類由[CDefault Element Traits 類](../../atl/reference/cdefaultelementtraits-class.md)使用。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a>預設比較特徵::比較元素

調用此函數以比較兩個元素以實現相等性。

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>參數

*元素1*<br/>
第一個元素。

*元素2*<br/>
第二個元素。

### <a name="return-value"></a>傳回值

如果元素相等,則返回 true,否則為 false。

### <a name="remarks"></a>備註

此函數的預設實現是相等**==**( ) 運算子。 對於簡單數據類型以外的物件,可能需要重寫此函數。

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a>預設比較特徵:比較元素排序

調用此函數以確定更大和更小的元素。

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>參數

*元素1*<br/>
第一個元素。

*元素2*<br/>
第二個元素。

### <a name="return-value"></a>傳回值

傳回基於下表的整數:

|條件|傳回值|
|---------------|------------------|
|*元素1* < *元素2*|<0|
|*元素1* == *元素2*|0|
|*元素1* > *元素2*|>0|

### <a name="remarks"></a>備註

此函數的預設實現使用**==**、**\<****>** 運算子。 對於簡單數據類型以外的物件,可能需要重寫此函數。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
