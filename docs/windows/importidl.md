---
title: importidl |Microsoft Docs
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
ms.openlocfilehash: 1de680b2598a9439338986c283a4041482642fa0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015754"
---
# <a name="importidl"></a>importidl
指定的.idl 檔插入所產生的.idl 檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ importidl(  
   idl_file  
) ];  
```  
  
### <a name="parameters"></a>參數  
 *idl_file*  
 識別您想要與您的應用程式將會產生.idl 檔案合併的.idl 檔案的名稱。  
  
## <a name="remarks"></a>備註  
 **Importidl** c + + 屬性會放之外的程式庫區塊的區段 (在*idl_file*) 到您的程式產生的.idl 檔案和程式庫 > 一節 (在*idl_file*) 到程式庫，您的程式區段產生.idl 檔案。  
  
 您可能想要**importidl**，比方說，如果您想要使用產生的.idl 檔案中的手動編碼的.idl 檔案。  
  
## <a name="example"></a>範例  
  
```cpp  
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