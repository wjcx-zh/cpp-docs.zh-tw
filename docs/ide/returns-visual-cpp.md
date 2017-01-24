---
title: "&lt;returns&gt; (Visual C++) | Microsoft Docs"
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
  - "returns"
  - "<returns>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<returns> C++ XML 標記"
  - "returns C++ XML 標記"
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;returns&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<returns\> 標記應使用於方法宣告的註解來描述傳回值。  
  
## 語法  
  
```  
<returns>description</returns>  
```  
  
#### 參數  
 `description`  
 為傳回值的描述。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
  
```  
// xml_returns_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_returns_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <returns>Returns zero.</returns>  
   int GetZero() { return 0; }  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)