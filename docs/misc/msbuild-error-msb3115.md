---
title: "MSBuild 錯誤 MSB3115 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidEntryPoint"
helpviewer_keywords: 
  - "MSB3115"
ms.assetid: 7d9d4156-fd6a-455a-8a3d-b191485f1294
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3115
**MSB3115: 檔案 '\<file\>' 不是有效的進入點。**  
  
 當資訊清單指定了無效的進入點時，就會產生這個錯誤訊息。  
  
### 若要更正這個錯誤  
  
-   確認在資訊清單中指定有效的進入點。  如果是應用程式資訊清單，有效的進入點是 .exe 檔案。  如果是部署資訊清單，則有效的進入點是應用程式資訊清單。