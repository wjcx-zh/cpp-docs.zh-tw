---
title: "GetModuleBase 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19f575705b1f8680a68e9100f20be66ca22ec87a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="getmodulebase-function"></a>GetModuleBase 函式
擷取[ModuleBase](../windows/modulebase-class.md)允許遞增和遞減參考計數的指標[RuntimeClass](../windows/runtimeclass-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## <a name="return-value"></a>傳回值  
 指標`ModuleBase`物件。  
  
## <a name="remarks"></a>備註  
 此函式在內部用來遞增和遞減物件參考計數。  
  
 您可以使用此函式來控制參考計數，藉由呼叫[modulebase:: Incrementobjectcount](../windows/modulebase-incrementobjectcount-method.md)和[modulebase:: Decrementobjectcount](../windows/modulebase-decrementobjectcount-method.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)