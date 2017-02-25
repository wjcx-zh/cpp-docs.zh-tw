---
title: "專案建置警告 PRJ0049 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0049"
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 專案建置警告 PRJ0049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

參考的目標 '\<Reference\>' 需要 .NET Framework \<MinFrameworkVersion\>，如果以此專案的目標 Framework 執行將會失敗  
  
 使用 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 建立的應用程式可以指定他們目標的 [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] 版本。  如果在相依於 [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] 版本的組件或專案中，加入比目標版本還要新的參考，就會在編譯時期收到這個警告。  
  
### 若要更正此警告  
  
1.  選擇下列其中一項：  
  
    -   在專案的 \[**屬性頁**\] 對話方塊中變更目標 Framework，讓它比所有參考的組件和專案的最小 Framework 版本還要新或是一樣。  如需詳細資訊，請參閱[加入參考](../../ide/adding-references-in-visual-cpp-projects.md)。  
  
    -   移除最小 Framework 版本比目標 Framework 還要新的組件或專案的參考。  這些項目在專案的 \[**屬性頁**\] 中會標示為警告圖示。  
  
## 請參閱  
 [專案組建錯誤和警告 \(PRJxxxx\)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)