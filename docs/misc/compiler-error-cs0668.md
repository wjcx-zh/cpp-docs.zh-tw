---
title: "編譯器錯誤 CS0668 | Microsoft Docs"
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
  - "CS0668"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0668"
ms.assetid: 7bdaa795-ce13-4284-b753-a617c1735cfa
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0668
兩個索引子具有不同的名稱; 類型中每個索引子上都必須使用同名的 IndexerName 屬性。  
  
 傳遞給 **IndexerName** 屬性的值必須對於類型中的所有索引子都相同。 如需有關 **IndexerName** 屬性的詳細資訊，請參閱 [IndexerNameAttribute 類別](frlrfSystemRuntimeCompilerServicesIndexerNameAttributeClassTopic)。  
  
 下列範例會產生 CS0668：  
  
```  
// CS0668.cs using System; using System.Runtime.CompilerServices; class IndexerClass { [IndexerName("IName1")] public int this [int index]   // indexer declaration { get { return index; } set { } } [IndexerName("IName2")] public int this [string s]    // CS0668, change IName2 to IName1 { get { return int.Parse(s); } set { } } void Main() { } }  
```