---
title: retval |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c0bf7ecd989b51a17c853c6d2986db204c3ce34
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="retval"></a>retval
指定接收成員的傳回值的參數。  
  
## <a name="syntax"></a>語法  
  
```  
  
[retval]  
  
```  
  
## <a name="remarks"></a>備註  
 **Retval** c + + 屬性具有相同的功能[retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL 屬性。  
  
 **retval**必須出現在函式宣告中的最後一個引數。  
  
## <a name="example"></a>範例  
 請參閱範例的[可繫結](../windows/bindable.md)的範例使用**retval**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|介面參數，在介面方法|  
|**可重複**|否|  
|**必要屬性**|**out**|  
|**無效屬性**|**in**|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
