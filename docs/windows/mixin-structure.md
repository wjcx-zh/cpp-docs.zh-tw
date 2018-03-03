---
title: "MixIn 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 883e952dde579cce3f5a65ba4a453f98ddbb4740
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mixin-structure"></a>MixIn 結構
確保執行階段類別衍生自 Windows 執行階段介面 (若有的話)，然後才是傳統 COM 介面。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### <a name="parameters"></a>參數  
 `Derived`  
 型別衍生自[實作](../windows/implements-structure.md)結構。  
  
 `MixInType`  
 基底類型。  
  
 `hasImplements`  
 `true`如果`MixInType`是衍生自目前實作的基底類型。`false`否則。  
  
## <a name="remarks"></a>備註  
 如果類別衍生自 Windows 執行階段和 COM 的類別介面，在類別宣告清單必須先列出的任何 Windows 執行階段介面，然後任何傳統 COM 介面。 MixIn 可確保指定的介面時，會以正確的順序。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `MixIn`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)