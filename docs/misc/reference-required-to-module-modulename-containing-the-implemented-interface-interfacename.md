---
title: "模組 &#39;&lt;模組名稱&gt;&#39; 需要的參考包含實作介面 &#39;&lt;介面名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc30010"
  - "bc30010"
helpviewer_keywords: 
  - "BC30010"
ms.assetid: 57fe7e15-bf99-49d1-ba6c-bb7abeb615b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模組 &#39;&lt;模組名稱&gt;&#39; 需要的參考包含實作介面 &#39;&lt;介面名稱&gt;&#39;
模組 '\<模組名稱\>' 需要的參考包含實作介面 '\<介面名稱\>'。 請在專案中加入一個參考。  
  
 此介面是在專案中未直接參考的模組中所定義。[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器需要參考，以避免當介面在多個模組中定義時所發生的模稜兩可情況。  
  
 **錯誤識別碼：**BC30010  
  
### 更正這個錯誤  
  
-   請在您的專案參考中包含未參考之模組的名稱。  
  
## 請參閱  
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)