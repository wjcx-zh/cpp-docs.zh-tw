---
title: "MSBuild 錯誤 MSB3111 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ConfigBindingRedirectsWithPartialTrust"
helpviewer_keywords: 
  - "MSB3111"
ms.assetid: f01286a1-ba27-4733-a431-35ffe9a31356
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3111
**MSB3111: 需要完全信任，才能使用 app.config 繫結重新導向。**  
  
 如果建置處理序偵測到應用程式試圖將它的某些組件重新導向至 app.config 檔內的另一個版本，就會產生這個警告訊息。  這並不適用於部分信任應用程式。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)