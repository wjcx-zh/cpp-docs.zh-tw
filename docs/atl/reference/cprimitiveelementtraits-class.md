---
title: CPrimitiveElementTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa5f96b8937168126509025735d20fab7b35c2b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019195"
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits 類別

這個類別會提供預設方法，集合類別的函式是由基本資料類型所組成。

## <a name="syntax"></a>語法

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
集合類別物件中儲存的資料型別。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|

## <a name="remarks"></a>備註

這個類別會提供預設的靜態函式和移動、 複製、 比較和雜湊儲存在集合類別物件的基本資料型別項目所用的方法。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="inargtype"></a>  CPrimitiveElementTraits::INARGTYPE

要用於將項目加入至集合的類別物件的資料類型。

```
typedef T INARGTYPE;
```

##  <a name="outargtype"></a>  CPrimitiveElementTraits::OUTARGTYPE

要用來擷取元素的集合類別物件的資料類型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
