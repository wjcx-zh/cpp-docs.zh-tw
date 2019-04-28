---
title: CComAutoDeleteCriticalSection 類別
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: d479adce489e0329be3a93b55a70aa3e58a0e038
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246653"
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 類別

這個類別提供方法來取得和釋放重要區段物件的擁有權。

## <a name="syntax"></a>語法

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>備註

`CComAutoDeleteCriticalSection` 衍生自類別[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)。 不過，`CComAutoDeleteCriticalSection`會覆寫[詞彙](ccomsafedeletecriticalsection-class.md#term)方法來**私用**強制發生只有當此類別的執行個體超出範圍或明確刪除從內部記憶體清除的存取記憶體。

這個類別會介紹沒有額外的方法，透過其基底類別。 請參閱[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)並[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)如需有關重要區段協助程式類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>需求

**標頭：** atlcore.h

## <a name="see-also"></a>另請參閱

[CComSafeDeleteCriticalSection 類別](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
