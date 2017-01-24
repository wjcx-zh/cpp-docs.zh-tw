---
title: "編譯器警告 (層級 1) CS0658 | Microsoft Docs"
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
  - "CS0658"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0658"
ms.assetid: 0309074c-741a-492c-9370-73b4bbfd3c1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0658
'attribute modifier' 不是可辨識的屬性位置。 將會忽略此區塊中的所有屬性。  
  
 指定的屬性修飾詞無效。 如需詳細資訊，請參閱[屬性目標](http://msdn.microsoft.com/zh-tw/59a261f0-1cfb-4aa5-b610-6b735389882c)。  
  
 下列範例會產生 CS0658：  
  
```  
// CS0658.cs using System; public class TestAttribute : Attribute{} [badAttributeLocation: Test]   // CS0658, badAttributeLocation is invalid class ClassTest { public static void Main() { } }  
```