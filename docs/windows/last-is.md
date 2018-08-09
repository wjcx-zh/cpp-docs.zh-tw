---
title: last_is |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98527958ba9fdf2c2b53e8b18348cb93d3aed6ad
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016453"
---
# <a name="lastis"></a>last_is
指定要傳送的最後一個陣列元素的索引。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ last_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>參數  
 *運算式*  
 一或多個 C 語言的運算式。 允許空白的引數位置。  
  
## <a name="remarks"></a>備註  
 **Last_is** c + + 屬性具有相同的功能[last_is](http://msdn.microsoft.com/library/windows/desktop/aa367066) MIDL 屬性。  
  
## <a name="example"></a>範例  
 請參閱[first_is](../windows/first-is.md)如需如何指定的陣列區段的範例。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|欄位**結構**或是**聯集**，參數的介面，介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [max_is](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   