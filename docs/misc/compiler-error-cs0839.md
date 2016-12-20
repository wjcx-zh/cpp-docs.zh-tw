---
title: "編譯器錯誤 CS0839 | Microsoft Docs"
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
  - "CS0839"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0839"
ms.assetid: 6f2f1062-8551-4125-8880-68bfbfbcf061
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0839
遺漏引數。  
  
 在方法呼叫中遺漏引數。  
  
### 更正這個錯誤  
  
1.  請再檢查一次方法的簽章，並找到和提供遺漏的引數。  
  
## 範例  
 下列範例會產生 CS0839：  
  
```  
// cs0839.cs using System; namespace TestNamespace { class Test { static int Add(int i, int j) { return i + j; } static int Main() { int i = Test.Add( , 5); // CS0839 return 1; } } }  
```