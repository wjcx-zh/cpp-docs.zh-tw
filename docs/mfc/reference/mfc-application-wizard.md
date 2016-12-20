---
title: "MFC 應用程式精靈 | Microsoft Docs"
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
  - "vc.appwiz.mfc.exe.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "可執行檔, 建立"
  - "MFC 應用程式精靈"
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 應用程式精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 應用程式精靈產生的應用程式可於編譯時實作 Windows 可執行檔 \(.exe\) 應用程式的基本功能。  MFC 起始應用程式包括 C\+\+ 來源檔 \(.cpp\)、資源檔 \(.rc\)、標題檔 \(.h\) 以及專案檔 \(.vcxproj\)。  起始檔案 \(Starter File\) 中所產生的程式碼是以 MFC 為基礎。  
  
> [!NOTE]
>  根據所選取的選項，精靈會在專案中建立額外的檔案。  例如，您在[進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)頁面中選取 \[**即時線上說明**\]，精靈就會建立編譯專案說明檔時必要的檔案。  如需精靈建立檔案的詳細資訊，請參閱[為 Visual C\+\+ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)，並參閱專案中的 Readme.txt 檔案。  
  
## 概觀  
 本精靈頁面說明目前正在建立的 MFC 應用程式之應用程式設定。  在預設情況下，精靈會如下建立專案：  
  
-   [MFC 應用程式精靈、應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   專案建立為具有索引標籤式多重文件介面 \(MDI\) 支援。  如需詳細資訊，請參閱[SDI 和 MDI](../../mfc/sdi-and-mdi.md)。  
  
    -   這個專案使用[文件\/檢視架構](../../mfc/document-view-architecture.md)。  
  
    -   專案使用 Unicode 程式庫。  
  
    -   專案是使用 Visual Studio 專案樣式建立，會啟用視覺化樣式切換。  
  
    -   專案在共用 DLL 使用 MFC。  如需詳細資訊，請參閱[Visual C\+\+ 中的 DLL](../../build/dlls-in-visual-cpp.md)。  
  
-   [MFC 應用程式精靈、複合文件支援](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   專案不提供複合文件支援。  
  
-   [MFC 應用程式精靈、文件樣板字串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   專案會使用專案名稱做為預設的文件樣板字串。  
  
-   [MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   專案不提供資料庫支援。  
  
-   [MFC 應用程式精靈、使用者介面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   專案實作標準 Windows 使用者介面功能，例如系統功能表、狀態列、最大化和最小化方塊、\[**關於**\] 方塊、標準功能表列和停駐工具列，以及子框架。  
  
-   [MFC 應用程式精靈、進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   專案支援列印和預覽列印。  
  
    -   專案支援 ActiveX 控制項。  如需詳細資訊，請參閱[建立 ActiveX 控制項的作業順序](../../mfc/sequence-of-operations-for-creating-activex-controls.md)。  
  
    -   專案不支援 [Automation](../../mfc/automation.md)、[MAPI](../../mfc/mapi-support-in-mfc.md)、[Windows Sockets](../../mfc/windows-sockets-in-mfc.md) 或 Active Accessibility。  
  
    -   專案支援 \[**總管停駐窗格**\]、\[**輸出停駐窗格**\] 和 \[**屬性停駐窗格**\]。  
  
-   [MFC 應用程式精靈、產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   專案的檢視類別是衍生自 [CView Class](../../mfc/reference/cview-class.md)。  
  
    -   專案的應用程式類別是衍生自 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)。  
  
    -   專案的文件類別是衍生自 [CDocument Class](../../mfc/reference/cdocument-class.md)。  
  
    -   專案的主框架類別是衍生自 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)。  
  
    -   專案的子框架類別是衍生自 [CMDIChildWndEx 類別](../../mfc/reference/cmdichildwndex-class.md)。  
  
 若要變更這些預設值，請按一下精靈左欄中的適當索引標籤標題，並於出現的頁面上進行變更。  
  
 在您建立 MFC 應用程式專案後，可使用 Visual C\+\+ [程式碼精靈](../../ide/adding-functionality-with-code-wizards-cpp.md)在專案中加入物件或控制項。  
  
## 請參閱  
 [建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)   
 [MFC 桌面應用程式](../../mfc/mfc-desktop-applications.md)   
 [使用類別來編寫 Windows 應用程式](../../mfc/using-the-classes-to-write-applications-for-windows.md)