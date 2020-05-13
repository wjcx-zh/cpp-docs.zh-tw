---
title: 元素基礎類
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 5a29e8778cf2f3400df25b55574950a005bad995
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327011"
---
# <a name="celementtraitsbase-class"></a>元素基礎類

此類為集合類提供預設複製和移動方法。

## <a name="syntax"></a>語法

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合中的數據類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[元素特徵庫::INARGTYPE](#inargtype)|用於向集合類物件添加元素的數據類型。|
|[元素特徵庫::OUTARGTYPE](#outargtype)|用於從集合類物件檢索元素的數據類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[元素庫基礎::複製元素](#copyelements)|呼叫此方法以複製儲存在集合類物件中的元素。|
|[元素庫基礎::重新置放元素](#relocateelements)|呼叫此方法以重新定位儲存在集合類物件中的元素。|

## <a name="remarks"></a>備註

此基類定義用於複製和重新定位集合類中的元素的方法。 它被類[CDefault ElementTraits、CStringRef Element Traits](../../atl/reference/cstringrefelementtraits-class.md)和[CString Element TraitsI](../../atl/reference/cstringelementtraitsi-class.md)使用。 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a>元素庫基礎::複製元素

呼叫此方法以複製儲存在集合類物件中的元素。

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
指向將接收複製數據的第一個元素的指標。

*pSrc*<br/>
指向要複製的第一個元素的指標。

*n 元素*<br/>
要複製的項目數目。

### <a name="remarks"></a>備註

源元素和目標元素不應重疊。

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a>元素特徵庫::INARGTYPE

用於向集合中添加元素的數據類型。

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a>元素特徵庫::OUTARGTYPE

用於從集合檢索元素的數據類型。

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a>元素庫基礎::重新置放元素

呼叫此方法以重新定位儲存在集合類物件中的元素。

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
指向將接收重新置放數據的第一個元素的指標。

*pSrc*<br/>
指向要重新置放的第一個元素的指標。

*n 元素*<br/>
要重新置放的元素數。

### <a name="remarks"></a>備註

此方法調用[memmove](../../c-runtime-library/reference/memmove-wmemmove.md),對於大多數數據類型來說,這就足夠了。 如果要移動的物件包含指向其自己的成員的指標,則需要重寫此方法。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
