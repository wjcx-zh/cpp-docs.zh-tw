---
title: "疑難排解例外狀況：System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DeploymentDownloadException 類別"
  - "應用程式部署 [C#]，DeploymentDownloadException 類別"
  - "部署應用程式 [C#]，DeploymentDownloadException 類別"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.DeploymentFramework.DeploymentDownloadException
正在下載應用程式更新時發生任何種類的網路例外狀況時，就會發生 `T:System.DeploymentFramework.DeploymentDownloadException`。  
  
## 相關秘訣  
 **檢查 InnerException，以判斷基礎的 System.Net 或 System.IO 例外狀況。**  
 正在下載應用程式更新時產生網路例外狀況，就會發生這個例外狀況。 請檢查例外狀況的 <xref:System.Exception.InnerException%2A> 屬性，以判斷基礎的例外狀況。  
  
## 請參閱  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)