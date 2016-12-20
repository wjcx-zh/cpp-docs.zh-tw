---
title: "A failure occurred writing to the licenses file | Microsoft Docs"
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
  - "vs.tasklisterror.fail_writing_licenses_file"
ms.assetid: 7ea1e2ac-fc94-4d53-8ce9-2ae31bcba85d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# A failure occurred writing to the licenses file
專案系統無法寫入轉換的檔案。  專案系統會將文字檔 .licx 轉換為 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 授權系統可以解讀的二進位授權檔，當做準備授權的一部分。  
  
 這個錯誤的可能原因包括裝置上已沒有可用的磁碟空間或檔案名稱已超過 MAX\_PATH 的限制。  
  
 **若要更正這個錯誤**  
  
-   將專案移至具有短絕對路徑名稱的其他資料夾或縮短輸出檔名稱。  
  
     如果發生這種錯誤，建置處理序將無法完成。  
  
## 請參閱  
 [如何：授權元件和控制項](../Topic/How%20to:%20License%20Components%20and%20Controls.md)