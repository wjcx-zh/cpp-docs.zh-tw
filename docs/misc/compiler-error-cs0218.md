---
title: "編譯器錯誤 CS0218 | Microsoft Docs"
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
  - "CS0218"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0218"
ms.assetid: f675e06a-c55c-44a1-b5db-0df178fd8f79
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0218
類型 \('type'\) 必須包含運算子 true 和運算子 false 的宣告  
  
 如果您定義了一個使用者定義類型的運算子，然後嘗試使用該運算子作為最少運算運算子，則使用者定義運算子必須已定義運算子 true 和運算子 false。 如需最少運算運算子的詳細資訊，請參閱 [&& 運算子](../Topic/&&%20Operator%20\(C%23%20Reference\).md)和 [&#124;&#124; 運算子](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0218：  
  
```  
// CS0218.cs using System; public class MyClass { // uncomment these operator declarations to resolve this CS0218 /* public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } */ public static implicit operator int(MyClass x) { return 0; } public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f;   // CS0218, requires operators true and false } }  
```  
  
## 請參閱  
 [轉換運算子](../Topic/Conversion%20Operators%20\(C%23%20Programming%20Guide\).md)