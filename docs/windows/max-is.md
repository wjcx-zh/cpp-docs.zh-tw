---
title: max_is |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3fae7ee95255d72d2799a5913821606f770e2b3b
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608426"
---
# <a name="maxis"></a>max_is
指定有效的陣列索引的最大值。  
  
## <a name="syntax"></a>語法  
  
```  
[ max_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *運算式*  
 一或多個 C 語言的運算式。 允許空白的引數位置。  
  
## <a name="remarks"></a>備註  
 **Max_is** c + + 屬性具有相同的功能[max_is](http://msdn.microsoft.com/library/windows/desktop/aa367074) MIDL 屬性。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|欄位**結構**或是**聯集**，參數的介面，介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|**size_is**|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="example"></a>範例  
 請參閱[first_is](../windows/first-is.md)如需如何指定的陣列區段的範例。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [length_is](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   