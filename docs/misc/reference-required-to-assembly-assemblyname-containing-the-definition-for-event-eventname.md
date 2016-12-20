---
title: "組件 &#39;&lt;組件名稱&gt;&#39; (包含事件 &#39;&lt;事件名稱&gt;&#39; 的定義) 需要參考 | Microsoft Docs"
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
  - "vbc30005"
  - "bc30005"
helpviewer_keywords: 
  - "BC30005"
ms.assetid: 843b0b2f-0f93-41c3-8727-13a2138e8140
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 組件 &#39;&lt;組件名稱&gt;&#39; (包含事件 &#39;&lt;事件名稱&gt;&#39; 的定義) 需要參考
組件 '\<`assemblyname`\>' \(包含事件 '\<`eventname`\>' 的定義\) 需要參考。 請將參考加入您的專案中。  
  
 此事件是在專案中未直接參考的動態連結程式庫 \(DLL\) 或組件中所定義。[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器需要參考，以避免當事件在多個 DLL 或組件中定義時所發生的模稜兩可情況。  
  
 **錯誤 ID︰**BC30005  
  
### 更正這個錯誤  
  
-   在您的專案參考中包含未參考之 DLL 或組件的名稱。  
  
## 請參閱  
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)