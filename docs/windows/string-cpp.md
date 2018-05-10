---
title: 字串 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bdcdc6557253f8be9c6ecb20300f2338ab35d07
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="string-c"></a>string (C++)
表示一維`char`， `wchar_t`，**位元組**（或對等） 陣列或這類陣列的指標必須視為字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
[string]  
  
```  
  
## <a name="remarks"></a>備註  
 **字串**c + + 屬性具有相同的功能[字串](http://msdn.microsoft.com/library/windows/desktop/aa367270)MIDL 屬性。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用**字串**介面上，並在 typedef 上：  
  
```  
// cpp_attr_ref_string.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, string] typedef char a[21];  
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1)] HRESULT Method3([in, string] char *pC);  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|陣列或指標陣列的介面參數、 介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [陣列屬性](../windows/array-attributes.md)   
 [export](../windows/export.md)   
