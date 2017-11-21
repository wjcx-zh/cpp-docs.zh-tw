---
title: "版本 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.version
dev_langs: C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 757ab7a6d2c8b846a51da359c4b8dc5a72c6e9e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="version-c"></a>version (C++)
識別類別的多個版本之間的特定版本。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *version*  
 Coclass 的版本號碼。 如果未指定，1.0 會放入.idl 檔案。  
  
## <a name="remarks"></a>備註  
 **版本**c + + 屬性具有相同的功能[版本](http://msdn.microsoft.com/library/windows/desktop/aa367306)MIDL 屬性，並透過傳遞給產生的.idl 檔案。  
  
## <a name="example"></a>範例  
 請參閱[可繫結](../windows/bindable.md)範例使用範例**版本**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|**coclass**|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
