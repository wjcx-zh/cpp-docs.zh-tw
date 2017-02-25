---
title: "如何：加入重新啟動管理員支援 | Microsoft Docs"
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
  - "重新啟動管理員"
  - "C++, 應用程式損毀支援"
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 如何：加入重新啟動管理員支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重新啟動管理員是一項加入 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] for [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] 的功能。 重新啟動管理員會在應用程式意外關閉或重新啟動時加入支援。 重新啟動管理員的行為，取決於應用程式的類型。 如果應用程式是文件編輯器，重新啟動管理員可讓應用程式自動儲存任何已開啟文件的狀態和內容，而且在意外關閉之後重新啟動應用程式。 如果應用程式不是文件編輯器，則重新啟動管理員預設會重新啟動應用程式，但不會儲存應用程式的狀態。  
  
 如果應用程式是 Unicode，則應用程式會在重新啟動之後顯示工作對話方塊。 如果是 ANSI 應用程式，則應用程式會顯示 Windows 訊息方塊。 此時，使用者可以選擇是否要還原自動儲存的文件。 如果使用者不要還原自動儲存的文件，則重新啟動管理員會捨棄暫存檔案。  
  
> [!NOTE]
>  您可以覆寫重新啟動管理員的預設行為，以便儲存資料和重新啟動應用程式。  
  
 根據預設，當應用程式在具有 [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] 的電腦上執行時，使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的專案精靈建立的 MFC 應用程式可支援重新啟動管理員。 如果您不想讓應用程式支援重新啟動管理員，可以在新的專案精靈中停用重新啟動管理員。  
  
### 將重新啟動管理員的支援加入現有的應用程式  
  
1.  在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中開啟現有的 MFC 應用程式。  
  
2.  開啟主應用程式的原始程式檔。 根據預設，這是與應用程式同名的 .cpp 檔。 例如，MyProject 的主應用程式原始程式檔為 MyProject.cpp。  
  
3.  尋找主應用程式的建構函式。 例如，專案若為 MyProject，建構函式則為 `CMyProjectApp::CMyProjectApp()`。  
  
4.  將下面這行程式碼加入建構函式。  
  
    ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
    ```  
  
5.  確保應用程式的 `InitInstance` 方法會呼叫其父 `InitInstance` 方法：[CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md) 或 `CWinAppEx::InitInstance`。`InitInstance` 方法負責檢查 `m_dwRestartManagerSupportFlags` 參數。  
  
6.  編譯並執行您的應用程式。  
  
## 請參閱  
 [CDataRecoveryHandler Class](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m\_dwRestartManagerSupportFlags](../Topic/CWinApp::m_dwRestartManagerSupportFlags.md)   
 [CWinApp Class](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m\_nAutosaveInterval](../Topic/CWinApp::m_nAutosaveInterval.md)   
 [CDocument::OnDocumentEvent](../Topic/CDocument::OnDocumentEvent.md)