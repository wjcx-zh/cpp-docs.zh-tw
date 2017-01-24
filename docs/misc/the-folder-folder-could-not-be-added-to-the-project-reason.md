---
title: "The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt;
無法將從 .vbproj 或 .csproj 檔案讀取的資料夾加入至專案。  原因包括：  
  
-   無效的名稱  
  
-   路徑中的檔案。  例如，如果您有一個專案相對路徑 Folder1\\Folder2\\Folder3，但還有一個具有相對路徑 Folder1\\Folder2 的檔案。  
  
-   項目已存在。  如果資料夾在專案檔中列出兩次，就會出現這個錯誤。  
  
 最可能導致這個錯誤的原因是以手動方式編輯專案檔。  
  
 **若要更正這個錯誤**  
  
-   從專案檔移除受影響的資料夾節點。  
  
     出現這項診斷的任何資料夾和此資料夾下的任何檔案，都不會被加入至專案。  
  
## 請參閱  
 [專案檔](../ide/project-files.md)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)