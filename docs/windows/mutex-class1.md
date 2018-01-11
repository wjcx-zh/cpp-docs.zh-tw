---
title: "Mutex Class1 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs: C++
helpviewer_keywords: Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0e849d1fee7eca67f3b5765d31b54e0660eaa25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mutex-class1"></a>Mutex Class1
表示以獨佔方式控制共用的資源的同步處理物件。  
  
## <a name="syntax"></a>語法  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|**SyncLock**|支援同步鎖定的類型同義。|  
  
### <a name="public-constructor"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Mutex::Mutex 建構函式](../windows/mutex-mutex-constructor.md)|初始化 Mutex 類別的新執行個體。|  
  
### <a name="public-members"></a>Public 成員  
  
|名稱|描述|  
|----------|-----------------|  
|[Mutex::Lock 方法](../windows/mutex-lock-method.md)|等待目前的物件或指定的控制代碼相關聯的 Mutex 物件釋放 mutex，或超過指定的逾時間隔。|  
  
### <a name="public-operator"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[Mutex::operator= 運算子](../windows/mutex-operator-assign-operator.md)|指派 （移動） 指定的 Mutex 物件傳遞給目前的 Mutex 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Mutex`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)