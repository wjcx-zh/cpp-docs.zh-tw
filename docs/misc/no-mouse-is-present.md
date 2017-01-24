---
title: "滑鼠不存在 | Microsoft Docs"
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
  - "vbrMouse_NoMouseIsPresent"
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 滑鼠不存在
已呼叫 `My.Computer.Mouse` 物件的其中一個屬性，但是電腦未安裝滑鼠或滑鼠連接埠。  
  
### 更正這個錯誤  
  
-   在 `My.Computer.Mouse` 物件的屬性呼叫周圍加入 `Try...Catch` 區塊。  
  
     — 或 —  
  
-   在電腦上安裝滑鼠。  
  
## 請參閱  
 [My.Computer.Mouse Object](../Topic/My.Computer.Mouse%20Object.md)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)