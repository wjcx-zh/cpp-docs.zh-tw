---
title: 本機 （c + +） |Microsoft Docs
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
ms.openlocfilehash: efa937c1eaabb23fe5a360444f8c2105b735b260
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604196"
---
# <a name="local-c"></a>local (C++)
介面的標頭中使用時，可讓您使用 MIDL 編譯器為標頭的產生器。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。  
  
## <a name="syntax"></a>語法  
  
```  
[local]  
```  
  
## <a name="remarks"></a>備註  
 **本機**c + + 屬性具有相同的功能[本機](http://msdn.microsoft.com/library/windows/desktop/aa367071)MIDL 屬性。  
  
## <a name="example"></a>範例  
 請參閱[call_as](../windows/call-as.md)如需如何使用的範例**本機**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**介面**，介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|`dispinterface`|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   