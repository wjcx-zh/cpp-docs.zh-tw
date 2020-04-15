---
title: scheduler_interface 結構
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: da2ebc2f9c2878baefcfa792bac08f420dbbb281
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358781"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface 結構

排程器介面

## <a name="syntax"></a>語法

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[scheduler_interface:計劃](#schedule)||

## <a name="inheritance-hierarchy"></a>繼承階層架構

`scheduler_interface`

## <a name="requirements"></a>需求

**標題:** pplinterface.h

**命名空間:** 併發

## <a name="scheduler_interfaceschedule-method"></a><a name="schedule"></a>scheduler_interface::計劃方法

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
