---
title: switch_type |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c6c1b6dda469dec663e5a8c385d300b113246a77
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016440"
---
# <a name="switchtype"></a>switch_type
識別做為等位的判別變數的型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[switch_type(  
type  
}]  
```  
  
### <a name="parameters"></a>參數  
 *type*  
 參數型別可以是整數、 字元、 布林值或列舉類型。  
  
## <a name="remarks"></a>備註  
 **Switch_type** c + + 屬性具有相同的功能[switch_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL 屬性。  
  
 不支援 c + + 屬性[封裝等位](http://msdn.microsoft.com/library/windows/desktop/aa366811)。 [Nonencapsulated 等位](http://msdn.microsoft.com/library/windows/desktop/aa367119)只支援下列格式：  
  
```cpp  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## <a name="example"></a>範例  
 請參閱[案例](../windows/case-cpp.md)的範例使用的範例**switch_type**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**typedef**|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   