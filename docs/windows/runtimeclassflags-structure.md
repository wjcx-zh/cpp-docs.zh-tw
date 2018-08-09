---
title: RuntimeClassFlags 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 823244b54513e4f6b2901bc29984604f65eb9a11
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018032"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 結構
包含的執行個體的型別[RuntimeClass](../windows/runtimeclass-class.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
### <a name="parameters"></a>參數  
 *flags*  
 A [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)值。  
  
## <a name="members"></a>成員  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[RuntimeClassFlags::value 常數](../windows/runtimeclassflags-value-constant.md)|包含[RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)值。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `RuntimeClassFlags`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)