---
title: GetModuleBase 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 403330097f1428ee0d7650f5931aef1621f61b11
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612597"
---
# <a name="getmodulebase-function"></a>GetModuleBase 函式
擷取[ModuleBase](../windows/modulebase-class.md)指標，這是用來遞增和遞減參考計數[RuntimeClass](../windows/runtimeclass-class.md)物件。
  
## <a name="syntax"></a>語法
  
```cpp
inline Details::ModuleBase* GetModuleBase() throw()  
```
  
## <a name="return-value"></a>傳回值
 `ModuleBase` 物件的指標。
  
## <a name="remarks"></a>備註
 此函式在內部用來遞增和遞減物件的參考計數。
  
 您可以使用此函式，來控制參考計數，藉由呼叫[modulebase:: Incrementobjectcount](../windows/modulebase-incrementobjectcount-method.md)並[modulebase:: Decrementobjectcount](../windows/modulebase-decrementobjectcount-method.md)。
  
## <a name="requirements"></a>需求
 **標頭：** implements.h
  
 **命名空間：** Microsoft::WRL
  
## <a name="see-also"></a>另請參閱
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)