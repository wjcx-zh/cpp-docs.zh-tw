---
title: 包含 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2c88dd610c1a0b8a8fee4e23da1b5ad844e989c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878420"
---
# <a name="include-c"></a>include (C++)
指定要包含在產生的.idl 檔中的一個或多個標頭檔。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ include(  
   header_file  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 *header_file*  
 您想要包含在產生的.idl 檔案中的檔案名稱。  
  
## <a name="remarks"></a>備註  
 **包含**c + + 屬性會造成`#include`放下方的陳述式`import "docobj.idl"`產生的.idl 檔案中的陳述式。  
  
 **包含**c + + 屬性具有相同的功能[包含](http://msdn.microsoft.com/library/windows/desktop/aa367052)MIDL 屬性。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用**包含**。 例如，檔案 include.h 僅包含 #include 陳述式。  
  
```  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
 [匯入](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [includelib](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   
