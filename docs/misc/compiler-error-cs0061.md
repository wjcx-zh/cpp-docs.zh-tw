---
title: "編譯器錯誤 CS0061 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0061"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0061"
ms.assetid: 8dfc57a9-653d-4902-a88c-92032ba64024
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0061
不一致的存取範圍: 基底介面 'interface 1' 比介面 'interface 2' 的存取範圍小  
  
 [公用](../Topic/public%20\(C%23%20Reference\).md)建構必須傳回可公開存取的物件。  
  
 不能縮小衍生介面中的介面存取範圍。 如需詳細資訊，請參閱 [介面](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md) 與 [存取修飾詞](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0061。  
  
```  
// CS0061.cs // compile with: /target:library internal interface A {} public interface AA : A {}  // CS0061 // OK public interface B {} internal interface BB : B {} internal interface C {} internal interface CC : C {}  
```