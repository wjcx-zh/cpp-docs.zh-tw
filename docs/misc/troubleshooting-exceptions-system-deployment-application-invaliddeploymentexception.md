---
title: "疑難排解例外狀況：System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "InvalidDeploymentException 類別"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Deployment.Application.InvalidDeploymentException
應用程式本身或其應用程式和部署資訊清單無效時，就會擲回 <xref:System.Deployment.Application.InvalidDeploymentException> 例外狀況。  
  
## 相關秘訣  
 **請確定這個應用程式的資訊清單有效。**  
 所謂應用程式資訊清單，就是說明並識別共用和私用並存組件的 XML 檔，這些並存組件是應用程式要在執行時間加以繫結的組件。 並存組件的版本必須與用來測試應用程式的組件版本相同。 應用程式資訊清單可能也會說明應用程式私用檔案的中繼資料。  
  
 **使用 ClickOnce 功能部署應用程式。**  
 使用 ClickOnce 將 Windows 應用程式發行至 Web 伺服器或與簡易安裝共用的網路檔。 如需詳細資訊，請參閱[ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)。  
  
## 請參閱  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [疑難排解 ClickOnce 部署](../Topic/Troubleshooting%20ClickOnce%20Deployments.md)   
 [Windows Form 的 ClickOnce 部署](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)