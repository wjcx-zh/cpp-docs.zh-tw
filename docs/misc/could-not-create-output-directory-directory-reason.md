---
title: "Could not create output directory &#39;directory&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_create_output_dir"
ms.assetid: b4d1d19f-f582-49d0-a9a9-d3f4ce0a447b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not create output directory &#39;directory&#39;. &lt;reason&gt;
專案系統無法建立專案目錄。  
  
 一旦開啟專案，專案系統將試圖建立所有輸出目錄。  以下為由專案系統所建立的輸出目錄清單：  
  
 *projectfolder*\\obj\\`configname`  
 暫存的特定組態輸出目錄。  
  
 *projectfolder*\\obj\\`configname`\\temp  
 編譯器 \(Compiler\) 所使用的工作區。  
  
 *projectfolder*\\obj\\`configname`\\temppe  
 設計工具在設計階段所使用的暫存組件會在此處建立。  
  
 outputdir  
 Output Path 屬性 \(Property\) 所指定的目錄。  如需詳細資訊，請參閱[專案設計工具、建置頁 \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)。  
  
 無法在 \[obj\] 資料夾下建立目錄的最常見原因是因為超過目錄名稱的 MAX\_PATH 限制。  
  
 較不常見的原因還包括使用權限遭拒和磁碟空間不足。  
  
 **若要更正這個錯誤**  
  
-   如果路徑太長，則變更專案位置或縮短專案組態的名稱。  
  
     如果發生這種錯誤，建置處理序將無法完成。  
  
## 請參閱  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)