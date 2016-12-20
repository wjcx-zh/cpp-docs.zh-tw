---
title: "MSBuild 錯誤 MSB3148 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoOutputPath"
helpviewer_keywords: 
  - "MSB3148"
ms.assetid: 389b335f-5760-4dcc-9146-c52d6d7ac81f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3148
**MSB3148: 組建設定中沒有指定輸出路徑。**  
  
 如果指定了 null 或無效的輸出路徑，例如，如果專案檔中的 `OutputPath=""`，就會發生這個錯誤訊息。  輸出路徑的預設值為 `CurrentDirectory`。  
  
### 若要更正這個錯誤  
  
-   確認 `OutputPath` 不是空白，或者專案檔中沒有這項設定。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)