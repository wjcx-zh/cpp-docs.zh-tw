---
title: "The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_dependency"
ms.assetid: 1902c0b5-d09d-49b9-8f71-e325f7b9cfd7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The parent file, &#39;file1&#39;, for file &#39;file2&#39; cannot be found in the project file
專案系統找不到對應於檔案的節點。  
  
 將 `DependentUpon` 屬性 \(Attribute\) 加入至 `<File>` 節點，便可在專案檔中保存相依檔案。  例如：  
  
```  
<File  
    RelPath = "Form1.resx"  
    SubType = "Code"  
    BuildAction = "EmbeddedResource"  
    DependentUpon="Form1.vb"  
/>  
```  
  
 在專案階層架構中，這將使 Form1.resx 顯示在 Form1.vb 的下方。  
  
 最可能導致這個錯誤的原因是以手動方式編輯專案檔。  
  
### 若要更正這個錯誤  
  
-   編輯並且更新專案檔。  
  
     受影響的檔案將被加入至專案，但是相依性不會保留。  
  
## 請參閱  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)