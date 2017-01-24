---
title: "編譯器錯誤 CS0276 | Microsoft Docs"
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
  - "CS0276"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0276"
ms.assetid: 0c49017f-c7a9-42a5-9d0a-6f1d82142bd7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0276
'property\/indexer': 存取子上的存取範圍修飾詞，只能使用於屬性或索引子同時有 get 和 set 存取子的情況  
  
 如果您宣告僅有一個存取子的屬性或索引子，並在存取子上使用存取修飾詞，則會發生這個錯誤。 若要解決，請移除存取修飾詞，或加入另一個存取子。  
  
## 範例  
 下列範例會產生 CS0276：  
  
```  
// CS0276.cs public class MyClass { public int Property { protected set { }   // CS0276 } public int Property2 { internal get { }   // CS0276 } }  
```