---
title: "MSBuild 錯誤 MSB3022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3022
**"'\<attribute\>'" 及 "'\<attribute\>'" 在專案檔中都指定為輸入參數。  請選擇使用其中一個。**  
  
 使用 `Copy` 工作時，您必須指定 `DestinationFiles` 或 `DestinationDirectory`，但不能同時指定這兩個工作屬性。  
  
### 若要更正這個錯誤  
  
-   在專案檔中，為 `Copy` 工作指定 `DestinationFiles` 或 `DestinationDirectory` 屬性。  
  
## 請參閱  
 [Copy Task](../Topic/Copy%20Task.md)   
 [工作](../Topic/MSBuild%20Tasks.md)