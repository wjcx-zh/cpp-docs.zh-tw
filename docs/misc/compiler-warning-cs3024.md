---
title: "編譯器警告 CS3024 | Microsoft Docs"
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
  - "CS3024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3024"
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 CS3024
條件約束類型 'type' 不符合 CLS 標準。  
  
 由於使用不符合 CLS 標準的類型作為泛型類型條件約束，可能會使得以某些語言撰寫的程式碼無法使用您的泛型類別，因此編譯器會發出這個警告。  
  
### 移除這個警告  
  
1.  針對類型條件約束使用符合 CLS 標準的類型。  
  
## 範例  
 下列範例會在幾個位置產生 CS3024：  
  
```  
// cs3024.cs // Compile with: /target:library [assembly: System.CLSCompliant(true)] [type: System.CLSCompliant(false)] public class TestClass // CS3024 { public ushort us; } [type: System.CLSCompliant(false)] public interface ITest // CS3024 {} public interface I<T> where T : TestClass {} public class TestClass_2<T> where T : ITest {} public class TestClass_3<T> : I<T> where T : TestClass {} public class TestClass_4<T> : TestClass_2<T> where T : ITest {} public class Test { public static int Main() { return 0; } }  
```  
  
## 請參閱  
 [類型參數的條件約束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)