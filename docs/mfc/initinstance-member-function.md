---
title: "InitInstance 成員函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式 [MFC], 初始化"
  - "初始化 MFC 應用程式"
  - "InitInstance 方法"
  - "MFC [C++], 初始化"
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InitInstance 成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows 作業系統允許執行多個複製或「執行個體」，相同的應用程式。  在應用程式中建立新的執行個體啟動時，`WinMain` 會呼叫 [InitInstance](../Topic/CWinApp::InitInstance.md) 。  
  
 MFC 應用程式精靈所建立的標準 `InitInstance` 實作會執行下列工作:  
  
-   為中的作用，建立會建立文件、檢視和框架視窗的文件範本。  如需這個程序的說明，請參閱 [資料範本建立。](../mfc/document-template-creation.md)。  
  
-   從一個 .ini 檔案或 Windows 登錄的載入標準檔案選項，包括最近使用的檔案名稱。  
  
-   註冊一個或多個資料範本。  
  
-   對於 MDI 應用程式，建立一個主框架視窗。  
  
-   處理命令列會在命令列上指定的檔案或開啟新，空的文件。  
  
 您可以將自己的初始化程式碼或修改精靈所撰寫的程式碼。  
  
> [!NOTE]
>  MFC 應用程式必須設定為單一執行緒 Apartment \(STA\)。  如果您在 `InitInstance` 覆寫中呼叫 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) ，請指定 `COINIT_APARTMENTTHREADED` \(而不是 `COINIT_MULTITHREADED`\)。  如需詳細資訊，請參閱 \<PRB:MFC 應用程式停止回應，當您使用應用程式設定為單一執行多執行緒 Apartment \(828643\) 中 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;828643](http://support.microsoft.com/default.aspx?scid=kb;en-us;828643)。  
  
## 請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)