---
title: "編譯器錯誤 CS0415 | Microsoft Docs"
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
  - "CS0415"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0415"
ms.assetid: 1ed45b02-4568-4af4-b2a6-c8b01230d19a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0415
'IndexerName' 屬性只在非明確介面成員宣告的索引子上有效  
  
 如果您在明確介面實作的索引子上使用 IndexerName 屬性，就會發生這個錯誤。 請盡可能從索引子的宣告中移除介面名稱，以避免發生這個錯誤。 如需詳細資訊，請參閱 [IndexerNameAttribute 類別](frlrfSystemRuntimeCompilerServicesIndexerNameAttributeClassTopic)。  
  
 下列範例會產生 CS0415：  
  
```  
// CS0415.cs using System; using System.Runtime.CompilerServices; public interface IA { int this[int index] { get; set; } } public class A : IA { [IndexerName("Item")]  // CS0415 int IA.this[int index] // Try this line instead: // public int this[int index] { get { return 0; } set { } } static void Main() { } }  
```