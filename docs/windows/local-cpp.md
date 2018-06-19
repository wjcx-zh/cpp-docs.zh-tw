---
title: 本機 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17a57ad56402b345aa64e4e4fd02bc57dd7f0321
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877913"
---
# <a name="local-c"></a>local (C++)
介面標頭中使用時，可讓您使用 MIDL 編譯器為標頭產生器。 個別的函式中使用時，會指定產生的任何虛設常式區域的程序。  
  
## <a name="syntax"></a>語法  
  
```  
  
[local]  
  
```  
  
## <a name="remarks"></a>備註  
 `local` C + + 屬性具有相同的功能[本機](http://msdn.microsoft.com/library/windows/desktop/aa367071)MIDL 屬性。  
  
## <a name="example"></a>範例  
 請參閱[call_as](../windows/call-as.md)如需如何使用的範例`local`。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|**dispinterface**|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   
