---
title: ModuleType 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d36355c9f64f9f5c827ef8c4d5b3cb6a77d17b65
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876832"
---
# <a name="moduletype-enumeration"></a>ModuleType 列舉
指定模組是否應支援同處理序伺服程式或跨處理序伺服程式。  
  
## <a name="syntax"></a>語法  
  
```  
enum ModuleType;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`InProc`|同處理序伺服器。|  
|`OutOfProc`|跨處理序伺服器。|  
|`DisableCaching`|停用在模組上的快取機制。|  
|`InProcDisableCaching`|組合`InProc`和`DisableCaching`。|  
|`OutOfProcDisableCaching`|組合`OutOfProc`和`DisableCaching`。|  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)