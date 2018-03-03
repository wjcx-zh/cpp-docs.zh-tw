---
title: "satype |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d4e083cfd0ee1a72992d3c400c4790f5cd50396
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="satype"></a>satype
指定的資料型別**SAFEARRAY**結構。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ satype(  
   data_type  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *data_type*  
 資料型別**SAFEARRAY**做為參數傳遞至介面方法的資料結構。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|介面參數，在介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
## <a name="remarks"></a>備註  
 **Satype** c + + 屬性指定的資料型別**SAFEARRAY**。  
  
> [!NOTE]
>  從卸除的間接取值層級**SAFEARRAY**如何宣告，在.cpp 檔案中產生的.idl 檔中的指標。  
  
## <a name="example"></a>範例  
  
```  
// cpp_attr_ref_satype.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyModule")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A {  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [id](../windows/id.md)   
