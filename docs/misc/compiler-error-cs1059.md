---
title: "編譯器錯誤 CS1059 | Microsoft Docs"
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
  - "CS1059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1059"
ms.assetid: 3ebd02ab-e40d-4aad-b901-a0cb6e2eace7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1059
遞增或遞減運算子的運算元必須是變數、屬性或索引子。  
  
 當您嘗試遞增或遞減常數值時，會引發這個錯誤。 如果您嘗試遞增運算式 \(例如 `(a+b)++`\)，也可能會發生這個錯誤。  
  
### 更正這個錯誤  
  
-   將變數設為非 const。  
  
-   移除遞增和遞減運算子。  
  
-   將運算式儲存在變數中，然後遞增變數。  
  
## 範例  
 下列範例會產生 CS1059，因為 `i` 是常數，而非變數，而 `E` 是其項目也是常數值的 `Enum` 類型。  
  
```  
// CS1059.cs class Program { public enum E : sbyte { a = 1, b = 2 } static void Main(string[] args) { const int i = 0; i++;            // CS1059 E test = E.a++; // CS1059 } }  
```  
  
## 請參閱  
 [常數](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)