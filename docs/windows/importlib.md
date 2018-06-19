---
title: importlib |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importlib
dev_langs:
- C++
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c21b97e50fa03861245a0c0881963387dd8a3102
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876754"
---
# <a name="importlib"></a>importlib
讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ importlib(  
   "tlb_file"  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 *tlb_file*  
 您要匯入目前專案之類型程式庫中的 .tlb 檔案名稱 (加上引號)。  
  
## <a name="remarks"></a>備註  
 **Importlib** c + + 屬性會造成`importlib`放置產生的.idl 檔案的程式庫區塊中的陳述式。 **Importlib**屬性具有相同的功能[importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) MIDL 屬性。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用**importlib**:  
  
```  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
 [匯入](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [包含](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)