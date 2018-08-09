---
title: 來源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.source
dev_langs:
- C++
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a30598e617a4c68559d6932e20dadaf7f83dc2eb
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015516"
---
# <a name="source-c"></a>source (C++)
在類別上，指定連接點的 COM 物件的來源介面。 在屬性或方法中，表示成員傳回的物件或變數，是事件來源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ source(  
   interfaces  
) ]  
```  
  
### <a name="parameters"></a>參數  
 *interfaces*  
 一或多個介面，指定當您將套用的來源屬性的類別。 未在來源套用至屬性或方法時，會使用此參數。  
  
## <a name="remarks"></a>備註  
 **來源**c + + 屬性具有相同的功能[來源](http://msdn.microsoft.com/library/windows/desktop/aa367166)MIDL 屬性。  
  
 您可以使用[預設](../windows/default-cpp.md)屬性來指定預設來源介面的物件。  
  
## <a name="example"></a>範例  
  
```cpp  
// cpp_attr_ref_source.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid(11111111-1111-1111-1111-111111111111)]  
__interface b  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]  
   HRESULT get_I([out, retval]long *i);  
};  
  
[object, uuid(11111111-1111-1111-1111-111111111131)]  
__interface c  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]   
   HRESULT et_I([out, retval]long *i);  
};  
  
[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]  
class N : public b  
{  
};  
  
[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]  
class NN : public b  
{  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**， **struct**，**介面**|  
|**可重複**|否|  
|**必要屬性**|`coclass` （當套用至類別或結構）|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [coclass](../windows/coclass.md)   