---
title: "疑難排解例外狀況：System.Deployment.DependentPlatformMissingException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DependentPlatformMissingException 類別"
ms.assetid: 2343eb4f-f23f-4b6c-a65c-1f93c3e6ea36
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Deployment.DependentPlatformMissingException
嘗試在不相容的電腦上執行應用程式時，就會擲回 `T:System.Deployment.DependentPlatformMissingException` 例外狀況。 在目標電腦上安裝錯誤的作業系統或錯誤版本的 .NET Framework 時，就可能會產生這個例外狀況。  
  
## 相關秘訣  
 **請確定目標電腦上已經安裝了應用程式所需的所有組件。**  
 嘗試使用 Windows Installer 的每個安裝作業，一開始都會檢查使用者的電腦上是否已存有這個安裝程式，如果沒有的話，便會檢查電腦是否已準備安裝 Windows Installer。  
  
## 請參閱  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)