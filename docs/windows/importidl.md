---
title: importidl |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5284c631813271f5682343c74cff693d1ea785e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="importidl"></a>importidl
將指定的.idl 檔案插入至產生的.idl 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ importidl(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 `idl_file`  
 識別您想要與應用程式將會產生.idl 檔案合併的.idl 檔案名稱。  
  
## <a name="remarks"></a>備註  
 **Importidl** c + + 屬性會放在程式庫區塊外的區段 (在`idl_file`) 至您的程式產生的.idl 檔案和媒體櫃一節 (在`idl_file`) 到您的程式的程式庫區段產生的.idl 檔案。  
  
 您可能想要使用**importidl**，例如，如果您想要使用手動編碼的.idl 檔與產生的.idl 檔案。  
  
## <a name="example"></a>範例  
  
```  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
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
 [importlib](../windows/importlib.md)   
 [包含](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
