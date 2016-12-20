---
title: "MSBuild 錯誤 MSB3154 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
helpviewer_keywords: 
  - "MSB3154"
ms.assetid: 513b70fa-15f5-4137-bdbc-5974607fb75a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3154
**MSB3154: 找不到項目 '\<package\>' 的字串資源。**  
  
 如果指定的套件沒有包含任何文化特性資訊，就會產生這個錯誤訊息。  若不是 package.xml 檔不存在，就是檔案沒有包含 `Culture` 屬性。  
  
### 若要更正這個錯誤  
  
-   提供包含了正確 `Culture` 標記的有效 package.xml 檔。