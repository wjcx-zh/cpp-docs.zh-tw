---
title: "MSBuild 錯誤 MSB3144 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3144
**MSB3144: 提供的資料不足以產生啟動載入器。  請至少為下列其中一項提供值: 'ApplicationFile' 或 'BootstrapperItems'。**  
  
 如果提供的資料不足以產生啟動載入器，就會發生這個錯誤訊息。  建置處理序會建立不具有應用程式安裝程式和套件的空白啟動載入器。  
  
### 若要更正這個錯誤  
  
-   至少為 `ApplicationFile` 或 `BootstrapperItems` 其中一項參數提供值。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)