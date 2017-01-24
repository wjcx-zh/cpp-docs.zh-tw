---
title: "MSBuild 錯誤 MSB3128 | Microsoft Docs"
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
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3128
**MSB3128：無法簽署 ClickOnce 資訊清單，因為其中包含一個或多個未經雜湊處理的參考。**  
  
 當您發行具有已簽署之資訊清單的應用程式時，所有檔案都必須包含在雜湊中。  
  
### 若要更正這個錯誤  
  
1.  移至 \[**專案設計工具**\] 的 \[**發行**\] 頁。  
  
2.  按一下 \[**應用程式檔案**\]。  
  
3.  針對要發行的所有檔案，將 \[**雜湊**\] 值設定為 \[**包含**\]。  
  
## 請參閱  
 [專案設計工具、發行頁](../Topic/Publish%20Page,%20Project%20Designer.md)