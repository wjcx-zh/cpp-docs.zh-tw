---
title: "&lt;example&gt; (Visual C++) | Microsoft Docs"
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
  - "<example>"
  - "example"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<example> C++ XML 標記"
  - "example C++ XML 標記"
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;example&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<example\> 標記讓您指定一個範例，說明如何使用方法或其他程式庫成員。  通常，這也會牽涉到 [\<code\>](../ide/code-visual-cpp.md) 標記的用途。  
  
## 語法  
  
```  
<example>description</example>  
```  
  
#### 參數  
 `description`  
 為程式碼範例的描述。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
  
```  
// xml_example_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_example_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <summary>  
   /// GetZero method  
   /// </summary>  
   /// <example> This sample shows how to call the GetZero method.  
   /// <code>  
   /// int main()   
   /// {  
   ///    return GetZero();  
   /// }  
   /// </code>  
   /// </example>  
   static int GetZero() {  
      return 0;  
   }  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)