---
title: "編譯器錯誤 CS0277 | Microsoft Docs"
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
  - "CS0277"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0277"
ms.assetid: 8abec3eb-4d4c-4aab-87cc-d0444ab23535
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0277
'類別' 未實作介面成員 '存取子'， 因為 '類別存取子' 並非公用  
  
 當您嘗試實作介面的屬性，但類別中屬性存取子的實作不是公用時，就會發生這個錯誤。 實作介面成員的方法必須具有公用存取範圍。 若要解決，請移除屬性存取子上的存取修飾詞。  
  
## 範例  
 下列範例會產生 CS0277：  
  
```  
// CS0277.cs public interface MyInterface { int Property { get; set; } } public class MyClass : MyInterface   // CS0277 { public int Property { get { return 0; } // Try this instead: //set { } protected set { } } }  
```