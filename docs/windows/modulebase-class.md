---
title: ModuleBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b298bcab4c2b3547f2b285fe21d4967f4696fb9d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605054"
---
# <a name="modulebase-class"></a>ModuleBase 類別
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>備註  
 表示基底類別[模組](../windows/module-class.md)類別。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ModuleBase::ModuleBase 建構函式](../windows/modulebase-modulebase-constructor.md)|初始化 `Module` 類別的執行個體。|  
|[ModuleBase::~ModuleBase 解構函式](../windows/modulebase-tilde-modulebase-destructor.md)|取消初始化目前的執行個體`Module`類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount 方法](../windows/modulebase-decrementobjectcount-method.md)|實作時，遞減模組所追蹤的物件數目。|  
|[ModuleBase::IncrementObjectCount 方法](../windows/modulebase-incrementobjectcount-method.md)|實作時，遞增模組所追蹤的物件數目。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ModuleBase`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)