---
title: "&#39;&lt;方法1&gt;&#39; 和 &#39;&lt;方法2&gt;&#39; 無法互相多載，因為它們的差異只在於傳回類型不同而已。 | Microsoft Docs"
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
  - "bc30301"
  - "vbc30301"
helpviewer_keywords: 
  - "BC30301"
ms.assetid: 5adc442b-9671-4d93-add8-42929b1a09b9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 和 &#39;&lt;方法2&gt;&#39; 無法互相多載，因為它們的差異只在於傳回類型不同而已。
您已嘗試將某個方法多載另一個方法，後者只有傳回類型和前者不同。 在多載中，您必須藉引數清單區分任何兩個版本的方法；除了引數清單，沒有任何其他項目可以區別方法。  
  
 **錯誤識別碼：**BC30301  
  
### 更正這個錯誤  
  
-   請確定方法是以其引數清單區分。  
  
## 請參閱  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Considerations in Overloading Procedures](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)