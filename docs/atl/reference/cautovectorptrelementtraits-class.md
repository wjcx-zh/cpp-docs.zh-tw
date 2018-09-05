---
title: CAutoVectorPtrElementTraits 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd39f56d69aef836714d70b50f6e2c882cad9448
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754822"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits 類別

這個類別提供方法、 靜態的函式和建立使用新的向量的智慧型指標的集合和 delete 運算子時很有用的 typedef。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <typename T>  
class CAutoVectorPtrElementTraits : 
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>參數

`T`  
指標類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|要用於將項目加入至集合的類別物件的資料類型。|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|要用來擷取元素的集合類別物件的資料類型。|

## <a name="remarks"></a>備註

這個類別會提供方法、 靜態的函式和 typedef，來協助建立包含智慧型指標的集合類別物件。 不同於[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)，這個類別會使用向量 new 和 delete 運算子。

## <a name="inheritance-hierarchy"></a>繼承階層

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="inargtype"></a>  CAutoVectorPtrElementTraits::INARGTYPE

要用於將項目加入至集合的類別物件的資料類型。

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoVectorPtrElementTraits::OUTARGTYPE

要用來擷取元素的集合類別物件的資料類型。

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)   
[CAutoVectorPtr 類別](../../atl/reference/cautovectorptr-class.md)   
[類別概觀](../../atl/atl-class-overview.md)
