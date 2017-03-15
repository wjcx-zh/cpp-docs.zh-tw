---
title: "說明檔 (WinHelp) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案類型 [C++], WinHelp 檔案"
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 說明檔 (WinHelp)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您在 MFC 應用程式精靈的 [進階功能](../mfc/reference/advanced-features-mfc-application-wizard.md) 頁面選取 \[即時線上說明\] 核取方塊，然後選取 \[WinHelp 格式\] 將說明支援的 WinHelp 類型加入至應用程式時，會建立下列檔案。  
  
|檔案名稱|目錄位置|方案總管位置|描述|  
|----------|----------|------------|--------|  
|*Projname*.hpj|*Projname*\\hlp|原始程式檔|說明專案檔，是說明編譯器用來建立您的程式或控制項的說明檔。|  
|*Projname*.rtf|*Projname*\\hlp|說明檔|包含您可編輯的範本主題以及自訂 .hpj 檔的資訊。|  
|*Projname*.cnt|*Projname*\\hlp|說明檔|提供 Windows 說明的 \[**內容**\] 視窗結構。|  
|Makehelp.bat|*Projname*|原始程式檔|當編譯專案時，系統用來建置說明專案的檔案。|  
|Print.rtf|*Projname*\\hlp|說明檔|在您專案包含列印支援的情況下建立 \(預設值\)。  描述列印命令和對話方塊。|  
|\*.bmp|*Projname*\\hlp|資源檔|包含不同產生說明檔主題的影像。|  
  
 您可在 MFC ActiveX 控制項精靈的 [應用程式設定](../mfc/reference/application-settings-mfc-activex-control-wizard.md) 索引標籤 中選取 \[產生說明檔\] 將 WinHelp 支援加入至 MFC ActiveX 控制項專案。  當您將說明支援加入至 MFC ActiveX 控制項時，下列檔案也會加入至專案：  
  
|檔案名稱|目錄位置|方案總管位置|描述|  
|----------|----------|------------|--------|  
|*Projname*.hpj|*Projname*\\hlp|原始程式檔|專案檔，說明編譯器用來建立程式或控制項的說明檔。|  
|*Projname*.rtf|*Projname*\\hlp|專案|包含您可編輯的範本主題以及自訂 .hpj 檔的資訊。|  
|Makehelp.bat|*Projname*|原始程式檔|當編譯專案時，系統用來建置說明專案的檔案。|  
|Bullet.bmp|*Projname*|資源檔|標準說明檔主題用來表示項目符號清單的檔案。|  
  
## 請參閱  
 [為 Visual C\+\+ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)