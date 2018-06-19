---
title: 匯入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b371cd1094a49f8a629cb6f8e880fd1210670f91
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877263"
---
# <a name="import"></a>import
指定包含的定義您想要從您主要的 IDL 中參考的另一個.idl、.odl 或標頭檔。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 `idl_file`  
 您要匯入目前專案的類型程式庫的.idl 檔案名稱。  
  
## <a name="remarks"></a>備註  
 **匯入**c + + 屬性會造成`#import`放下方的陳述式`import "docobj.idl"`產生的.idl 檔案中的陳述式。 **匯入**屬性具有相同的功能[匯入](http://msdn.microsoft.com/library/windows/desktop/aa367047)MIDL 屬性。  
  
 **匯入**屬性只會將指定的檔案放入您的專案，將產生的.idl 檔案**匯入**屬性不會讓您從來源程式碼，呼叫的建構中指定的檔案在您的專案。  若要呼叫的建構，請在指定的檔案從您的專案中原始程式碼使用[#import](../preprocessor/hash-import-directive-cpp.md)和`embedded_idl`屬性，或者您可以加入的.h 檔案的`idl_file`.h 檔案存在，則。  
  
## <a name="example"></a>範例  
 下列程式碼範例：  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 會產生下列程式碼產生的.idl 檔案中：  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
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
 [IDL 屬性](../windows/idl-attributes.md)   
 [獨立屬性](../windows/stand-alone-attributes.md)   
 [importidl](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [包含](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
