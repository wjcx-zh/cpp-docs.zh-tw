---
title: "滑鼠滾輪不存在 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoWheelIsPresent"
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 滑鼠滾輪不存在
已呼叫 `My.Computer.Mouse.WheelScrollLines` 屬性，但是滑鼠有沒有滾輪。  
  
### 更正這個錯誤  
  
-   請檢查 `My.Computer.Mouse.WheelExists` 屬性看看滑鼠是否有滾輪，然後再呼叫 `My.Computer.Mouse.WheelScrollLines` 屬性。  
  
     \-或\-  
  
-   在電腦上安裝有滾輪的滑鼠。  
  
## 請參閱  
 [My.Computer.Mouse.WheelScrollLines 屬性](http://msdn.microsoft.com/zh-tw/67600f96-25d7-4dd9-946a-b46e1fc6a57f)   
 [My.Computer.Mouse.WheelExists 屬性](http://msdn.microsoft.com/zh-tw/332d44f7-0b66-4eaa-b4ce-d7f161bfbd07)   
 [Visual Basic 中的例外狀況和錯誤處理](http://msdn.microsoft.com/zh-tw/3e351e73-cf23-40ab-8b60-05794160529e)