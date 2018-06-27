---
title: 精靈和資源編輯器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db1b807856baf4cab3cdef57092cd29fdff3a19d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951136"
---
# <a name="wizards-and-the-resource-editors"></a>精靈和資源編輯器
Visual c + + MFC 程式設計，以及許多整合式的資源編輯器中包含數個精靈，供使用。 對 ActiveX 控制項的程式設計， [ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)用途很像，MFC 應用程式精靈。 雖然您可以撰寫 MFC 應用程式，這些工具大部分都沒有，工具將可大幅簡化和加速您的工作。  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> 使用 MFC 應用程式精靈建立 MFC 應用程式  
 使用[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立 Visual c + + 中，其中可以包括 OLE 以及資料庫支援的 MFC 專案。 專案中的檔案包含您的應用程式、 文件、 檢視和框架視窗類別。標準資源，包括功能表和選擇性的工具列。其他所需的 Windows 檔案。並選擇性.rtf 檔案包含標準 Windows 說明主題，您可以修訂和強化來建立您的程式說明檔。  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> 使用類別檢視管理類別和 Windows 訊息  
 類別檢視可協助您建立的 Windows 訊息和命令處理函式，建立並管理類別，建立類別的成員變數、 建立 Automation 方法和屬性、 建立資料庫類別等等。  
  
> [!NOTE]
>  類別檢視也可協助您覆寫虛擬函式中的 MFC 類別。 選取類別並覆寫虛擬函式。 以下段落中所述相似與訊息處理程序的其餘部分。  
  
 在 Windows 下執行的應用程式是[訊息導向](../mfc/message-handling-and-mapping.md)。 使用者動作和其他正在執行的程式中所發生的事件會導致將訊息傳送至 windows 程式中的 Windows。 例如，如果使用者按一下滑鼠在視窗中的，Windows 會傳送 WM_LBUTTONDOWN 訊息時按下滑鼠左鍵和 WM_LBUTTONUP 訊息生於放開按鍵時。 當使用者從功能表列選取命令時，Windows 也會傳送 WM_COMMAND 訊息。  
  
 在 MFC 架構中，各種物件，例如文件、 檢視、 框架視窗、 文件範本和應用程式物件，可以 「 處理 」 訊息。 這類物件提供 「 處理常式函數 」 做為其中一個其成員函式，並 framework 會將內送訊息對應至其處理常式。  
  
 大部分的程式設計工作所選擇哪些訊息来對應到哪些物件，然後實作該對應。 若要這樣做，您可以使用類別檢視和 [屬性] 視窗。  
  
 [屬性] 視窗將會建立空的訊息處理常式成員函式，以及您使用原始碼程式碼編輯器來實作的處理常式的本文。 您也可以建立或編輯類別 （包括不從 MFC 類別衍生您自己的類別） 和使用類別檢視其成員。 如需使用類別檢視 和精靈加入程式碼加入專案的相關資訊，請參閱[使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)。  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> 使用資源編輯器來建立和編輯資源  
 使用 Visual c + +[資源編輯器](../windows/resource-editors.md)建立和編輯功能表、 對話方塊、 自訂控制項、 快速鍵、 點陣圖、 圖示、 游標、 字串和版本資源。 自 Visual c + + 4.0 版，工具列編輯器使建立工具列更為容易。  
  
 為了協助您更多，Mfc 程式庫會提供一個稱為一般檔案。RES，包含 「 美工圖案 」 資源，您可以從一般複製。RES 並貼上到您自己的資源檔。 常見的。RES 包括工具列按鈕、 常見的資料指標、 圖示和多個。 您可以使用、 修改和重新發佈應用程式中的這些資源。 如需常見的詳細資訊。RES，請參閱[美工圖案範例](../visual-cpp-samples.md)。  
  
 MFC 應用程式精靈、 Visual c + + 精靈、 資源編輯器和 MFC 架構為您執行許多工作，以管理您的程式碼更容易。 大部分的應用程式專屬的程式碼是在您的文件和檢視類別中。  
  
## <a name="see-also"></a>另請參閱  
 [使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)
