---
title: "MSBuild 錯誤 MSB3177 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.AllowPartiallyTrustedCallers"
helpviewer_keywords: 
  - "MSB3177"
ms.assetid: 0b2417d5-3bc3-4169-b69c-a4a3cbf47882
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3177
**MSB3177: 參考 '\<reference\>' 不允許部分信任的呼叫端。**  
  
 如果應用程式是部分信任的應用程式，並且如果 *reference* 已加入當做專案參考、具有強式名稱 \(Strong Name\)，而且沒有 APTCA 屬性 \(Attribute\)，就會在應用程式資訊清單產生期間產生這個警告訊息。  
  
### 若要更正這個錯誤  
  
-   請將 APTCA 屬性加入至參考的組件，或者如果此方法不可行，請停止使用它。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)