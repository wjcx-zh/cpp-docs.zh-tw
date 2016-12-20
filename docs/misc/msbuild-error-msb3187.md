---
title: "MSBuild 錯誤 MSB3187 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3187
**MSB3187: 參考組件'\<assembly\>'以應用程式以外的不同處理器為目標。**  
  
 如果應用程式的目標平台 \(處理器架構\) 設定為中性 \(MSIL\)，但參考組件並不是中性，或者如果應用程式的架構不是中性，但相依性是中性，就會產生這個警告。  同樣地，如果兩者都不是中性平台，那麼它們的架構就必須相符。  此外，應用程式架構與進入點組件架構一定要相符。  
  
### 若要更正這個錯誤  
  
-   確認應用程式的目標平台 \(處理器架構\) 符合所有參考組件以及進入點組件的架構。  
  
## 請參閱  
 [進階編譯器設定對話方塊 \(Visual Basic\)](../Topic/Advanced%20Compiler%20Settings%20Dialog%20Box%20\(Visual%20Basic\).md)   
 [專案設計工具、建置頁 \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)