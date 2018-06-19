---
title: helpcontext |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpcontext
dev_langs:
- C++
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 317e204c7292c4a7cccb1f81f6bc9d2a2fbfd407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877211"
---
# <a name="helpcontext"></a>helpcontext
指定的內容識別碼，可讓使用者檢視的說明檔中此項目有關的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 說明主題的內容識別碼。 請參閱[HTML 說明： 程式的即時線上說明](../mfc/html-help-context-sensitive-help-for-your-programs.md)如需有關內容識別碼。  
  
## <a name="remarks"></a>備註  
 **Helpcontext** c + + 屬性具有相同的功能[helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) MIDL 屬性。  
  
## <a name="example"></a>範例  
 請參閱範例的[defaultvalue](../windows/defaultvalue.md)如需如何使用的範例**helpcontext**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface``typedef`，**類別**、 方法、 屬性|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [說明檔](../windows/helpfile.md)   
 [helpstring](../windows/helpstring.md)   
