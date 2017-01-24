---
title: "MSBuild 錯誤 MSB1019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.InvalidLoggerError"
helpviewer_keywords: 
  - "MSB1019"
ms.assetid: 5d0169f7-f878-433a-ac30-d9d6010130af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1019
**記錄器參數的格式不正確。**  
  
 所指定的 **\/logger** 參數不正確。  若要指定記錄器，您至少必須提供記錄器組件，或者如果您想要明確指定要載入哪一個記錄器，則必須提供記錄器類別和記錄器組件。  記錄器參數是選擇性參數。  
  
### 若要更正這個錯誤  
  
1.  同時使用記錄器類別和記錄器組件來指定記錄器。  `<logger>` 語法是：  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     `<logger class>` 語法是：  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     `<logger assembly>` 語法是：  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     `<logger parameters>` 是選擇項，並且會確實以您輸入的內容傳遞給記錄器。  
  
     範例：\/`logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)   
 [組建記錄器](../Topic/Build%20Loggers.md)