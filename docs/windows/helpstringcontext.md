---
title: helpstringcontext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b71d8183921e0df66d6b9a82ff79faf24ccb41d3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642330"
---
# <a name="helpstringcontext"></a>helpstringcontext
指定.hlp 或.chm 檔案中的說明主題的識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ helpstringcontext(  
   contextID  
) ]  
```  
  
### <a name="parameters"></a>參數  
 *contextID*  
 在 32 位元說明內容識別碼**協助**檔案。  
  
## <a name="remarks"></a>備註  
 **Helpstringcontext** c + + 屬性具有相同的功能[helpstringcontext](http://msdn.microsoft.com/library/windows/desktop/aa366858) ODL 屬性。  
  
## <a name="example"></a>範例  
  
```cpp  
// cpp_attr_ref_helpstringcontext.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[   object,   
   helpstring("help string"),   
   helpstringcontext(1),   
   uuid="11111111-1111-1111-1111-111111111111"  
]  
__interface IMyI   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，**介面**，介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [模組](../windows/module-cpp.md)   