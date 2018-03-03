---
title: "library_block |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab7c4c8c65d23dc252fb3ce228313fb36aa7e032
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="libraryblock"></a>library_block
將放在 IDL 程式庫區塊內的建構。  
  
## <a name="syntax"></a>語法  
  
```  
  
[library_block]  
  
```  
  
## <a name="remarks"></a>備註  
 當您將程式庫區塊內的建構時，確定它將會傳遞至類型程式庫，不論是否參考。 根據預設，只有建構會修改由[coclass](../windows/coclass.md)， [dispinterface](../windows/dispinterface.md)，和[idl_module](../windows/idl-module.md)屬性會放在程式庫區塊。  
  
## <a name="example"></a>範例  
 下列程式碼，自訂介面位於程式庫區塊內。  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
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
  
## <a name="see-also"></a>請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
