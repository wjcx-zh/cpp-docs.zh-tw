---
title: CDefaultHashTraits類
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 43932092621d44cfc8b07270df92e2765665f23f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327077"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits類

此類提供用於計算哈希值的靜態函數。

## <a name="syntax"></a>語法

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在集合中的數據類型。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDefaultHashTraits:哈希](#hash)|(靜態)調用此函數以計算給定元素的哈希值。|

## <a name="remarks"></a>備註

此類包含單個靜態函數,該函數返回給定元素的哈希值。 此類由[CDefault Element Traits 類](../../atl/reference/cdefaultelementtraits-class.md)使用。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits:哈希

調用此函數以計算給定元素的哈希值。

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>參數

*元素*<br/>
元素。

### <a name="return-value"></a>傳回值

返回哈希值。

### <a name="remarks"></a>備註

默認哈希演演演算法非常簡單:返回值是元素編號。 如果需要更複雜的演演演算法,則重寫此函數。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
