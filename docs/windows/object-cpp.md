---
title: "物件 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5714d7c3bd029c7b1df636044ed1968f53600848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="object-c"></a>object (C++)
識別的自訂介面。  
  
## <a name="syntax"></a>語法  
  
```  
  
[object]  
  
```  
  
## <a name="remarks"></a>備註  
 當之前的介面定義，**物件**c + + 屬性會造成要放入.idl 檔案，做為自訂介面的介面。  
  
 使用物件標記任何介面必須繼承自**IUnknown**。 如果任何基底介面繼承自符合此條件**IUnknown**。 如果沒有基底介面繼承自**IUnknown**，編譯器會以標記的介面**物件**衍生自**IUnknown**。  
  
## <a name="example"></a>範例  
 請參閱[nonbrowsable](../windows/nonbrowsable.md)如需如何使用的範例**物件**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
 [雙重](../windows/dual.md)   
 [dispinterface](../windows/dispinterface.md)   
 [自訂](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
