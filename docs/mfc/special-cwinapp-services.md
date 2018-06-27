---
title: 特殊 CWinApp 服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd6af2ab524711c591772c28ed47742e6aa406ad
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955868"
---
# <a name="special-cwinapp-services"></a>特殊 CWinApp 服務
除了執行訊息迴圈，並讓您有機會初始化應用程式和之後，清除[CWinApp](../mfc/reference/cwinapp-class.md)提供數個其他服務。  
  
##  <a name="_core_shell_registration"></a> Shell 註冊  
 根據預設，MFC 應用程式精靈可讓使用者在檔案總管或檔案管理員中，按兩下開啟您的應用程式所建立的資料檔案。 如果您的應用程式是 MDI 應用程式，而且您指定您的應用程式建立的檔案副檔名，MFC 應用程式精靈將呼叫新增至[RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes)和[EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen)的成員函式[CWinApp](../mfc/reference/cwinapp-class.md)至`InitInstance`為您的覆寫。  
  
 `RegisterShellFileTypes` 將您的應用程式的文件類型註冊於檔案總管或檔案管理員。 此函式會將項目加入至 Windows 維護的註冊資料庫。 項目會註冊每個文件類型，將副檔名與檔案類型建立關聯，指定命令列以開啟應用程式，並指定動態資料交換 (DDE) 命令以開啟該類型的文件。  
  
 `EnableShellOpen` 可讓您的應用程式接收來自檔案總管或檔案管理員的 DDE 命令，以開啟使用者選擇的檔案，來完成處理序。  
  
 `CWinApp` 中的此項自動註冊支援，不需要以應用程式傳輸 .reg 檔案或執行特殊安裝工作。  
  
 如果您想要初始化 GDI + 您的應用程式 (藉由呼叫[Initinstance](https://msdn.microsoft.com/library/ms534077)中您[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)函式)，您必須隱藏 GDI + 背景執行緒。  
  
 您可以藉由設定`SuppressBackgroundThread`隸屬[Suppressbackgroundthread](https://msdn.microsoft.com/library/ms534067)結構以**TRUE**。 當隱藏 GDI + 背景執行緒，`NotificationHook`和`NotificationUnhook`呼叫應該要對先前只進入和退出應用程式的訊息迴圈。 如需有關這些呼叫的詳細資訊，請參閱[GdiplusStartupOutput](https://msdn.microsoft.com/library/ms534068)。 因此，若要呼叫的好地方`GdiplusStartup`與攔截通知函式會在虛擬函式的覆寫[cwinapp:: Run](../mfc/reference/cwinapp-class.md#run)，如下所示：  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]  
  
 如果您不要隱藏背景 GDI+ 執行緒，DDE 命令可以在其主視窗建立之前提早發行至應用程式。 殼層發出的 DDE 命令可能會提前中止，造成錯誤訊息。  
  
##  <a name="_core_file_manager_drag_and_drop"></a> 檔案管理員拖放  
 檔案可以從 [檔案管理員] 或 [檔案總管] 中的檔案檢視拖曳至應用程式中的視窗。 比方說，您可以將一個或多個檔案拖曳到 MDI 應用程式的主視窗，使應用程式可以在此擷取檔案名稱和開啟這些檔案的 MDI 子視窗。  
  
 若要啟用檔案拖放在您的應用程式中，MFC 應用程式精靈會將呼叫[CWnd](../mfc/reference/cwnd-class.md)成員函式[DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles)主框架視窗中您`InitInstance`。 如果不要實作拖放功能，您可以移除該呼叫。  
  
> [!NOTE]
>  您也可以實作多個一般拖放功能，在文件內或之間以 OLE 拖曳資料。 如需資訊，請參閱文章[拖放 (OLE)](../mfc/drag-and-drop-ole.md)。  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> 追蹤的最最近使用過的文件  
 使用者開啟和關閉檔案時，應用程式物件會記錄最近四個最常使用的檔案。 這些檔案名稱會新增至 [檔案] 功能表，當檔案變更時則會更新。 架構會使用與專案相同的名稱將這些檔案名稱儲存在登錄或 .ini 檔案中，並在應用程式啟動時從檔案讀取這些名稱。 `InitInstance`覆寫 MFC 應用程式精靈建立包含呼叫[CWinApp](../mfc/reference/cwinapp-class.md)成員函式[LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings)，從登錄或.ini 載入資訊檔案，包括最近使用的檔案名稱。  
  
 這些項目儲存如下：  
  
-   在 Windows NT、Windows 2000 和更新版本中，值會儲存到登錄機碼。  
  
-   在 Windows 3.x 中，值會儲存到 WIN.INI 檔案中。  
  
-   在 Windows 95 和更新版本中，值會儲存到快取版本的 WIN.INI 中。  
  
## <a name="see-also"></a>另請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)