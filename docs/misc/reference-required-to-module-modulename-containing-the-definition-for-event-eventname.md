---
title: "模組 &#39;&lt;模組名稱&gt;&#39; (包含事件 &#39;&lt;事件名稱&gt;&#39; 的定義) 需要參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30006"
  - "bc30006"
helpviewer_keywords: 
  - "BC30006"
ms.assetid: 7ab80acd-b47b-4920-bb15-6a3206b984e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模組 &#39;&lt;模組名稱&gt;&#39; (包含事件 &#39;&lt;事件名稱&gt;&#39; 的定義) 需要參考
模組 '\<`modulename`\>' \(包含事件 '\<`eventname`\>' 的定義\) 需要參考。 請在專案中加入一個參考。  
  
 此事件是在專案中未直接參考的模組中所定義。[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器需要參考，以避免當事件在多個模組中定義時所發生的模稜兩可情況。  
  
 **錯誤 ID︰**BC30006  
  
### 更正這個錯誤  
  
-   請在您的專案參考中包含未參考之模組的名稱。  
  
## 請參閱  
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)