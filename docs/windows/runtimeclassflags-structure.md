---
title: RuntimeClassFlags 結構 |Microsoft 文件
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
ms.openlocfilehash: 05166be14680b14d704095f5f1c9375bd97da7d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892022"
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