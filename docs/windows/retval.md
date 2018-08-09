---
title: retval |Microsoft Docs
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
ms.openlocfilehash: e4364f60012cb4571edbf195a02b77f500a2dc86
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010327"
---
# <a name="retval"></a>retval
指定接收成員的傳回值的參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[retval]  
```  
  
## <a name="remarks"></a>備註  
 **Retval** c + + 屬性具有相同的功能[retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL 屬性。  
  
 **retval**必須出現在函式宣告中的最後一個引數。  
  
## <a name="example"></a>範例  
 範例，請參閱[可繫結](../windows/bindable.md)範例使用**retval**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|介面參數，介面方法|  
|**可重複**|否|  
|**必要屬性**|**out**|  
|**無效屬性**|**in**|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   