---
title: "特殊 CWinApp 服務 | Microsoft Docs"
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
  - "LoadStdProfileSettings"
  - "EnableShellOpen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式物件 [C++], 服務"
  - "CWinApp 類別, 檔案管理員拖放"
  - "CWinApp 類別, 初始化 GDI+"
  - "CWinApp 類別, 最近使用的文件"
  - "CWinApp 類別, 服務"
  - "CWinApp 類別, Shell 註冊"
  - "拖放 [C++], 檔案"
  - "DragAcceptFiles 方法"
  - "EnableShellOpen 方法"
  - "檔案 [C++], 拖放"
  - "檔案 [C++], 最近使用的"
  - "GDI+, 針對 MFC 初始化"
  - "GDI+, 隱藏背景執行緒 [MFC]"
  - "LoadStdProfileSettings 方法"
  - "MFC [C++], 檔案作業"
  - "MFC [C++], 最近使用的檔案清單"
  - "MFC [C++], Shell 註冊"
  - "MRU 清單"
  - "註冊檔案類型"
  - "RegisterShellFileTypes 方法"
  - "註冊 [C++], Shell"
  - "登錄 [C++], 最近使用的檔案"
  - "服務, CWinApp 提供的"
  - "Shell, 註冊檔案類型"
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
caps.latest.revision: 10
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 特殊 CWinApp 服務
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了執行訊息以外的迴圈，並讓您有機會初始化應用程式並在之後清除， [CWinApp](../mfc/reference/cwinapp-class.md) 提供數個其他服務。  
  
##  <a name="_core_shell_registration"></a> Shell 註冊  
 根據預設， MFC 應用程式精靈可讓使用者可以開啟資料檔應用程式藉由按兩下建立在檔案總管或文件管理員。  如果您的應用程式是 MDI 應用程式，而且您指定檔案的副檔名為應用程式建立， MFC 應用程式精靈將呼叫 [RegisterShellFileTypes](../Topic/CWinApp::RegisterShellFileTypes.md) ，而 [EnableShellOpen](../Topic/CWinApp::EnableShellOpen.md) 的 [CWinApp](../mfc/reference/cwinapp-class.md) 成員函式對 `InitInstance` 的覆寫它為您撰寫。  
  
 `RegisterShellFileTypes` 註冊您的應用程式中與檔案總管或文件管理員的文件類型。  將項目加入至視窗中維護的登入資料庫。  輸入註冊每個資料型別，使副檔名和檔案類型，指定命令列開啟應用程式，並指定動態資料交換 \(DDE\) \(DDE\) 命令開啟該類型的文件。  
  
 `EnableShellOpen` 可讓您的應用程式完成處理序會從檔案總管或文件管理員的 DDE 命令開啟使用者所選取的檔案。  
  
 在 `CWinApp` 的這個自動登入支援不需要傳輸將應用程式的 .reg 檔案或完成的安裝工作。  
  
 如果您要初始化應用程式的 GDI\+ \(透過中呼叫 [InitInstance](../Topic/CWinApp::InitInstance.md) 函式的 [GdiplusStartup](_gdiplus_FUNC_GdiplusStartup_token_input_output_) \)，您必須隱藏 GDI\+ 背景執行緒。  
  
 您可以透過設定 [GdiplusStartupInput](_gdiplus_STRUC_GdiplusStartupInput) 結構的 **SuppressBackgroundThread** 成員達成此 **TRUE**。  當隱藏 GDI\+ 背景執行緒時，應該在輸入和關閉應用程式的訊息迴圈之前呼叫 **NotificationHook** 和 **NotificationUnhook** 呼叫 \(請參閱 [GdiplusStartupOutput](_gdiplus_STRUC_GdiplusStartupOutput)\)。  因此，好呼叫 **GdiplusStartup** 的和告知攔截函式在虛擬函式 [CWinApp::Run](../Topic/CWinApp::Run.md)的覆寫，如下所示:  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/CPP/special-cwinapp-services_1.cpp)]  
  
 如果您不要隱藏 GDI\+ 背景執行緒， DDE 命令可以提早發行至應用程式，在其主視窗之前建立。  Shell 發出的 DDE 命令可以提前中止，造成錯誤訊息。  
  
##  <a name="_core_file_manager_drag_and_drop"></a> 檔案管理員拖放  
 檔案可以從文件管理員的檔案檢視或 Windows 檔案總管拖曳至應用程式的視窗。  您可能，例如，使一或多個檔案拖曳到 MDI 應用程式的主視窗，應用程式可以擷取檔案名稱和開啟檔案的 MDI 子視窗。  
  
 若要啟用應用程式的檔案拖放， MFC 應用程式精靈的 [CWnd](../mfc/reference/cwnd-class.md) 成員函式 [DragAcceptFiles](../Topic/CWnd::DragAcceptFiles.md) 寫入呼叫您的主框架視窗中的 `InitInstance`。  如果不要實作拖放功能，您可以移除該呼叫。  
  
> [!NOTE]
>  您也可以實作多個一般拖放功能拖曳資料之間或內資料與 OLE。  如需詳細資訊，請參閱本文件的 [拖放 \(Object Linking and Embedding，OLE\)](../mfc/drag-and-drop-ole.md)。  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> 記錄最近使用的檔案  
 因為使用者開啟和關閉檔案，應用程式物件記錄四個最近使用的檔案。  這些檔案名稱加入至檔案功能表並更新其何時變更。  當應用程式啟動時，架構會儲存這些檔案名稱在登錄或在 .ini 檔案，使用名稱與專案名稱相同且讀到檔案。  MFC 應用程式精靈為您建立的 `InitInstance` 覆寫包含呼叫包含最近使用的檔案名稱的 [CWinApp](../mfc/reference/cwinapp-class.md) 成員函式，從 [LoadStdProfileSettings](../Topic/CWinApp::LoadStdProfileSettings.md)註冊或 .ini 檔案載入資訊。  
  
 儲存這些項目如下：  
  
-   在 Windows NT、 Windows 2000 以及之後的版本，值儲存至登錄機碼。  
  
-   在 Windows 3.x，值在 WIN.INI 檔案中。  
  
-   在 Windows 95 \(含\) 以後版本中，值在 WIN.INI 快取版本中。  
  
## 請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)