---
title: 大小寫 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6567650d719b56bb320f1b40eae285322bcab364
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464307"
---
# <a name="case-c"></a>case (C++)
搭配[switch_type](../windows/switch-type.md)屬性中**聯集**。  
  
## <a name="syntax"></a>語法  
  
```  
[ case(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *值*  
 可能的輸入的值，您要提供處理。 型別**值**可以是下列類型之一：  
  
-   `int`  
  
-   `char`  
  
-   `boolean`  
  
-   `enum`  
  
 或此型別的識別項。  
  
## <a name="remarks"></a>備註  
 **案例**c + + 屬性具有相同的功能**案例**MIDL 屬性。 這個屬性只能搭配[switch_type](../windows/switch-type.md)屬性。  
  
## <a name="example"></a>範例  
 下列程式碼範例將示範用法**案例**屬性：  
  
```cpp  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|成員**類別**或**結構**|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   