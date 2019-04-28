---
title: CDefaultElementTraits 類別
ms.date: 11/04/2016
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
ms.openlocfilehash: 0ee076af5fc4a1c2145162ac510b3a4460e251e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245916"
---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits 類別

這個類別會提供預設方法和函式的集合類別。

## <a name="syntax"></a>語法

```
template <typename T>
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```

#### <a name="parameters"></a>參數

*T*<br/>
若要在集合中儲存的資料型別。

## <a name="remarks"></a>備註

這個類別會提供預設的靜態函式和方法，移動、 複製、 比較及集合類別物件中儲存的雜湊項目。 此類別衍生而來，它的函式和方法，從[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)， [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)，並[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)，並會利用[CElementTraits](../../atl/reference/celementtraits-class.md)， [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)，以及[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
