---
title: "MutexTraits 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs: C++
helpviewer_keywords: MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eebe8ffefedbc28be1f16a0d02a195d4af4ac0c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="mutextraits-structure"></a>MutexTraits 結構
定義的一般特性[Mutex](../windows/mutex-class1.md)類別。  
  
## <a name="syntax"></a>語法  
  
```  
struct MutexTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[MutexTraits::Unlock 方法](../windows/mutextraits-unlock-method.md)|版本的共用資源的獨佔控制。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空間](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)