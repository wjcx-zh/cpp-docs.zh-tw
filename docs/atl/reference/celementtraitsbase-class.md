---
title: CElementTraitsBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1173633cd720ed6ee0e4aacdf75a8b305fdbfe4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043361"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 類別

這個類別會提供預設的複製，並移動集合類別的方法。

## <a name="syntax"></a>語法

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>參數

*T*<br/>
若要在集合中儲存的資料型別。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|呼叫這個方法來複製集合類別物件中儲存的項目。|
|[CElementTraitsBase::RelocateElements](#relocateelements)|呼叫這個方法來重新放置集合類別物件中儲存的項目。|

## <a name="remarks"></a>備註

這個基底類別會定義用於複製和重新定位項目中的集合類別的方法。 它會利用類別[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)， [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)，並[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements

呼叫這個方法來複製集合類別物件中儲存的項目。

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
將接收複製的資料的第一個元素的指標。

*pSrc*<br/>
若要複製的第一個元素的指標。

*nElements*<br/>
要複製的項目數目。

### <a name="remarks"></a>備註

不應該重疊的來源和目的地的項目。

##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE

要用於將項目加入至集合的資料類型。

```
typedef const T& INARGTYPE;
```

##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE

要用來從集合擷取項目資料型別。

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements

呼叫這個方法來重新放置集合類別物件中儲存的項目。

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>參數

*pDest*<br/>
將會收到重新定位的資料的第一個元素的指標。

*pSrc*<br/>
重新定位之第一個元素的指標。

*nElements*<br/>
若要重新配置的元素數目。

### <a name="remarks"></a>備註

這個方法會呼叫[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，即足以應付大部分的資料類型。 如果要移動的物件包含其本身的成員的指標，這個方法必須覆寫。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
