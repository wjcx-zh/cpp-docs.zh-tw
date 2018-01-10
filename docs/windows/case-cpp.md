---
title: "大小寫 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.case
dev_langs: C++
helpviewer_keywords: case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: adacffa4dbce4cc908c393cb5019375234e9ff85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="case-c"></a>case (C++)
搭配[switch_type](../windows/switch-type.md)屬性**union**。  
  
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
  
 或這類類型的識別項。  
  
## <a name="remarks"></a>備註  
 **案例**c + + 屬性具有相同的功能**案例**MIDL 屬性。 這個屬性只能搭配[switch_type](../windows/switch-type.md)屬性。  
  
## <a name="example"></a>範例  
 下列程式碼將示範使用**案例**屬性：  
  
```  
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
|**適用於**|成員的**類別**或`struct`|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
