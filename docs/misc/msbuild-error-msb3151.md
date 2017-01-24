---
title: "MSBuild 錯誤 MSB3151 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
helpviewer_keywords: 
  - "MSB3151"
ms.assetid: e4766734-2e90-436e-850b-a8a9da535dee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3151
**MSB3151: 項目 '\<package\>' 已經包含 '\<package\>'。**  
  
 如果您選取了兩個啟動載入器套件，其中一個套件包含在另一個套件中 \(例如，選取包含的套件是多餘的\)，就會發生這個警告訊息。  
  
### 若要更正這個錯誤  
  
-   清除多餘套件的核取方塊。