---
title: C原始元素類別
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 6b45d93420d1832091cc451a3e6eb309f61d07a3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331444"
---
# <a name="cprimitiveelementtraits-class"></a>C原始元素類別

此類為由基元數據類型組成的集合類提供預設方法和函數。

## <a name="syntax"></a>語法

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合類對象中的數據類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[原始元素::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|
|[原始元素::OUTARGTYPE](#outargtype)|用於從集合類物件檢索元素的數據類型。|

## <a name="remarks"></a>備註

此類提供用於移動、複製、比較和哈希存儲在集合類物件中的原始數據類型元素的默認靜態函數和方法。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[C 預設比較特徵](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素庫](../../atl/reference/celementtraitsbase-class.md)

[CDefault 元素](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a>原始元素::INARGTYPE

用於向集合類物件添加元素的數據類型。

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a>原始元素::OUTARGTYPE

用於從集合類物件檢索元素的數據類型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementtraits 類別](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
