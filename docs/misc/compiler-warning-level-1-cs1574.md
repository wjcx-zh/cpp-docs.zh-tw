---
title: "編譯器警告 (層級 1) CS1574 | Microsoft Docs"
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
  - "CS1574"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1574"
ms.assetid: 4cd2b474-ab01-4397-aed7-63e5f0081649
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1574
'construct' 上 XML 註解的 cref 屬性 'name' 句法不正確  
  
 傳遞給 cref 標籤的字串，例如 \<例外狀況\> 標籤，參考了目前建置環境中無法使用的成員。 您傳遞給 cref 標籤的字串必須是語法正確的成員或欄位名稱。  
  
 如需詳細資訊，請參閱[建議使用的文件註解標籤](../Topic/Recommended%20Tags%20for%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS1574：  
  
```  
// CS1574.cs // compile with: /W:1 /doc:x.xml using System; /// <exception cref="System.Console.WriteLin">An exception class.</exception>   // CS1574 // instead, uncomment and try the following line // /// <exception cref="System.Console.WriteLine">An exception class.</exception> class EClass : Exception { } class TestClass { public static void Main() { try { } catch(EClass) { } } }  
```