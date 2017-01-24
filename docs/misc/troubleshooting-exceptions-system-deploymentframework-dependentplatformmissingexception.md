---
title: "疑難排解例外狀況：System.DeploymentFramework.DependentPlatformMissingException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DependentPlatformMissingException 類別, 疑難排解"
ms.assetid: fee1ca1c-0f0b-483b-b8ab-3743dfdda038
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.DeploymentFramework.DependentPlatformMissingException
應用程式依存於用戶端未安裝的組件時，就會擲回 `T:System.DeploymentFramework.DependentPlatformMissingException` 例外狀況。 可能的原因包括錯誤的作業系統，或是部署應用程式的電腦上 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 版本錯誤所造成。  
  
## 相關秘訣  
 **請檢查目標電腦上已安裝應用程式所需的所有組件。**  
 嘗試使用 Windows Installer 的每個安裝作業，一開始都會檢查使用者的電腦上是否已存有這個安裝程式，如果沒有的話，便會檢查電腦是否已準備安裝 Windows Installer。  
  
## 請參閱  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)