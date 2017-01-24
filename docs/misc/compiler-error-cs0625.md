---
title: "編譯器錯誤 CS0625 | Microsoft Docs"
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
  - "CS0625"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0625"
ms.assetid: 44091813-9988-436c-b35e-e24094793782
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0625
'field': 有 StructLayout\(LayoutKind.Explicit\) 標記的執行個體欄位類型必須有 FieldOffset 屬性  
  
 使用明確 **StructLayout** 屬性標記結構時，結構中的所有欄位都必須有 [FieldOffset](frlrfsystemruntimeinteropservicesfieldoffsetattributeclasstopic) 屬性。 如需詳細資訊，請參閱 [StructLayoutAttribute 類別](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic)。  
  
 下列範例會產生 CS0625：  
  
```  
// CS0625.cs // compile with: /target:library using System; using System.Runtime.InteropServices; [StructLayout(LayoutKind.Explicit)] struct A { public int i;   // CS0625 not static; an instance field } // OK [StructLayout(LayoutKind.Explicit)] struct B { [FieldOffset(5)] public int i; }  
```