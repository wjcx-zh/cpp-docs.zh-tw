---
title: "ModuleType 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd68d911a3734510bfb35db4b3ee0c4b8e46a4a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)