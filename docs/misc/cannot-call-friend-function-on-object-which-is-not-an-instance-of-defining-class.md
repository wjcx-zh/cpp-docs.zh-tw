---
title: "無法在不是定義類別執行個體的物件上呼叫 Friend 函式 | Microsoft Docs"
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
  - "vbrID97"
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法在不是定義類別執行個體的物件上呼叫 Friend 函式
可能是您嘗試呼叫類別的 `Friend` 程序，或嘗試存取跨處理序或跨執行緒的 `Friend` 屬性或方法。`Friend` 程序可以從類別外部的模組呼叫，但其為已定義類別之專案的一部分。  
  
### 更正這個錯誤  
  
-   確定您從屬於已定義類別之專案的模組，呼叫或存取程序。  
  
## 請參閱  
 [Friend](../Topic/Friend%20\(Visual%20Basic\).md)