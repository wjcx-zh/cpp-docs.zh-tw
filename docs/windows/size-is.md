---
title: size_is |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8dbb3bfbf61c4ad7303c6cee272e14fc91bc9656
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011851"
---
# <a name="sizeis"></a>size_is
指定記憶體的大小配置大小的指標、 調整大小來調整大小的指標，以及單一或多維陣列的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ size_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>參數  
 *運算式*  
 所配置的記憶體大小調整大小的指標。  
  
## <a name="remarks"></a>備註  
 **Size_is** c + + 屬性具有相同的功能[size_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) MIDL 屬性。  
  
## <a name="example"></a>範例  
 範例，請參閱[first_is](../windows/first-is.md)如需如何指定的陣列區段的範例。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|欄位**結構**或是**聯集**，參數的介面，介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|`max_is`|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [max_is](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   