---
title: 號誌類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1219c2118f9cde18fe1909a2edd02d58a4be2341
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="semaphore-class"></a>Semaphore 類別
表示控制項可支援有限的數目的使用者共用的資源的同步處理物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`SyncLock`|支援同步鎖定的類型同義。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Semaphore::Semaphore 建構函式](../windows/semaphore-semaphore-constructor.md)|初始化 Semaphore 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|會呼叫其簽章包含指定的引數數目的事件處理常式。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[Semaphore::Lock 方法](../windows/semaphore-lock-method.md)|等待目前的物件或指定的控制代碼相關聯的物件處於信號狀態，或超過指定逾時間隔。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[Semaphore::operator= 運算子](../windows/semaphore-operator-assign-operator.md)|將指定的控制代碼從號誌物件移至目前的號誌物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Semaphore`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)