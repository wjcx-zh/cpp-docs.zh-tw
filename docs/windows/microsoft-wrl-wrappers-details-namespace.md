---
title: Microsoft::WRL::Wrappers::Details 命名空間 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
dev_langs:
- C++
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f74f8fe3e5b637869af7b03bb2eaf5e13df9550
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020158"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details 命名空間
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
namespace Microsoft::WRL::Wrappers::Details;  
```  
  
## <a name="members"></a>成員  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT 類別](../windows/synclockt-class.md)|代表一種類型，可以採取獨佔或共用資源的擁有權。|  
|[SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)|代表一種類型，可以採取獨佔或共用資源的擁有權。|  
  
### <a name="methods"></a>方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CompareStringOrdinal 方法](../windows/comparestringordinal-method.md)|比較兩個指定`HSTRING`物件，並傳回一個整數，表示兩者在排序次序中的相對位置。|  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)