---
title: "The user options settings file for this project is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.peruserfile_sectionerr"
ms.assetid: 576070f5-76b6-46e4-8aba-83442521027f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The user options settings file for this project is missing the &#39;section&#39; section
.vbproj.user 或 .csproj.user 檔案遺漏  Build 節點。  
  
 Build 區段內含偵錯設定。  如果此區段遺失，您的偵錯設定便不會載入，且將採用預設值。  
  
 最可能導致這個情況的原因是以手動方式編輯專案檔。  
  
 專案系統在專案關閉時將自動重新寫入每位使用者的專案檔中。  
  
 這屬於資訊警告。  
  
## 請參閱  
 [專案檔](../ide/project-files.md)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)