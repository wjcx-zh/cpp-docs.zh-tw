---
title: "&lt;seealso&gt; (Visual C++) | Microsoft Docs"
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
  - "<seealso>"
  - "seealso"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<seealso> C++ XML 標記"
  - "seealso C++ XML 標記"
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;seealso&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<seealso\> 標記讓您指定在 \[參閱\] 部分要出現的文字。  使用 [\<see\>](../ide/see-visual-cpp.md) 從文字中指定連結。  
  
## 語法  
  
```  
<seealso cref="member"/>  
```  
  
#### 參數  
 `member`  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  將名稱加上單引號或雙引號。  
  
 編譯器會檢查特定程式碼項目是否存在並解析 `member` 給 XML 輸出檔案中的項目名稱。  編譯器會發出警告 \(如果找不到 `member`。  
  
 如需如何建立泛型型別的 cref 參考之詳細資訊，請參閱 [\<see\>](../ide/see-visual-cpp.md)。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
 為使用執行個體 \<seealso\>。請參閱 [\<summary\>](../ide/summary-visual-cpp.md) 。  
  
 Visual C\+\+ 編譯器會嘗試透過文件註解會剖析傳遞的 cref 參考。  因此，在中，如果使用 C\+\+ 搜尋規則，分隔符號是編譯器找不到參考會被標記為無法解析。  
  
## 範例  
 在下列範例中，未解析的符號在 cref 參考。  cref 的 XML 註解。B::Test 將為，則為 `<seealso cref="!:B::Test" />`，而對 A::Test 的參考是語式正確的 `<seealso cref="M:A.Test" />`。  
  
```  
// xml_seealso_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_seealso_tag.dll  
  
/// Text for class A.  
public ref struct A {  
   /// <summary><seealso cref="A::Test"/>  
   /// <seealso cref="B::Test"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void Test() {}  
};  
  
/// Text for class B.  
public ref struct B {  
   void Test() {}  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)