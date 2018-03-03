---
title: "InspectableClass 巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ac1f84c76bb61d24ee25e8ca431e13620f6f85a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="inspectableclass-macro"></a>InspectableClass 巨集
設定執行階段類別名稱和信任層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
#### <a name="parameters"></a>參數  
 `runtimeClassName`  
 執行階段類別的完整文字的名稱。  
  
 `trustLevel`  
 其中一個[TrustLevel](http://msdn.microsoft.com/library/br224625.aspx)列舉值。  
  
## <a name="remarks"></a>備註  
 `InspectableClass`巨集只能搭配 Windows 執行階段類型。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)