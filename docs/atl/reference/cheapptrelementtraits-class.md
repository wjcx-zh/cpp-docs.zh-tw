---
title: CHeapPtrElementTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d28136c9fa131d525878fe0551f5ba2421576951
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760080"
---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits 類別

建立集合的堆積指標時，這個類別會提供方法、 靜態的函式和實用的 typedef。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<typename T, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrElementTraits : 
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>參數

*T*  
要儲存在集合類別的物件類型。

*配置器*  
要使用的記憶體配置類別。 預設值是[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|

## <a name="remarks"></a>備註

這個類別會提供方法、 靜態的函式和 typedef，來協助建立包含堆積指標集合類別的物件。 此類別`CHeapPtrList`衍生自`CHeapPtrElementTraits`。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="inargtype"></a>  CHeapPtrElementTraits::INARGTYPE

要用於將項目加入至集合的類別物件的資料類型。

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

##  <a name="outargtype"></a>  CHeapPtrElementTraits::OUTARGTYPE

要用來擷取元素的集合類別物件的資料類型。

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
[CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)   
[類別概觀](../../atl/atl-class-overview.md)
