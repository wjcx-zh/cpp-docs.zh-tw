---
title: CSimpleArrayEqualHelper 類別
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: e677a5d12918649597db9614b965118f8d6b7da6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656219"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper 類別

這個類別是 helper [CSimpleArray](../../atl/reference/csimplearray-class.md)類別。

## <a name="syntax"></a>語法

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>參數

*T*<br/>
在衍生的類別中。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|（靜態）測試兩個`CSimpleArray`物件項目是否相等。|

## <a name="remarks"></a>備註

此特性類別是補充`CSimpleArray`類別。 它會提供方法來比較兩個項目儲存在`CSimpleArray`物件。 根據預設，項目會使用 「 比較**operator=()**，但如果陣列包含沒有自己的等號比較運算子的複雜資料型別，您必須覆寫這個類別。

## <a name="requirements"></a>需求

**標頭：** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual

測試兩個`CSimpleArray`物件項目是否相等。

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>參數

*T1*<br/>
型別 t 的物件

*T2*<br/>
型別 t 的物件

### <a name="return-value"></a>傳回值

如果項目相等，false 否則，就會傳回 true。

## <a name="see-also"></a>另請參閱

[CSimpleArray 類別](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse 類別](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
