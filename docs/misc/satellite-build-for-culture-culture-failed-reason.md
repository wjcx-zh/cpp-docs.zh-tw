---
title: "Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt;
無法建置某特定文化特性的附屬組件。  這種錯誤將導致建置處理序失敗。  
  
 出現這個錯誤的原因有二：  
  
1.  系統未安裝 ALINK.EXE。  
  
2.  ALINK.EXE 失敗，但沒有傳回任何延伸的錯誤訊息。  
  
 **若要更正這個錯誤**  
  
-   重新安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或只重新安裝 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)]。  
  
-   當 \<reason\> 回報為「無法啟動組件連結器。  檔案已存在」時，請將產生檔案的 Temp 資料夾 \(例如：C:\\Documents and Settings\\\<user\>\\Local Settings\\Temp\) 清空。  
  
## 請參閱  
 [Al.exe \(組件連結器\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)