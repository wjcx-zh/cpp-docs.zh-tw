---
title: "編譯器警告 (層級 3) CS1717 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1717"
ms.assetid: 5b150a2c-5d61-4cd8-b4d4-e6c2b93b52c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS1717
對同一個變數進行指派; 您是否想要指派別的東西?  
  
 當您將變數指派給它本身時，例如 `a = a`，就會出現這個警告。  
  
 幾個常見的錯誤都會產生這個警告：  
  
-   將 `a = a` 寫成 **if** 陳述式的條件，例如 `if (a = a)`。 您的意思可能是 `if (a == a)`，這一律為 true，所以您可以寫成更簡潔的 `if (true)`。  
  
-   拼錯字。 您的意思可能是 `a = b`。  
  
-   在參數和欄位同名的建構函式中，不要使用 **this** 關鍵字：您的意思可能是 `this.a = a`。  
  
## 範例  
 下列範例會產生 CS1717。  
  
```  
// CS1717.cs // compile with: /W:3 public class Test { public static void Main() { int x = 0; x = x;   // CS1717 } }  
```