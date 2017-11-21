---
title: "defaultvtable |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.defaultvtable
dev_langs: C++
helpviewer_keywords: defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0753887cef2b169758351be9fafc0ec532bacb05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="defaultvtable"></a>defaultvtable
為 COM 物件的預設 vtable 介面定義的介面。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ defaultvtable(  
   interface  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `interface`  
 您想要在 COM 物件的預設 vtable 指定的介面。  
  
## <a name="remarks"></a>備註  
 **Defaultvtable** c + + 屬性具有相同的功能[defaultvtable](http://msdn.microsoft.com/library/windows/desktop/aa366795) MIDL 屬性。  
  
## <a name="example"></a>範例  
 下列程式碼所使用的類別顯示屬性**defaultvtable**指定預設介面：  
  
```  
// cpp_attr_ref_defaultvtable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI1 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface IMyI2 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000003")]  
__interface IMyI3 {  
   HRESULT x();  
};  
  
[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),  
uuid("00000000-0000-0000-0000-000000000004")]  
class CMyC3 : public IMyI3 {};  
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
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
