---
title: "編譯器錯誤 CS0160 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0160"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0160"
ms.assetid: 4ef07061-8ef5-42d9-b043-3f81307d569f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0160
之前的 catch 子句已取得所有屬於此類型或超級類型 \('type'\) 的例外狀況  
  
 一系列的 **catch** 陳述式必須依照衍生的遞減順序。 例如，最具衍生性的物件必須最先出現。  
  
 如需詳細資訊，請參閱[例外狀況處理陳述式](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)和[例外狀況和例外狀況處理](../Topic/Exceptions%20and%20Exception%20Handling%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0160：  
  
```  
// CS0160.cs public class MyClass2 : System.Exception {} public class MyClass { public static void Main() { try {} catch(System.Exception) {}   // Second-most derived; should be second catch catch(MyClass2) {}   // CS0160  Most derived; should be first catch } }  
```