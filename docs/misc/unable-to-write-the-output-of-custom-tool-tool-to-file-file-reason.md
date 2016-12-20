---
title: "Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt;
專案系統無法將自訂工具的輸出寫入至指定的檔案。  
  
 若自訂工具輸入的檔名維持不變，自訂工具的輸出會寫入相同檔案。  如果所產生的輸出鎖定在磁碟上，就會出現這種錯誤。  
  
 **若要更正這個錯誤**  
  
-   請以滑鼠右鍵按一下受影響的檔案並從捷徑功能表選取 \[**執行自訂工具**\]，如此便可重新啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 並重新執行自訂工具。  
  
     因為專案系統無法加以更新，所產生的檔案可能已經過期了。