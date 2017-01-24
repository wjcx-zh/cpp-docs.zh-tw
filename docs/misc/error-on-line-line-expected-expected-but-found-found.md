---
title: "Error on line &lt;line&gt;. Expected &#39;expected&#39; but found &#39;found&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_lineerr"
ms.assetid: d78934c9-6d57-42b2-9968-2b0aa4bf05e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error on line &lt;line&gt;. Expected &#39;expected&#39; but found &#39;found&#39;
這是在讀取專案檔時發生的一般 XML 剖析錯誤。  這個錯誤會發生在專案檔 \(.vbproj\/.csproj\) 和個別使用者的設定檔 \(.vbproj.user\/.csproj.user\) 上。  專案系統將在參數 `expected` 和 `found` 中提供更詳細的資訊。  
  
 最可能導致這個錯誤的原因是以手動方式編輯專案 \(或使用者\) 檔案。  
  
 **若要更正這個錯誤**  
  
-   再次編輯專案檔案並且將專案檔案還原成令人滿意的條件。  
  
     您能否開啟該專案，須視錯誤的嚴重性而定。  
  
## 請參閱  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)