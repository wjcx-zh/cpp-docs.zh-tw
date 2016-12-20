---
title: "uuid (C++ Attributes) | Microsoft Docs"
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
  - "vc-attr.uuid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uuid attribute"
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uuid (C++ Attributes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定類別或介面的專一識別碼。  
  
## 語法  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### 參數  
 *uuid*  
 128 位元的唯一識別項。  
  
## 備註  
 如果未指定的介面或類別定義`uuid` C\+\+ 屬性，然後 Visual C\+\+ 編譯器會提供一個。  當您指定`uuid`，您必須將包含引號。  
  
 如果您未指定`uuid`，則編譯器會產生不同的屬性在電腦上的專案中的介面或類別具有相同的名稱相同的 GUID。  
  
 您可以使用 Uuidgen.exe 或 Guidgen.exe 來產生您自己的唯一識別碼。  \(若要執行這些工具的其中一個，請按一下 \[ **開始** 再利用 **執行**在功能表上。  然後輸入所需的工具的名稱\)。  
  
 也不會使用 ATL 專案中使用時，指定`uuid`屬性等同於指定 [uuid](../cpp/uuid-cpp.md) \_\_declspec 修飾詞。  若要擷取`uuid`的類別，您可以使用 [\_\_uuidof](../cpp/uuidof-operator.md)  
  
## 範例  
 請參閱[可繫結](../windows/bindable.md)的範例用法的範例`uuid`。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**, `struct`, `interface`, **union**,`enum`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)