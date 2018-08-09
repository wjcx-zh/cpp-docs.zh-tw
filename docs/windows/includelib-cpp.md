---
title: includelib （c + +） |Microsoft Docs
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
ms.openlocfilehash: 3d6f6a4dc4f23460b3661da4ed3775708cac9b6d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016173"
---
# <a name="includelib-c"></a>includelib (C++)
會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ includelib(  
   name.idl  
) ];  
```  
  
### <a name="parameters"></a>參數  
 *name.idl*  
 您想要產生的.idl 檔案的一部分的.idl 檔案的名稱。  
  
## <a name="remarks"></a>備註  
 **Includelib** c + + 屬性會造成的.idl 或.h 檔案之後，在產生的.idl 檔案中，包含`importlib`陳述式。  
  
## <a name="example"></a>範例  
 下列程式碼所示的.cpp 檔案：  
  
```cpp  
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