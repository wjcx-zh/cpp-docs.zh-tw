---
title: "&lt;see&gt; (Visual C++) | Microsoft Docs"
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
  - "<see>"
  - "see"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<see> C++ XML 標記"
  - "see C++ XML 標記"
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;see&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<see\> 標記讓您指定文字中的連結。  使用 [\<seealso\>](../ide/seealso-visual-cpp.md) 指定文字可以同時出現在參閱區段中。  
  
## 語法  
  
```  
<see cref="member"/>  
```  
  
#### 參數  
 `member`  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  將名稱加上單引號或雙引號。  
  
 編譯器會檢查特定程式碼項目是否存在並解析 `member` 給 XML 輸出檔案中的項目名稱。  編譯器會發出警告 \(如果找不到 `member`。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
 為使用執行個體 \<see\>。請參閱 [\<summary\>](../ide/summary-visual-cpp.md) 。  
  
 Visual C\+\+ 編譯器會嘗試透過文件註解會剖析傳遞的 cref 參考。  因此，在中，如果使用 C\+\+ 搜尋規則，分隔符號是編譯器找不到參考會被標記為無法解析。  如需詳細資訊，請參閱 [\<seealso\>](../ide/seealso-visual-cpp.md)。  
  
## 範例  
 下列範例顯示如何 cref 參考泛型型別，因此，編譯器會解析參考。  
  
```  
// xml_see_cref_example.cpp  
// compile with: /LD /clr /doc  
// the following cref shows how to specify the reference, such that,  
// the compiler will resolve the reference  
/// <see cref="C{T}">  
/// </see>  
ref class A {};  
  
// the following cref shows another way to specify the reference,   
// such that, the compiler will resolve the reference  
/// <see cref="C < T >"/>  
  
// the following cref shows how to hard-code the reference  
/// <see cref="T:C`1">  
/// </see>  
ref class B {};  
  
/// <see cref="A">  
/// </see>  
/// <typeparam name="T"></typeparam>  
generic<class T>  
ref class C {};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)