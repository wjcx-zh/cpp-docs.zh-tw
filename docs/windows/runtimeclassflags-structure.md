---
title: "RuntimeClassFlags 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClassFlags
dev_langs: C++
helpviewer_keywords: RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c06443bebdd808ed8e37208a9db2636ce97f775d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 結構
包含的執行個體的型別[RuntimeClass](../windows/runtimeclass-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
#### <a name="parameters"></a>參數  
 `flags`  
 A [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)值。  
  
## <a name="members"></a>成員  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[RuntimeClassFlags::value 常數](../windows/runtimeclassflags-value-constant.md)|包含[RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)值。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `RuntimeClassFlags`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)