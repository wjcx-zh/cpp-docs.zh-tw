---
title: "&lt;exception&gt; (Visual C++) | Microsoft Docs"
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
  - "exception"
  - "<exception>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<exception> C++ XML 標記"
  - "exception C++ XML 標記"
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;exception&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個 \<exception\> 標記讓您指定可以擲出哪些例外狀況，  並套用在方法定義上。  
  
## 語法  
  
```  
<exception cref="member">description</exception>  
```  
  
#### 參數  
 `member`  
 一個可以用於目前編譯環境例外狀況的參考。  使用名稱搜尋規則，編譯器會檢查特定例外狀況存在，而且轉譯 `member` 為匯出 XML 的正式的項目名稱。  編譯器會發出警告 \(如果找不到 `member`。  
  
 將名稱加上單引號或雙引號。  
  
 如需如何建立泛型型別的 cref 參考之詳細資訊，請參閱 [\<see\>](../ide/see-visual-cpp.md)。  
  
 `description`  
 一段說明文字。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
 Visual C\+\+ 編譯器會嘗試透過文件註解會剖析傳遞的 cref 參考。  因此，在中，如果使用 C\+\+ 搜尋規則，分隔符號是編譯器找不到參考會被標記為無法解析。  如需詳細資訊，請參閱 [\<seealso\>](../ide/seealso-visual-cpp.md)。  
  
## 範例  
  
```  
// xml_exception_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_exception_tag.dll  
using namespace System;  
  
/// Text for class EClass.  
public ref class EClass : public Exception {  
   // class definition ...  
};  
  
/// <exception cref="System.Exception">Thrown when... .</exception>  
public ref class TestClass {  
   void Test() {  
      try {  
      }  
      catch(EClass^) {  
      }  
   }  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)