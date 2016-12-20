---
title: "編譯器錯誤 CS0636 | Microsoft Docs"
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
  - "CS0636"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0636"
ms.assetid: 47597f89-fbe6-4708-9493-3c86c6f0ce56
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0636
FieldOffset 屬性僅能置於標記為 StructLayout\(LayoutKind.Explicit\) 類型的成員上  
  
 您必須在結構宣告上使用 **StructLayout\(LayoutKind.Explicit\)** 屬性 \(如果它包含使用 **FieldOffset** 屬性標記的任何成員\)。 如需詳細資訊，請參閱 [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic)。  
  
 下列範例會產生 CS0636：  
  
```  
// CS0636.cs using System; using System.Runtime.InteropServices; // To resolve the error, uncomment the following line: // [StructLayout(LayoutKind.Explicit)] struct Worksheet { [FieldOffset(4)]public int i;   // CS0636 } public class MainClass { public static void Main () { } }  
```