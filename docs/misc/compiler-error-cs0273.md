---
title: "編譯器錯誤 CS0273 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0273"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0273"
ms.assetid: 851ad056-feee-48fd-834c-578a1a13e926
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0273
'property\_accessor' 存取子的存取範圍修飾詞必須比屬性或索引子 'property' 更嚴格  
  
 set\/get 存取子的存取範圍修飾詞必須比屬性或索引子 'property\/indexer' 更嚴格  
  
 當您所宣告之屬性或索引子的存取修飾詞比其中一個存取子上的存取修飾詞較不嚴格時，就會發生這個錯誤。 若要解決這個錯誤，請在屬性或 set 存取子上使用適當的存取修飾詞。 如需詳細資訊，請參閱[存取子的存取範圍](../Topic/Restricting%20Accessor%20Accessibility%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 這個範例包含具有內部 set 方法的內部屬性。 下列範例會產生 CS0273。  
  
```  
// CS0273.cs // compile with: /target:library public class MyClass { internal int Property { get { return 0; } internal set {}   // CS0273 // try the following line instead // private set {} } }  
```