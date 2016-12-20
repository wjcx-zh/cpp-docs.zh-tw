---
title: "MSBuild 錯誤 MSB3188 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3188
**MSB3188: 組件 '\<assembly\>' 必須經過強式簽署才能標記成必要條件。**  
  
 當必要組件未經強式簽署時，就會產生這個錯誤訊息。  只有應用程式資訊清單會產生這個錯誤訊息。  
  
### 若要更正這個錯誤  
  
-   確認專案所使用的所有組件都經過強式簽署。