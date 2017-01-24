---
title: "MSBuild 錯誤 MSB1007 | Microsoft Docs"
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
  - "MSBuild.MissingLoggerError"
helpviewer_keywords: 
  - "MSB1007"
ms.assetid: bf45dbc3-50cd-488a-87df-9e647cd71f10
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB1007
**指定記錄器。**  
  
 必須指定 **\/logger** 參數的記錄器。  
  
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
  
     以下是幾個 **\/logger** 參數的範例：  
  
     `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
     `/logger:XMLLogger,C:\Loggers\MyLogger.dll`  
  
     `/logger:XMLLogger,..  \Loggers\MyLogger.dll;OutputAsHTML`  
  
## 請參閱  
 [Command\-Line Reference](../Topic/MSBuild%20Command-Line%20Reference.md)