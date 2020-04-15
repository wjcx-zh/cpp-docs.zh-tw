---
title: CAutoPtr 元素類別
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: ac29116dc9beedf587c42cc0e52f8c9dbaf3d782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318881"
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtr 元素類別

此類提供創建智慧指標集合時有用的方法、靜態函數和 typedef。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>參數

*T*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CAutoPtr元素::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|
|[CAutoPtr元素::OUTARGTYPE](#outargtype)|用於從集合類物件檢索元素的數據類型。|

## <a name="remarks"></a>備註

此類提供用於幫助創建包含智慧指標的集合類物件的方法、靜態函數和 typedef。 類別[CAutoPtrarray](../../atl/reference/cautoptrarray-class.md)與[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)的金生 。`CAutoPtrElementTraits` 如果構建需要向量新運算元和刪除運算符的智慧指標集合,請使用[CAutoVectorPtrElementTraits。](../../atl/reference/cautovectorptrelementtraits-class.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[C 預設比較特徵](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素庫](../../atl/reference/celementtraitsbase-class.md)

[CDefault 元素](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoPtr元素::INARGTYPE

用於向集合類物件添加元素的數據類型。

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoPtr元素::OUTARGTYPE

用於從集合類物件檢索元素的數據類型。

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementtraits 類別](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
