---
title: CloakedIid 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
dev_langs:
- C++
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b766858d0f558b4fdff3a703c612ec07c038abf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641916"
---
# <a name="cloakediid-structure"></a>CloakedIid 結構
若要指出`RuntimeClass`，`Implements`和`ChainInterfaces`範本指定的介面不是在 IID 清單中存取。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename T>  
struct CloakedIid : T;  
```  
  
#### <a name="parameters"></a>參數  
 *T*  
 介面隱藏的 （「 隱匿 」）。  
  
## <a name="remarks"></a>備註  
 以下是如何的範例**CloakedIid**使用： `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `T`  
  
 `CloakedIid`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)