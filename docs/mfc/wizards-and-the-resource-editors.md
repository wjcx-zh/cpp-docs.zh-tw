---
title: "精靈和資源編輯器 | Microsoft Docs"
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
  - "應用程式精靈 [C++], 與 MFC"
  - "類別檢視工具, 管理 Windows 訊息"
  - "編輯器, 資源"
  - "MFC [C++], 資源編輯器"
  - "MFC [C++], 精靈"
  - "MFC 應用程式精靈"
  - "資源編輯器, MFC"
  - "精靈 [C++], MFC 程式設計"
  - "精靈 [MFC]"
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 精靈和資源編輯器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 程式設計，與許多等位資源編輯器搭配 MFC 包括數個精靈可供使用。  對於程式設計的 ActiveX 控制項， [ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md) 符合目的很像 MFC 應用程式精靈。  當您撰寫 MFC 應用程式，而不用大部分工具時，工具大幅簡化並加速您的工作。  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> 使用 MFC 應用程式精靈建立 MFC 應用程式  
 使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md) 建立 Visual C\+\+ 的 MFC 專案，可能包含 OLE 和資料庫支援。  在專案的檔案包含您的應用程式、文件、檢視和框架視窗類別;標準資源，包括功能表和選擇性工具列;其他必要的 Windows 檔案;並選擇性 .rtf 檔包含您可以修改並擴大為程式建立說明檔的標準 Windows 說明主題。  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> 使用類別檢視處理類別和 Windows 訊息  
 類別檢視可以協助您建立視窗訊息的處理常式函式和命令，建立和管理類別，建立類別成員變數，建立自動化方法和屬性，建立資料庫類別等等。  
  
> [!NOTE]
>  也類別檢視說明覆寫 MFC 的虛擬函式進行分類。  選取類別和虛擬函式覆寫。  處理序的其餘部分類似訊息處理常式，如以下各節所述。  
  
 在 Windows 下的應用程式是 [所巡覽的訊息](../mfc/message-handling-and-mapping.md)。  在循序程式原因視窗就會傳送訊息至程式視窗的使用者動作和其他事件。  例如，在中，如果使用者按一下視窗上方時， Windows 會將 `WM_LBUTTONDOWN` 傳送資訊，並按下滑鼠左鍵和 `WM_LBUTTONUP` 訊息時，放開按鈕。  當使用者選取命令從功能表列時，視窗也會傳送 **WM\_COMMAND** 資訊。  
  
 在 MFC 架構，各種物件，例如文件，檢視，框架視窗，文件範本和應用程式物件，可能已處理訊息。  這類物件的「處理常式函式」做為其成員函式之一，因此，架構會將傳入訊息傳送至其處理常式。  
  
 對應的訊息至的物件來實作該對應您的程式設計工作的一個主要選取。  若要這麼做，您可以使用類別檢視和屬性視窗。  
  
 屬性視窗會建立空的訊息處理常式成員函式，因此，您使用原始程式碼編輯器實作處理常式的主體。  您也可以建立或編輯類別 \(從 MFC 類別，不是衍生的包含類別\) 及其有類別檢視的成員。  如需使用類別檢視的詳細資訊以及與精靈會在專案中加入程式碼，請參閱 [將與程式碼精靈的功能](../ide/adding-functionality-with-code-wizards-cpp.md)。  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> 使用資源編輯器建立和編輯資源  
 使用 Visual C\+\+ [資源編輯器](../mfc/resource-editors.md) 來建立和編輯功能表、對話方塊、自訂控制項、快速鍵、點陣圖、圖示、游標、字串和釋放資源。  根據 Visual C\+\+ 4.0 版，工具列編輯器讓建立工具列更加容易。  
  
 為了協助您， MFC 程式庫提供呼叫 COMMON.RES 的檔案，包含「美工圖案」資源可以從 COMMON.RES 和貼上複製到您的資源檔。  COMMON.RES 包括工具列按鈕、通用資料指標，圖示等。  您可以在應用程式中使用，修改和轉散發這些資源。  如需 COMMON.RES 的詳細資訊，請參閱 [Clipart 範例](../top/visual-cpp-samples.md)。  
  
 MFC 應用程式精靈、Visual C\+\+ 精靈、資源編輯器和 MFC 架構會執行大量工作並使管理您的程式碼更容易。  大部分應用程式專屬的程式碼在文件和檢視類別。  
  
## 請參閱  
 [使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)