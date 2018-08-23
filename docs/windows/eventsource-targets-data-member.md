---
title: 'Eventsource:: Targets_ 資料成員 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targets_
dev_langs:
- C++
helpviewer_keywords:
- targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fcdcb759c90009410f76a4b10039a0d976ca0cc4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605111"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ 資料成員

一或多個事件處理常式的陣列。

## <a name="syntax"></a>語法

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

## <a name="remarks"></a>備註

當事件，表示由目前**EventSource**物件發生時，會呼叫事件處理常式。

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱
[EventSource 類別](../windows/eventsource-class.md)