---
title: "在 &#39;MyClass&#39; 之後必須跟隨 &#39;.&#39; 及一個識別項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32028"
  - "vbc32028"
helpviewer_keywords: 
  - "BC32028"
ms.assetid: a7e92b54-32b8-4072-9576-632942f05e0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;MyClass&#39; 之後必須跟隨 &#39;.&#39; 及一個識別項
`MyClass` 不是真正的物件變數，因此不能單獨出現。 您僅可以使用它來存取目前執行個體的成員，就像它是基底類別中的 `NotOverridable` 一樣。  
  
 **錯誤 ID︰**BC32028  
  
### 更正這個錯誤  
  
1.  如果您想要存取類別成員，請在 `MyClass` 之後指定成員存取運算子 \(`.`\) 和目前執行個體的成員。  
  
2.  如果您不想要存取類別成員，請使用 `Me` 關鍵字。  
  
## 請參閱  
 [MyClass \- delete](http://msdn.microsoft.com/zh-tw/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [我](http://msdn.microsoft.com/zh-tw/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)