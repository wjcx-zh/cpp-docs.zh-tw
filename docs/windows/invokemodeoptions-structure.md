---
title: InvokeModeOptions 結構 |Microsoft 文件
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b1eb0e7f6cf49a7c6ac12a4810ae1622e263e2f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882833"
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions 結構

指定要委派佇列中的所有事件的都引發還是停止引發之後會引發錯誤。 允許的值中指定`InvokeMode`列舉。

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

**標頭：** event.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)
[Microsoft::WRL::AgileEventSource 類別](../windows/agileeventsource-class.md)