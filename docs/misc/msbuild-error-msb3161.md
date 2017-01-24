---
title: "MSBuild 錯誤 MSB3161 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CircularDependency"
helpviewer_keywords: 
  - "MSB3161"
ms.assetid: 2871d071-7c3a-4103-8b14-6ee56564a7f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3161
**MSB3161: 在下列建置套件之間偵測到循環相依性: '\<package\>'**  
  
 如果啟動載入器套件相依性的圖形中有循環相依性 \(例如：A→B→C→A\)，就會產生這個警告訊息。  在這種情況下，啟動載入器無法判斷要先安裝哪一個套件。  
  
### 若要更正這個錯誤  
  
-   變更啟動載入器套件檔案中所描述的相依性，或者不要安裝其中一個互相依存的套件，藉此方式移除循環相依性。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)   
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)