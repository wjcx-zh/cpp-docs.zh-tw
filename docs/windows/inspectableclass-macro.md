---
title: InspectableClass 巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a02e20f2b87afc312c24683417f808d636c2757f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608952"
---
# <a name="inspectableclass-macro"></a>InspectableClass 巨集
設定執行階段類別名稱和信任層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
### <a name="parameters"></a>參數  
 *runtimeClassName*  
 執行階段類別的完整文字名稱。  
  
 *trustLevel*  
 其中一個[TrustLevel](http://msdn.microsoft.com/library/br224625.aspx)列舉值。  
  
## <a name="remarks"></a>備註  
 **InspectableClass**巨集只能搭配 Windows 執行階段類型。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)