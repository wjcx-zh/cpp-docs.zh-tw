---
title: "import | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.import"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "import attribute"
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# import
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定包含您想要參考您主要的 IDL 中定義的另一個.idl、.odl 或標頭檔。  
  
## 語法  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### 參數  
 `idl_file`  
 您想要匯入型別程式庫，目前專案的.idl 檔的名稱。  
  
## 備註  
 **匯入** C\+\+ 屬性會造成`#import`陳述式放到以下`import "docobj.idl"`產生的.idl 檔內的陳述式。  **匯入** 屬性具有相同的功能，為 [匯入](http://msdn.microsoft.com/library/windows/desktop/aa367047) MIDL 屬性。  
  
 **匯入**屬性只會將指定的檔案放入.idl 檔，將由您的任務或資源。 **匯入**屬性不會讓您指定的檔案中的建構呼叫從專案中的原始程式碼。  建構中指定的檔案從呼叫程式碼置於您的專案，使用 [\# import](../preprocessor/hash-import-directive-cpp.md) 和`embedded_idl`屬性，或者也可以包含的.h 檔， `idl_file`、.h 檔案是否存在。  
  
## 範例  
 下列程式碼中：  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 將產生下列的程式碼產生的.idl 檔中：  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|全螢幕輸入|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [importidl](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [include](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)