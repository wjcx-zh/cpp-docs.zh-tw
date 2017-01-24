---
title: "編譯器錯誤 CS0633 | Microsoft Docs"
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
  - "CS0633"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0633"
ms.assetid: a24d310b-151a-45eb-b150-3407940ec24c
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0633
'attribute' 屬性的引數必須是有效的識別項  
  
 任何傳遞給 <xref:System.Diagnostics.ConditionalAttribute> 或 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 屬性的引數都必須是有效的識別項。 這表示它可能未包含字元 \(例如 "\+"\)，這些字元出現在識別項中時不合法。  
  
## 範例  
 這個範例使用 <xref:System.Diagnostics.ConditionalAttribute> 來說明 CS0633。 下列範例會產生 CS0633。  
  
```  
// CS0633a.cs #define DEBUG using System.Diagnostics; public class Test { [Conditional("DEB+UG")]   // CS0633 // try the following line instead // [Conditional("DEBUG")] public static void Main() { } }  
```  
  
## 範例  
 這個範例使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 來說明 CS0633。  
  
```  
// CS0633b.cs // compile with: /target:module #define DEBUG using System.Runtime.CompilerServices; public class Test { [IndexerName("Invalid+Identifier")]   // CS0633 // try the following line instead // [IndexerName("DEBUG")] public int this[int i] { get { return i; } } }  
  
```