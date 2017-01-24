---
title: "編譯器警告 (層級 1) CS0657 | Microsoft Docs"
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
  - "CS0657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0657"
ms.assetid: d12d2efc-f44e-40e6-b825-5a66ead0c08e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0657
'attribute modifier' 不是此宣告的有效屬性位置。 這個宣告的有效屬性位置是 'locations'。 將會忽略此區塊中的所有屬性。  
  
 編譯器在無效的位置中找到屬性修飾詞。 如需詳細資訊，請參閱[屬性目標](http://msdn.microsoft.com/zh-tw/59a261f0-1cfb-4aa5-b610-6b735389882c)。  
  
 下列範例會產生 CS0657：  
  
```  
// CS0657.cs // compile with: /target:library public class TestAttribute : System.Attribute {} [return: Test]   // CS0657 return not valid on a class class Class1 {}  
```