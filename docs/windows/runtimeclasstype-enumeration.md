---
title: RuntimeClassType 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 43ab0a738af4c6bc92d42c0884827b574946d2ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892399"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType 列舉
指定的型別[RuntimeClass](../windows/runtimeclass-class.md)支援的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
enum RuntimeClassType;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`ClassicCom`|傳統的 COM 執行階段類別。|  
|`Delegate`|相當於**ClassicCom**。|  
|`InhibitFtmBase`|停用`FtmBase`時支援`__WRL_CONFIGURATION_LEGACY__`未定義。|  
|`InhibitWeakReference`|停用弱式參考支援。|  
|`WinRt`|Windows 執行階段類別。|  
|`WinRtClassicComMix`|結合 `WinRt` 和 `ClassicCom`。|  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)