---
title: "registration_script |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.registration_script
dev_langs: C++
helpviewer_keywords: registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2260006e45407051f37e220d01cebd0ba8f797d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="registrationscript"></a>registration_script
執行指定的自訂註冊指令碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ registration_script(   
   script   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *指令碼*  
 自訂註冊指令碼 (.rgs) 檔案的完整路徑。 值為**無**，例如`script = "none"`，表示 coclass 擁有任何註冊需求。  
  
## <a name="remarks"></a>備註  
 **Registration_script** c + + 屬性來執行所指定的自訂註冊指令碼**指令碼**。 如果未指定此屬性，則會使用標準的.rgs 檔案 （包含將元件註冊資訊）。 如需有關.rgs 檔案的詳細資訊，請參閱[ATL 登錄元件 （登錄器）](../atl/atl-registry-component-registrar.md)。  
  
 此屬性需要 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi_progid](../windows/vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。  
  
## <a name="example"></a>範例  
 下列程式碼會指定此元件的呼叫 cpp_attr_ref_registration_script.rgs 登錄指令碼。  
  
```  
// cpp_attr_ref_registration_script.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="REG")];  
  
[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]  
__interface IFace {};  
  
// requires "cpp_attr_ref_registration_script.rgs"  
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist  
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),  
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]  
class CMyClass:public IFace {};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|下列一或多個項目： **coclass**、 **progid**或 **vi_progid**。|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [COM 屬性](../windows/com-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [rdx](../windows/rdx.md)   
