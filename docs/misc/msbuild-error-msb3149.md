---
title: "MSBuild 錯誤 MSB3149 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3149
**MSB3149: 沒有可用來建置啟動載入器的資源。**  
  
 如果找不到符合任何文化特性的啟動載入器資源檔 \(setup.xml\)，就會發生這個錯誤訊息。  
  
### 若要更正這個錯誤  
  
-   移至 \[**控制台**\]，選取 \[**新增或移除程式**\]，然後修復 Visual Studio SDK，或者將檔案複製到適當的目錄 \(\<SDK install path\>\\bootstrapper\\engine\\\<culture\>\\setup.xml\)。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)