---
title: "&lt;permission&gt; (Visual C++) | Microsoft Docs"
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
  - "permission"
  - "<permission>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<permission> C++ XML 標記"
  - "permission C++ XML 標記"
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;permission&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<permission\> 標記讓您記錄成員的存取。  <xref:System.Security.PermissionSet> 可讓您指定給成員的存取。  
  
## 語法  
  
```  
<permission cref="member">description</permission>  
```  
  
#### 參數  
 `member`  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  編譯器會檢查特定的程式碼項目是否存在，並在輸出的 XML 中將 `member` 轉譯為正式的項目名稱。  將名稱加上單引號或雙引號。  
  
 編譯器會發出警告 \(如果找不到 `member`。  
  
 如需如何建立泛型型別的 cref 參考之詳細資訊，請參閱 [\<see\>](../ide/see-visual-cpp.md)。  
  
 `description`  
 成員存取的描述。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
 Visual C\+\+ 編譯器會嘗試透過文件註解會剖析傳遞的 cref 參考。  因此，在中，如果使用 C\+\+ 搜尋規則，分隔符號是編譯器找不到參考會被標記為無法解析。  如需詳細資訊，請參閱 [\<seealso\>](../ide/seealso-visual-cpp.md)。  
  
## 範例  
  
```  
// xml_permission_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_permission_tag.dll  
using namespace System;  
/// Text for class TestClass.  
public ref class TestClass {  
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>  
   void Test() {}  
};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)