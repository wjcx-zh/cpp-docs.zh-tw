---
title: "cpp_quote |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.cpp_quote
dev_langs: C++
helpviewer_keywords: cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95b43856401b5bccfa9a0bef12fdc93ec886cea1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cppquote"></a>cpp_quote
指定的字串，不能包含引號字元，發出至產生的.idl 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 *statement*  
 C 指令。  
  
## <a name="remarks"></a>備註  
 **Cpp_quote** c + + 屬性才有用，如果您想要將前置處理器指示詞放在.idl 檔案。  
  
 您也可以使用**cpp_quote**和的 MIDL 編譯時產生的.h 檔案。 例如，如果您有使用 c + + IDL 屬性，但是某些工作不能使用此檔案的 c + + 標頭檔，然後您可以編譯它建立 MIDL 產生的.h 檔案，您應該能夠使用。  
  
 **Cpp_quote**屬性具有相同的功能[cpp_quote](http://msdn.microsoft.com/library/windows/desktop/aa366765) MIDL 屬性。  
  
## <a name="example"></a>範例  
 請參閱範例的[雙重](../windows/dual.md)範例使用使用方式**cpp_quote**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
