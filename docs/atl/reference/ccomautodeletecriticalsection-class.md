---
title: CComAutoDeleteCriticalSection 類別
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: f44dbff7d353cb09142ac742b526d3541e9b2265
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224327"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 類別

這個類別會提供方法來取得和釋放重要區段物件的擁有權。

## <a name="syntax"></a>語法

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>備註

`CComAutoDeleteCriticalSection`衍生自類別[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)。 不過， `CComAutoDeleteCriticalSection` 會覆寫要存取的[詞彙](ccomsafedeletecriticalsection-class.md#term)方法 **`private`** ，這只會在此類別的實例超出範圍或明確地從記憶體中刪除時，才會強制執行內部記憶體清理。

這個類別不會對其基類引進任何其他方法。 如需重要區段協助程式類別的詳細資訊，請參閱[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)和[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>需求

**標頭：** atlcore。h

## <a name="see-also"></a>另請參閱

[CComSafeDeleteCriticalSection 類別](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
