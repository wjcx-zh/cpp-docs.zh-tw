---
title: "&lt;value&gt; (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "value"
  - "<value>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<value> C++ XML 標記"
  - "value C++ XML 標記"
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;value&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<value\> 標記讓您描述屬性和屬性存取子方法。  請注意，當您加入具有程式碼精靈的屬性 Visual Studio 整合式開發環境中，它會將新的屬性的 [\<summary\>](../ide/summary-visual-cpp.md) 標記。  接著，您應該手動加入一個 \<value\> 標記，來說明該屬性表示的值。  
  
## 語法  
  
```  
<value>property-description</value>  
```  
  
#### 參數  
 `property-description`  
 屬性的描述。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
  
```  
// xml_value_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_value_tag.dll  
using namespace System;  
/// Text for class Employee.  
public ref class Employee {  
private:  
   String ^ name;  
   /// <value>Name accesses the value of the name data member</value>  
public:  
   property String ^ Name {  
      String ^ get() {  
         return name;   
      }  
      void set(String ^ i) {  
         name = i;  
      }  
   }  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)