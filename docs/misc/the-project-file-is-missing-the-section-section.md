---
title: "The project file is missing the &#39;section&#39; section | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_sectionerr"
ms.assetid: 516ab410-1b73-4539-9654-6323af6135b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file is missing the &#39;section&#39; section
.vbproj 或 .csproj 檔案已損毀。  遺漏下列其中一個區段：  
  
-   建置  
  
-   檔案  
  
-   VisualStudio  
  
-   VisualBasic 或 CSHARP  
  
 如果 VisualStudio、VisualBasic 或 CSHARP 區段遺漏時，專案將不載入。  如果 Build 或 Files 區段遺漏時，專案檔將如下所述地載入：  
  
-   如果 Build 遺漏，所有建置設定和組態資訊都將遺失。  
  
-   如果 Files 遺漏，專案中將沒有檔案。  
  
 **若要更正這個錯誤**  
  
-   重新建立您的專案。  
  
## 請參閱  
 [專案檔](../ide/project-files.md)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)