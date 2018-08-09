---
title: CancelTransitionPolicy 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs:
- C++
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd203ee0413b60bc7aa713e7923fd4d69bde665e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642954"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy 列舉
表示非同步作業方式嘗試轉換為終止狀態的完成或錯誤的用戶端要求已取消狀態行為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum CancelTransitionPolicy;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`RemainCanceled`|如果非同步作業目前正在用戶端要求已取消狀態，這表示它會保留於已取消的狀態，而不是轉換為已完成的終端機或錯誤狀態。|  
|`TransitionFromCanceled`|如果非同步作業目前正在用戶端要求已取消狀態，這表示應該轉換與已取消的狀態，以終止狀態的完成狀態或錯誤，會利用這個旗標的呼叫所決定。|  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)