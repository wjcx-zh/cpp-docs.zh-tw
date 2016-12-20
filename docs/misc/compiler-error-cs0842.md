---
title: "編譯器錯誤 CS0842 | Microsoft Docs"
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
  - "CS0842"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0842"
ms.assetid: 93a8b333-efc4-40c7-ae53-5264f721a74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0842
在標記著 StructLayout\(LayoutKind.Explicit\) 的類型內部不能使用自動實作的屬性。  
  
 自動實作屬性的支援欄位是由編譯器所提供，原始程式碼無法存取此欄位。 因此，這些屬性與 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> 不相容。  
  
### 更正這個錯誤  
  
1.  將屬性設為可在其中提供存取子主體的一般屬性。  
  
## 範例  
 下列範例會產生 CS0842：  
  
```  
// cs0842.cs using System; using System.Runtime.InteropServices; namespace TestNamespace { [StructLayout(LayoutKind.Explicit)] struct Str { public int Num // CS0842 { get; set; } static int Main() { return 1; } } }  
```