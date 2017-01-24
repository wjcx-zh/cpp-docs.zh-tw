---
title: "&#39;&lt;名稱&gt;&#39; 不可以透過其預設執行個體參考自身，請使用 &#39;Me&#39; 代替 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31139"
  - "bc31139"
helpviewer_keywords: 
  - "BC31139"
ms.assetid: 459e5d5a-d526-4cd0-934e-96e4e1eb51bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;名稱&gt;&#39; 不可以透過其預設執行個體參考自身，請使用 &#39;Me&#39; 代替
已嘗試從表單內參考該表單作為預設執行個體。 這可能會導致表單遞迴地呼叫它自己。  
  
 在大多數情況下，您應該在參考表單的目前執行個體時使用 `Me`，而非使用預設執行個體。  
  
 **錯誤 ID︰**BC31139  
  
### 更正這個錯誤  
  
-   使用 `Me` 來參考物件。  
  
## 請參閱  
 [偵錯工具基礎](../Topic/Debugger%20Basics.md)