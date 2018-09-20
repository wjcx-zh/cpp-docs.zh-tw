---
title: 'Eventtargetarray:: Addtail 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab0219c8893ff7ad35e29f9dd8b18be18caf8eb9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378120"
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>參數

*項目*<br/>
要附加的事件處理常式的指標。

## <a name="remarks"></a>備註

將指定的事件處理常式附加至事件處理常式內部陣列的結尾。

**AddTail()** 旨在只可用於在內部`EventSource`類別。

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[EventTargetArray 類別](../windows/eventtargetarray-class.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)