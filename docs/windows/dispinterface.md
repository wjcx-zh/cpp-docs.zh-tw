---
title: dispinterface |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6497d6da630095f4d7691edb076fc354b87e5a13
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569210"
---
# <a name="dispinterface"></a>dispinterface
將介面放入 .idl 檔案中作為分派介面。  
  
## <a name="syntax"></a>語法  
  
```  
[dispinterface]  
```  
  
## <a name="remarks"></a>備註  
 **dispinterface** C++ 屬性在介面前面時，會將介面放在所產生 .idl 檔案的程式庫區塊內。  
  
 除非您指定基底類別，否則分派介面將衍生自 `IDispatch`。 您必須指定分派介面成員的 [id](../windows/id.md) 。  
  
 MIDL 文件中 [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) 的用法範例：  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 不適用於 **dispinterface** 屬性。  
  
## <a name="example"></a>範例  
 如需如何使用 [dispinterface](../windows/bindable.md) 的範例，請參閱 **bindable**範例。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**interface**|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|**dual**、 **object**、 **oleautomation**、 `local`、 **ms_union**|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [屬性的用法](../windows/attributes-by-usage.md)   
 [uuid](../windows/uuid-cpp-attributes.md)   
 [雙重](../windows/dual.md)   
 [自訂](../windows/custom-cpp.md)   
 [object](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   