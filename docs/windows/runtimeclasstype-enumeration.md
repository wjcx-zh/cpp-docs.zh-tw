---
title: RuntimeClassType 列舉 |Microsoft Docs
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
ms.openlocfilehash: 1b54813a41a8857e4533f21d1eb0adaf8dcecd25
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010817"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType 列舉
指定的型別[RuntimeClass](../windows/runtimeclass-class.md)支援的執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum RuntimeClassType;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`ClassicCom`|傳統的 COM 執行階段類別。|  
|`Delegate`|相當於 `ClassicCom`。|  
|`InhibitFtmBase`|停用`FtmBase`支援，同時`__WRL_CONFIGURATION_LEGACY__`未定義。|  
|`InhibitWeakReference`|停用弱式參考支援。|  
|`WinRt`|Windows 執行階段類別。|  
|`WinRtClassicComMix`|結合 `WinRt` 和 `ClassicCom`。|  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)