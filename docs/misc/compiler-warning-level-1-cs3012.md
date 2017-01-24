---
title: "編譯器警告 (層級 1) CS3012 | Microsoft Docs"
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
  - "CS3012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3012"
ms.assetid: 1f7555b4-61e4-4821-85c9-586301df4c5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS3012
在模組上指定的 CLSCompliant 屬性不能與組件上的 CLSCompliant 屬性不同  
  
 為了讓模組透過 `[module:System.CLCSompliant(true)]` 符合 Common Language Specification \(CLS\) 標準，必須以 [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) 編譯器選項建置該模組。 如需 CLS 的詳細資訊，請參閱[語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  
  
## 範例  
 未使用 `/target:module` 建置時，下列範例會產生 CS3012：  
  
```  
// CS3012.cs // compile with: /W:1 [module:System.CLSCompliant(true)]   // CS3012 public class C { public static void Main() { } }  
```