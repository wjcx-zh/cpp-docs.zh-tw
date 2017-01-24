---
title: "MSBuild 錯誤 MSB3179 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ComImport"
helpviewer_keywords: 
  - "MSB3179"
ms.assetid: fa744f6c-e398-4e60-b4f7-455ace7e3bd2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3179
**MSB3179: 隔離的 COM 參考 '\<assembly\>' 時發生問題: '\<error\>'**  
  
 這是泛型錯誤訊息，指出在應用程式資訊清單 \(如 `IsolatedComReferences` 工作參數所指定\) 中產生 RegFree COM 項目時發生了問題。  這個錯誤訊息的後半部包含了更詳細的資訊，以描述此問題的性質。  發生這個錯誤可能是因為沒有在建置電腦上正確地註冊 RegFree COM 元件。  
  
### 若要更正這個錯誤  
  
-   確認建置電腦上已經註冊了所有 COM 元件。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)