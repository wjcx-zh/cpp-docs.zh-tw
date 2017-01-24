---
title: "Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.resource_naming_conflict"
ms.assetid: 50d656ad-8557-4240-95b0-3f44b9c21da6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39;
專案系統計算出有兩個檔案的組件資源名稱相同，這兩個檔案的 `BuildAction` 屬性都設定為 `EmbeddedResource`，且其文化特性是中性。  如果發生這種錯誤，建置處理序將無法完成。  如需 `BuildAction` 屬性的詳細資訊，請參閱 [File Properties](http://msdn.microsoft.com/zh-tw/013c4aed-08d6-4dce-a124-ca807ca08959)。  
  
 因為 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 沒有以資料夾為基礎的命名空間 \(Namespace\) 概念，所以下列資源檔名稱：  
  
-   Proj1\\FolderA\\MyProj.bmp  
  
-   Proj1\\FolderB\\MyProj.bmp  
  
 將為上述兩個檔案產生 Proj1.MyProj.bmp 的組件資訊清單 \(Assembly Manifest\) 名稱。  
  
 **若要更正這個錯誤**  
  
-   如果要解決這個問題，請重新命名受影響的資源檔 \(*file1* and *file2*\)。  
  
## 請參閱  
 [NIB: Resource File Naming Conventions](http://msdn.microsoft.com/zh-tw/7b1a2cdf-6196-4034-8fc7-51a271842cc2)