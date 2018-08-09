---
title: 限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af30716208b4caf949630ba5f6965fcc6a1a54c2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017054"
---
# <a name="restricted"></a>restricted
指定的模組、 介面或 dispinterface 成員不能任意呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ restricted(  
   interfaces  
) ]  
```  
  
### <a name="parameters"></a>參數  
 *interfaces*  
 Metodu nelze volat 任意 COM 物件的一或多個介面。 此參數才有效時套用至類別。  
  
## <a name="remarks"></a>備註  
 **受限**c + + 屬性具有相同的功能[限制](http://msdn.microsoft.com/library/windows/desktop/aa367157)MIDL 屬性。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用**限制**屬性：  
  
```cpp  
// cpp_attr_ref_restricted.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface b  
{  
};  
  
[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]  
class c : public a, public b  
{  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|介面方法，**介面**，**類別**，**結構**|  
|**可重複**|否|  
|**必要屬性**|**coclass** (當套用至**類別**或是**結構**)|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   