---
title: "在 &#39;MyBase&#39; 之後必須跟隨 &#39;.&#39; 及一個識別項 | Microsoft Docs"
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
  - "bc32027"
  - "vbc32027"
helpviewer_keywords: 
  - "BC32027"
ms.assetid: 39e5512c-ef1e-46a3-a96c-277ea24bfee2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;MyBase&#39; 之後必須跟隨 &#39;.&#39; 及一個識別項
`MyBase` 不是真正的物件變數，因此不能單獨出現。 您僅可以使用它來存取目前執行個體的基底類別成員。  
  
 **錯誤 ID︰**BC32027  
  
### 更正這個錯誤  
  
-   如果您想要成員存取，請指定成員存取運算子 \(.\) 和基底類別成員 \(在 `MyBase` 後面\)。  
  
-   如果您不想要成員存取，請宣告並初始化基底類別執行個體或移除 `MyBase` 的參考。  
  
## 請參閱  
 [MyBase \- delete](http://msdn.microsoft.com/zh-tw/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)