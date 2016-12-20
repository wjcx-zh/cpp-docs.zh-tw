---
title: "MSBuild 錯誤 MSB3163 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidComponentsLocation"
helpviewer_keywords: 
  - "MSB3163"
ms.assetid: 35c5efbf-2fd7-478c-bb8e-3c4eabb3e4d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3163
**MSB3163: 建置輸入參數 'ComponentsLocation\='\<ComponentsLocation\>'' 無效。  這個值必須是 'HomeSite'、'Relative' 或 'Absolute' 其中一個。  預設為 'HomeSite'。**  
  
 當 `ComponentsLocation` 屬性 \(安裝必要條件的位置\) 的指定值無效時，就會發生這個錯誤。  `ComponentsLocation` 的值應該是下列三個的其中一個：`HomeSite`、`Relative` 或 `Absolute`。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)