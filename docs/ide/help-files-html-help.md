---
title: "說明檔 (HTML 說明) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案類型 [C++], HTML 說明檔"
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 說明檔 (HTML 說明)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您在 MFC 應用程式精靈的[進階功能](../mfc/reference/advanced-features-mfc-application-wizard.md)頁面選取 \[即時線上說明\] 核取方塊，然後選取 \[HTML 說明格式\] 來將說明支援的 HTML 類型加入至應用程式時，會建立下列檔案。  
  
|檔案名稱|目錄位置|方案總管位置|描述|  
|----------|----------|------------|--------|  
|*Projname*.hhp|*Projname*\\hlp|HTML 說明檔|說明專案檔。  它包含將說明檔編譯為 .hxs 檔或 .chm 檔所需的資料。|  
|*Projname*.hhk|*Projname*\\hlp|HTML 說明檔|包含說明主題的索引。|  
|*Projname*.hhc|*Projname*\\hlp|HTML 說明檔|說明專案的內容。|  
|Makehtmlhelp.bat|*Projname*|原始程式檔|當編譯專案時，系統用來建置說明專案的檔案。|  
|Afxcore.htm|*Projname*\\hlp|HTML 說明主題|包含標準 MFC 命令和螢幕物件的標準說明主題。  將您自己的說明主題加入至這個檔案。|  
|Afxprint.htm|*Projname*\\hlp|HTML 說明主題|包含列印命令列的說明主題。|  
|\*.jpg；\*.gif|*Projname*\\hlp\\Images|資源檔|包含不同產生說明檔主題的影像。|  
  
## 請參閱  
 [為 Visual C\+\+ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)