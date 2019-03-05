---
title: CSimpleMapEqualHelper Class
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: c614cbb11376c5ae338762c0feaa54c8f1bb3e27
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282769"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper Class

這個類別是 helper [CSimpleMap](../../atl/reference/csimplemap-class.md)類別。

## <a name="syntax"></a>語法

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>參數

*TKey*<br/>
索引鍵的項目。

*TVal*<br/>
Value 元素中。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|（靜態）測試兩個索引鍵相等。|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|（靜態）測試兩個值相等。|

## <a name="remarks"></a>備註

此特性類別是補充`CSimpleMap`類別。 它提供方法來比較兩個`CSimpleMap`物件是否相等的項目 （具體而言，索引鍵和值元件）。 根據預設，索引鍵和值的比較**operator**，但如果對應包含沒有自己的等號比較運算子的複雜資料型別，這個類別可以覆寫以提供額外的必要的功能。

## <a name="requirements"></a>需求

**標頭：** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

測試兩個索引鍵相等。

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>參數

*k1*<br/>
第一個索引鍵。

*k2*<br/>
第二個索引鍵。

### <a name="return-value"></a>傳回值

如果索引鍵相等，false 否則，就會傳回 true。

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

測試兩個值相等。

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>參數

*v1*<br/>
第一個值。

*v2*<br/>
第二個值。

### <a name="return-value"></a>傳回值

如果值相等，false 否則，就會傳回 true。

## <a name="see-also"></a>另請參閱

[CSimpleMapEqualHelperFalse 類別](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
