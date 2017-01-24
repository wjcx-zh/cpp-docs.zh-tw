---
title: "無法將多檔案組件元件 &#39;component_filename&#39; 複製至檔案 &#39;destination_filename&#39;。 &lt;原因。&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannotcopyscattercomponent"
ms.assetid: 22f851fc-431b-4cdf-9de1-3a29727fa1e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法將多檔案組件元件 &#39;component_filename&#39; 複製至檔案 &#39;destination_filename&#39;。 &lt;原因。&gt;
指定的元件未複製到 bin 目錄。  
  
 部分組件包含多個檔案。 每當多檔案組件中的檔案無法複製到執行目錄時，會顯示此診斷。  
  
 可能有多種原因會造成失敗。 例如，磁碟空間不足，或是達到路徑長度的 MAX\_PATH 限制。 此外，處理程序 \(或許是 Visual Studio\) 中，可能會緊抓無法複製的元件。  
  
 **更正這個錯誤**  
  
-   檢查是否有足夠的可用磁碟空間。  
  
-   請嘗試將專案移動至路徑長度小於目前專案資料夾路徑長度的資料夾。  
  
-   將輸出目錄變更為具有較小絕對路徑長度的資料夾。 這僅適用於用戶端 \(非 Web\) 專案。  
  
-   重新啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
## 請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../Topic/Debugging%20Web%20Applications:%20Errors%20and%20Troubleshooting.md)