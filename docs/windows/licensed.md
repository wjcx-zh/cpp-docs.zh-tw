---
title: "授權 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.licensed
dev_langs: C++
helpviewer_keywords: licensed attribute
ms.assetid: 09cf3b4a-d3f2-43e3-9180-d420333b23bf
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d33e51cf938642f2ff54c48e1ecd22c3f48b71f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="licensed"></a>licensed
表示它所套用的 COM 物件係授權使用，而且必須使用具現化**IClassFactory2**。  
  
## <a name="syntax"></a>語法  
  
```  
  
[licensed]  
  
```  
  
## <a name="remarks"></a>備註  
 **授權**c + + 屬性具有相同的功能[授權](http://msdn.microsoft.com/library/windows/desktop/aa367070)MIDL 屬性。  
  
## <a name="example"></a>範例  
  
```  
// cpp_attr_ref_licensed.cpp  
// compile with: /LD  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {  
   HRESULT f();  
};  
  
[coclass, version("2.1"), uuid(12345678-1111-2222-3333-123456789012),   
licensed, threading(free), progid(some.name)]  
class CSample : public IMyI {  
public:  
   int nSize;  
};  
  
[module(name="MyLibrary", version="1.0", helpstring="My Library Block")];  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|**coclass**|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
