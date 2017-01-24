---
title: "&#39;&lt;方法1&gt;&#39; 和 &#39;&lt;方法2&gt;&#39; 無法互相多載，因為它們的差異只在於選擇性參數不同。 | Microsoft Docs"
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
  - "vbc30300"
  - "bc30300"
helpviewer_keywords: 
  - "BC30300"
ms.assetid: adb44ceb-57a0-4123-8fd8-7eb83c3f601f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 和 &#39;&lt;方法2&gt;&#39; 無法互相多載，因為它們的差異只在於選擇性參數不同。
您已嘗試將某個方法多載另一個方法，後者只有選擇性參數和前者不同。 具有選擇性參數的方法相當於兩個多載方法，一個有選擇性參數，另一個則沒有。 因此，方法只要其中之一有對應的引數清單，即無法多載。  
  
 **錯誤 ID：**BC30300  
  
### 更正這個錯誤  
  
-   確定方法的區分方式不只是透過選擇性參數。  
  
## 請參閱  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Considerations in Overloading Procedures](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)