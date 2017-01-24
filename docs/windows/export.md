---
title: "export | Microsoft Docs"
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
  - "vc-attr.export"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "export attribute"
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# export
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

會造成.idl 檔內放置的資料結構。  
  
## 語法  
  
```  
  
[export]  
  
```  
  
## 備註  
 **匯出** C\+\+ 屬性會造成一種資料結構放置在.idl 檔，並可以在型別程式庫，以使其可用於任何語言的二進位相容格式。  
  
 您無法套用**匯出**屬性至類別，即使此類別只具有公用的成員 \(相當於`struct`\)。  
  
 如果您匯出 \[未命名`enum`s 或`struct`s，就能指定的名稱開頭的 **\_\_unnamed***x*，其中 *x* 是一個循序編號。  
  
 檔的 typedef 也適用於匯出基底型別、 結構、 等位、 列舉、 或型別識別項。  請參閱 [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) 如需詳細資訊。  
  
## 範例  
 下列程式碼示範如何使用**匯出**屬性：  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**union**, `typedef`, `enum`, `struct`, or`interface`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)