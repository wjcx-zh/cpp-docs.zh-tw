---
title: InvokeModeOptions 結構 |Microsoft 文件
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
- event/Microsoft::WRL::InvokeMode
dev_langs:
- C++
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b27789f582b383530a675da83456a100780760b4
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions 結構

指定要委派佇列中的所有事件的都引發還是停止引發之後會引發錯誤。 允許的值中指定`InvokeMode`列舉。

## <a name="syntax"></a>語法

```
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

 **標頭：** event.h

 **命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)
[Microsoft::WRL::AgileEventSource 類別](../windows/agileeventsource-class.md)