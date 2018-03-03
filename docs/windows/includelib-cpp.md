---
title: "includelib （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df6c38889db24cc1b4f28ce0bfe4cf96eb6b03a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="includelib-c"></a>includelib (C++)
會導致的.idl 或.h 檔案包含在產生的.idl 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ includelib(  
   name.idl  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 *name.idl*  
 您想要包含在產生的.idl 檔的.idl 檔案名稱。  
  
## <a name="remarks"></a>備註  
 `includelib` C + + 屬性會造成的.idl 或.h 檔案包含在產生的.idl 檔案之後,`importlib`陳述式。  
  
## <a name="example"></a>範例  
 下列程式碼所示的.cpp 檔：  
  
```  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|[是]|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
 [匯入](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [包含](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
