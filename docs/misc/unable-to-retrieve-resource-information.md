---
title: "Unable to retrieve resource information | Microsoft Docs"
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
  - "vs.tasklisterror.resx_scan_failed"
ms.assetid: e4389ff0-eb64-4c31-b32f-5216c73fadfb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to retrieve resource information
掃描 .resx 檔案的階層架構失敗。  
  
 專案系統會掃描所有副檔名為.resx 之檔案的專案階層架構，當做`Preparing resources` \(顯示於 \[**輸出**\] 視窗\) 建置步驟的一部分。  這個動作會產生 .resx XML 檔案的清單，這些檔案需要先轉換為 .resources 二進位檔案，才能包含在專案輸出中做為資源。  
  
 **若要更正這個錯誤**  
  
-   重新啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  如果這樣行不通，請聯絡 Microsoft 產品支援服務來報告這個問題。  
  
     這種錯誤將導致建置失敗。  
  
## 請參閱  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/zh-tw/f793852c-da06-4d52-a826-65f635844772)