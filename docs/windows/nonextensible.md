---
title: "nonextensible |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.nonextensible
dev_langs: C++
helpviewer_keywords: nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 277e8ad4b19f5da5cf0d5574e240915ddc9b525c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="nonextensible"></a>nonextensible
指定`IDispatch`實作只會包含屬性和方法的介面描述中所列，並且無法在執行階段擴充與其他成員。  
  
## <a name="syntax"></a>語法  
  
```  
  
[nonextensible]  
  
```  
  
## <a name="remarks"></a>備註  
 **Nonextensible** c + + 屬性具有相同的功能[nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) MIDL 屬性。  
  
 使用**nonextensible**也需要[oleautomation](../windows/oleautomation.md)屬性。  
  
## <a name="example"></a>範例  
 下列程式碼將示範使用一**nonextensible**屬性：  
  
```  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`|  
|**可重複**|否|  
|**必要屬性**|**雙重**和**oleautomation**，或**分配介面**|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
