---
title: "MFC 應用程式精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d4997d2d793102119e5021ba1110db2674e1b42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-application-wizard"></a>MFC 應用程式精靈
MFC 應用程式精靈產生應用程式，編譯時，實作 Windows 可執行檔 (.exe) 應用程式的基本功能。 MFC 起始應用程式包括 c + + 來源 (.cpp) 檔案、 資源 (.rc) 檔、 標頭 (.h) 檔案和專案 (.vcxproj) 檔案。 產生起始檔案中的程式碼是以 MFC 為基礎。  
  
> [!NOTE]
>  根據您選取的選項，精靈會建立其他檔案專案中。 例如，如果您選取**即時線上說明**上[進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md) 頁面上，精靈會建立編譯專案的說明檔所需的檔案。 如需精靈建立的檔案的詳細資訊，請參閱[Visual c + + 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)，並查看專案的 Readme.txt 檔案。  
  
## <a name="overview"></a>總覽  
 這個精靈頁面說明 MFC 應用程式所建立的目前應用程式設定。 依預設，此精靈建立專案，如下所示：  
  
-   [MFC 應用程式精靈、應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   具有索引標籤式的多重文件介面 (MDI) 支援在建立專案。 如需詳細資訊，請參閱[SDI 和 MDI](../../mfc/sdi-and-mdi.md)。  
  
    -   專案會使用[文件/檢視架構](../../mfc/document-view-architecture.md)。  
  
    -   專案會使用 Unicode 程式庫。  
  
    -   專案使用 Visual Studio 專案樣式建立，並啟用視覺化樣式切換。  
  
    -   專案會使用 MFC 共用 dll。 如需詳細資訊，請參閱 [Visual C++ 中的 DLL](../../build/dlls-in-visual-cpp.md)。  
  
-   [MFC 應用程式精靈、複合文件支援](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   專案不提供支援複合文件。  
  
-   [MFC 應用程式精靈、文件樣板字串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   專案會使用預設文件樣板字串的專案名稱。  
  
-   [MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   專案不提供支援的資料庫。  
  
-   [MFC 應用程式精靈、使用者介面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   專案會實作標準的 Windows 使用者介面功能，例如系統功能表、 狀態列、 最大化，和最小化 方塊中，**有關**方塊、 標準功能表停駐工具列，以及子框架。  
  
-   [MFC 應用程式精靈、進階功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   專案支援列印和預覽列印。  
  
    -   專案支援 ActiveX 控制項。 如需詳細資訊，請參閱[順序的作業，以建立 ActiveX 控制項](../../mfc/sequence-of-operations-for-creating-activex-controls.md)。  
  
    -   此專案提供了不支援[自動化](../../mfc/automation.md)， [MAPI](../../mfc/mapi-support-in-mfc.md)， [Windows Sockets](../../mfc/windows-sockets-in-mfc.md)，或使用中的協助工具。  
  
    -   專案支援**總管**停駐窗格，**輸出**停駐窗格中，與**屬性**停駐窗格。  
  
-   [MFC 應用程式精靈、產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   專案的檢視類別衍生自[CView 類別](../../mfc/reference/cview-class.md)。  
  
    -   專案的應用程式類別衍生自[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。  
  
    -   專案的文件類別衍生自[CDocument 類別](../../mfc/reference/cdocument-class.md)。  
  
    -   專案的主要畫面格類別衍生自[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)。  
  
    -   專案的子框架類別衍生自[CMDIChildWndEx 類別](../../mfc/reference/cmdichildwndex-class.md)。  
  
 若要變更這些預設設定，按一下精靈左欄中的適當的索引標籤標題，並在出現的頁面上進行變更。  
  
 建立 MFC 應用程式專案之後，您可以將物件或控制項加入您專案中使用 Visual c + +[程式碼精靈](../../ide/adding-functionality-with-code-wizards-cpp.md)。  
  
## <a name="see-also"></a>請參閱  
 [建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)   
 [MFC 桌面應用程式](../../mfc/mfc-desktop-applications.md)   
 [使用類別來編寫 Windows 應用程式](../../mfc/using-the-classes-to-write-applications-for-windows.md)
