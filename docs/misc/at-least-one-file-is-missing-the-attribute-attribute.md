---
title: "At least one file is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_file_attrib"
ms.assetid: 2627974b-c9cd-4d85-9af4-dd3811214ea4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one file is missing the &#39;attribute&#39; attribute
從 .vbproj 或 .csproj 檔案讀取的檔案節點遺漏專案系統所需的某個屬性。  目前，這類屬性 \(Attribute\) 只有 `RelPath` 屬性 \(Attribute\)，而這個屬性 \(Attribute\) 會指定檔案位於專案資料夾底下的什麼位置。  
  
 最可能導致這個錯誤的原因是以手動方式編輯專案檔。  
  
 **若要更正這個錯誤**  
  
-   從專案檔移除受影響的檔案節點。  此外，如果檔案仍在磁碟上，您可以切換至 \[**顯示所有檔案**\] 模式 \(按一下 \[方案總管\] 工作列中的按鈕\)，然後以滑鼠右鍵按一下受影響的檔案並選取 \[**加入至專案**\]。  
  
     任何遺漏了 `RelPath` 屬性 \(Attribute\) 的檔案將不會加入至專案。  
  
## 請參閱  
 [專案檔](../ide/project-files.md)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)