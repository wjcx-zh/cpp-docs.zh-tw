---
title: "無法將檔案 &#39;file&#39; 加入專案中。 &lt;原因&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法將檔案 &#39;file&#39; 加入專案中。 &lt;原因&gt;
無法將讀取自 .vbproj 或 .csproj 檔案的檔案加入專案中。 原因包括：  
  
-   檔名無效。  
  
-   路徑中的檔案。 例如，若您有 File1\\File2.txt 的專案相對路徑，但也有一個包含相對路徑 File1\\File2.txt 的資料夾。  
  
-   項目已存在。 當檔案在專案中重複列出時，就會發生此情況。  
  
-   連結已存在。[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 與 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 專案系統的限制在於，每個專案只能包含一個具有相同名稱的連結。 舉例來說，這表示專案的資料夾 A 和資料夾 B 中不能同時包含 file.vb 的連結。  
  
 此錯誤很可能是因為手動編輯專案而導致。  
  
 此診斷所顯示的任何檔案都不會加入專案中。  
  
## 請參閱  
 [專案檔](../ide/project-files.md)   
 [NIB：專案中的項目管理](http://msdn.microsoft.com/zh-tw/762e606b-7f44-4b66-97a1-e30a703654a0)