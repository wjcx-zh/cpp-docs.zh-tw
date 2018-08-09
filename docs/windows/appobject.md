---
title: appobject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.appobject
dev_langs:
- C++
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78cc02c4f4d39b2bcba4c79a07ec84b9657cb66b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651193"
---
# <a name="appobject"></a>appobject
識別做為應用程式物件，這是完整的.exe 應用程式相關聯，表示全域可用在此函式和屬性的 coclass coclass[型別程式庫](../mfc/automation-clients-using-type-libraries.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[appobject]  
```  
  
## <a name="remarks"></a>備註  
 **Appobject** c + + 屬性具有相同的功能[appobject](http://msdn.microsoft.com/library/windows/desktop/aa366726) MIDL 屬性。  
  
## <a name="example"></a>範例  
 下列程式碼示範簡單的類別定義，加上包含的屬性區塊**appobject**:  
  
```cpp  
// cpp_attr_ref_appobject.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];  
  
[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]  
__interface ICustom {};  
  
[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]  
class A : public ICustom {  
   int i;  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，**結構**|  
|**可重複**|否|  
|**必要屬性**|`coclass`|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   