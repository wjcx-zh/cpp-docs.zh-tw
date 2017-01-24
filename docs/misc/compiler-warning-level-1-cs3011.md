---
title: "編譯器警告 (層級 1) CS3011 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3011"
ms.assetid: e27ce521-0147-488b-b4a1-1b6fb5168661
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3011
'member': 只有符合 CLS 標準的成員，才可為抽象  
  
 類別成員不可同時為[抽象](../Topic/abstract%20\(C%23%20Reference\).md)和不符合 Common Language Specification \(CLS\) 標準。 CLS 指定應該實作所有類別成員。 如需 CLS 符合性的詳細資訊，請參閱[撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)和[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 下列範例會產生 CS3011：  
  
```  
// CS3011.cs using System; [assembly:CLSCompliant(true)] public abstract class I { [CLSCompliant(false)] public abstract int M();   // CS3011 // OK [CLSCompliant(false)] public void M2() { } } public class C : I { public override int M() { return 1; } public static void Main() { } }  
```