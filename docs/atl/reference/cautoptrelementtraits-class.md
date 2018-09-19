---
title: CAutoPtrElementTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f406415afab907b7b00d75e52dce1fcac7166fd5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021079"
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits 類別

建立智慧型指標的集合時，這個類別會提供方法、 靜態的函式和實用的 typedef。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

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
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|

## <a name="remarks"></a>備註

這個類別會提供方法、 靜態的函式和 typedef，來協助建立包含智慧型指標的集合類別物件。 類別[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)並[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)衍生自`CAutoPtrElementTraits`。 如果建置智慧型指標的集合，需要新的向量和 delete 運算子，請使用[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)改。

## <a name="inheritance-hierarchy"></a>繼承階層

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="inargtype"></a>  CAutoPtrElementTraits::INARGTYPE

要用於將項目加入至集合的類別物件的資料類型。

```
typedef CAutoPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoPtrElementTraits::OUTARGTYPE

要用來擷取元素的集合類別物件的資料類型。

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
