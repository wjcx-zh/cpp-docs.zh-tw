---
title: "同步處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.synchronize
dev_langs: C++
helpviewer_keywords: synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38898eefcbc2d5bb882186786894e7fb752e28ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="synchronize"></a>synchronize
同步處理至目標方法的存取。  
  
## <a name="syntax"></a>語法  
  
```  
  
[synchronize]  
  
```  
  
## <a name="remarks"></a>備註  
 **同步**c + + 屬性實作同步處理物件的目標方法的支援。 同步處理允許多個物件使用的一般資源 （例如類別的方法） 控制目標方法的存取權。  
  
 這個屬性所插入的程式碼會呼叫適當`Lock`目標方法的開頭 （由執行緒模型） 的方法。 當方法結束時，`Unlock`自動呼叫。 如需這些函式的詳細資訊，請參閱[CComAutoThreadModule::Lock](../atl/reference/ccomautothreadmodule-class.md#lock)  
  
 此屬性需要 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi_progid](../windows/vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用 **progid** ，則也會套用 **vi_progid** 和 **coclass** 。  
  
## <a name="example"></a>範例  
 下列程式碼提供的同步處理`UpdateBalance`方法`CMyClass`物件。  
  
```  
// cpp_attr_ref_synchronize.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="SYNC")];  
  
[coclass,  
 threading(both),  
 vi_progid("MyProject.MyClass"),  
 progid("MyProject.MyClass.1"),  
 uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")  
]  
class CMyClass {  
   float m_nBalance;  
  
   [synchronize]  
   void UpdateBalance(float nAdjust) {  
      m_nBalance += nAdjust;  
   }  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|類別方法方法|  
|**可重複**|否|  
|**必要屬性**|下列一或多個項目： **coclass**、 **progid**或 **vi_progid**。|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [COM 屬性](../windows/com-attributes.md)   
