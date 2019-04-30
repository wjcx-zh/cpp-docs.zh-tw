---
title: scheduler_interface 結構
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 99a3ea8b6ad1f23b4f3d54b7f2f406a3d115b374
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392436"
---
# <a name="schedulerinterface-structure"></a>scheduler_interface 結構

排程器介面

## <a name="syntax"></a>語法

```
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[scheduler_interface::schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>繼承階層

`scheduler_interface`

## <a name="requirements"></a>需求

**標頭：** pplinterface.h

**命名空間：** concurrency

##  <a name="schedule"></a>  scheduler_interface:: schedule 方法

```
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
