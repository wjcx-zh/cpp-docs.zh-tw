---
title: "編譯器警告 (層級 1) CS1570 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1570"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1570"
ms.assetid: a121d5c4-8b90-4cda-af5b-6ba8f23b2b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1570
'construct' 上 XML 註解的 'reason' XML 格式錯誤  
  
 使用 [\/doc](../Topic/-doc%20\(C%23%20Compiler%20Options\).md) 時，原始程式碼中的任何註解都必須為 XML 格式。 XML 標記的任何錯誤都會產生 CS1570。 例如:  
  
-   如果您是將字串傳遞給 **cref** \(例如，在 [\<例外狀況\>](../Topic/%3Cexception%3E%20\(C%23%20Programming%20Guide\).md) 標記中\)，則必須以雙引號括住字串。  
  
-   如果您是使用沒有結尾標記的標記 \(例如 [\<另請參閱\>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md)\)，則必須在右角括號前面指定正斜線。  
  
-   如果您需要在描述文字中使用大於或小於符號，則需要使用 **&gt;** 或 **&lt;** 代表它們。  
  
-   [\<包含\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) 標記上的檔案或路徑屬性遺漏或格式不正確。  
  
 下列範例會產生 CS1570：  
  
```  
// CS1570.cs // compile with: /W:1 namespace ns { // the following line generates CS1570 /// <summary> returns true if < 5 </summary> // try this instead // /// <summary> returns true if <5 </summary> public class MyClass { public static void Main () { } } }  
```