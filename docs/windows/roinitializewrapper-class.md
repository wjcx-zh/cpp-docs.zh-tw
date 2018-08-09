---
title: RoInitializeWrapper 類別 |Microsoft Docs
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 41eb5e79ca1471fb8c12ffca420a134115fbfcc1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014035"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 類別
初始化 Windows 執行階段。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>備註  
 **RoInitializeWrapper**是為了方便起見，會初始化 Windows 執行階段，並會傳回 HRESULT，指出作業是否成功。 因為類別的解構函式會呼叫`::Windows::Foundation::Uninitialize`，執行個體**RoInitializeWrapper**必須在全域或最上層範圍中宣告。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper 建構函式](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|初始化的新執行個體**RoInitializeWrapper**類別。|  
|[RoInitializeWrapper::~RoInitializeWrapper 解構函式](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|終結的目前執行個體**RoInitializeWrapper**類別。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() 運算子](../windows/roinitializewrapper-hresult-parens-operator.md)|擷取所產生的 HRESULT **RoInitializeWrapper**建構函式。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)