---
title: InvokeModeOptions 結構
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 9bca49479d97ee371f6728f90a9aa96da0387f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213833"
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions 結構

指定是否要在委派佇列中引發所有事件，或在發生錯誤後停止引發。 可在 `InvokeMode` 列舉中指定允許的值。

## <a name="syntax"></a>語法

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>需求

**Header：** 事件。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)<br/>
[Microsoft：： WRL：： AgileEventSource 類別](agileeventsource-class.md)
