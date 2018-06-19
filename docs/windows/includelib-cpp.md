---
title: includelib （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 252a5d953dd05edc494daf8c4a45322d5511f979
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878888"
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
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
 [匯入](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [包含](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
