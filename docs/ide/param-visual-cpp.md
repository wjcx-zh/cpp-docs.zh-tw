---
title: "&lt;param&gt; (Visual C++) | Microsoft Docs"
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
  - "param"
  - "<param>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<param> C++ XML 標記"
  - "param C++ XML 標記"
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;param&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<param\> 標記應使用於方法宣告的註解中，以描述該方法其中之一的參數。  
  
## 語法  
  
```  
<param name='name'>description</param>  
```  
  
#### 參數  
 `name`  
 為方法參數的名稱。  將名稱加上單引號或雙引號。  編譯器會發出警告 \(如果找不到 `name`。  
  
 `description`  
 參數的描述。  
  
## 備註  
 \<param\> 標記的文字會顯示在 IntelliSense， [物件瀏覽器](http://msdn.microsoft.com/zh-tw/f89acfc5-1152-413d-9f56-3dc16e3f0470)和程式碼結構 Web 報告。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)