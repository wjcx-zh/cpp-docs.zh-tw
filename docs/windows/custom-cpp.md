---
title: "自訂 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.custom
dev_langs: C++
helpviewer_keywords: custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f811197526d2d3da0700af27be84151da79d67f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="custom-c"></a>custom (C++)
類型程式庫中定義物件的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 *uuid*  
 唯一 ID。  
  
 *value*  
 值，這個值可以放入變數。  
  
## <a name="remarks"></a>備註  
 **自訂**c + + 屬性會導致資訊放入類型程式庫。 您必須從類型程式庫會讀取自訂值的工具。  
  
 **自訂**屬性具有相同的功能[自訂](http://msdn.microsoft.com/library/windows/desktop/aa366766)MIDL 屬性。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|非 COM `interface`，**類別**， `enum`s，`idl_module`方法、 介面成員、 介面參數`typedef`s， **union**s， `struct`s|  
|**可重複**|是|  
|**必要屬性**|**coclass** （時在類別上使用）|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [介面屬性](../windows/interface-attributes.md)   
