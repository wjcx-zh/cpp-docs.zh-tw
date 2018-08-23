---
title: 'Eventsource:: Targetspointerlock_ 資料成員 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targetsPointerLock_
dev_langs:
- C++
helpviewer_keywords:
- targetsPointerLock_ data member
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45c85502b7d0768f5fa3e275393a4071fd8649e4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598861"
---
# <a name="eventsourcetargetspointerlock-data-member"></a>EventSource::targetsPointerLock_ 資料成員

同步處理時存取內部資料成員，即使事件處理常式這**EventSource**正在加入、 移除或叫用。

## <a name="syntax"></a>語法

```cpp
Wrappers::SRWLock targetsPointerLock_;
```

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱
[EventSource 類別](../windows/eventsource-class.md)