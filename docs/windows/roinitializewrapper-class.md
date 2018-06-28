---
title: RoInitializeWrapper 類別 |Microsoft 文件
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
ms.openlocfilehash: cac71857e6b472f11d1c9eaba48d181ea78fb456
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705588"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 類別
初始化 Windows 執行階段。  
  
## <a name="syntax"></a>語法  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>備註  
 RoInitializeWrapper 為方便起見，初始化 Windows 執行階段，並會傳回 HRESULT，指出作業是否成功。 因為類別的解構函式呼叫`::Windows::Foundation::Uninitialize`的執行個體`RoInitializeWrapper`必須在全域或最上層範圍中宣告。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper 建構函式](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|初始化 RoInitializeWrapper 類別的新執行個體。|  
|[RoInitializeWrapper::~RoInitializeWrapper 解構函式](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|終結 RoInitializeWrapper 類別的目前執行個體。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() 運算子](../windows/roinitializewrapper-hresult-parens-operator.md)|擷取 RoInitializeWrapper 建構函式所產生的 HRESULT。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)