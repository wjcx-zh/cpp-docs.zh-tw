---
title: "lcid |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.lcid
dev_langs: C++
helpviewer_keywords: LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36ccb085c2f6128012d446f6be15dff94c718e35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="lcid"></a>lcid
可讓您將地區設定識別碼傳遞給函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
[lcid]  
  
```  
  
## <a name="remarks"></a>備註  
 **Lcid** c + + 屬性實作的功能[lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) MIDL 屬性。 如果您想要實作的程式庫區的地區設定，使用**lcid =** `lcid`參數[模組](../windows/module-cpp.md)屬性。  
  
## <a name="example"></a>範例  
  
```  
// cpp_attr_ref_lcid.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
typedef long HRESULT;  
  
[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]  
__interface IStatic {  
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|介面參數|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
