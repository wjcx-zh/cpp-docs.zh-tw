---
title: 精靈和資源編輯器
ms.date: 11/04/2016
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
ms.openlocfilehash: 5316899b7eb8828847af6d7db95edf3d8ba3822a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265518"
---
# <a name="wizards-and-the-resource-editors"></a>精靈和資源編輯器

Visual c + + 包含數個精靈，用於在 MFC 程式設計中，以及許多的整合式的資源編輯器。 ActiveX 控制項的程式設計中，針對[ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)用途很像，MFC 應用程式精靈。 雖然您可以撰寫 MFC 應用程式，而不需要大部分的這些工具，工具將可大幅簡化和加速您的工作。

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> 使用 MFC 應用程式精靈 建立 MFC 應用程式

使用[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立 Visual c + + 中，可以包括 OLE 和資料庫支援的 MFC 專案。 在專案檔包含您的應用程式、 文件、 檢視和框架視窗類別;標準的資源，包括功能表和選擇性的工具列，其他所需的 Windows 檔案;和選擇性.rtf 檔案包含標準 Windows 說明主題，您可以修改和建立您的程式說明檔的引數。

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> 使用 管理類別與 Windows 訊息的 類別檢視

類別檢視可協助您建立的 Windows 訊息和命令的處理常式函式、 建立和管理的類別，建立類別成員變數、 建立自動化的方法和屬性、 建立資料庫的類別，以及更多內容。

> [!NOTE]
>  類別檢視也可協助您覆寫虛擬函式中的 MFC 類別。 選取類別並覆寫虛擬函式。 下列段落中所述，此程序的其餘部分是類似於訊息處理。

在 Windows 下執行的應用程式都[驅動的訊息](../mfc/message-handling-and-mapping.md)。 使用者動作和其他執行中的程式中發生的事件會導致將訊息傳送至 windows 程式中的 Windows。 比方說，如果使用者按一下滑鼠，在視窗中的，Windows 會傳送時按下滑鼠左鍵 WM_LBUTTONDOWN 訊息和 WM_LBUTTONUP 訊息放開按鍵時。 當使用者從功能表列選取命令時，Windows 也會傳送 WM_COMMAND 訊息。

在 MFC 架構中，不同的物件，例如文件、 檢視、 框架視窗、 文件範本和應用程式物件，可以 「 處理 」 訊息。 這類物件提供 「 處理常式函式 」 做為其成員的其中一個函式，以及架構會將內送訊息對應至其處理常式。

您的程式設計工作的絕大部分是選擇哪些訊息来對應到哪些物件，然後實作該對應。 若要這樣做，您可以使用類別檢視 和 屬性 視窗。

[屬性] 視窗會建立空的訊息處理常式成員函式，而且您使用原始碼程式碼編輯器來實作的處理常式的主體。 您也可以建立或編輯 （包括自己的類別，不是衍生自 MFC 類別） 的類別和其成員，使用 類別檢視。 如需使用類別檢視，以及精靈加入至專案的程式碼的相關詳細資訊，請參閱[使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)。

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> 若要建立和編輯資源使用資源編輯器

使用 Visual c + +[資源編輯器](../windows/resource-editors.md)來建立和編輯功能表、 對話方塊、 自訂控制項、 快速鍵、 點陣圖、 圖示、 游標、 字串和版本資源。 截至 Visual c + + 4.0 版，工具列編輯器可建立工具列更容易。

為了協助您更多，Microsoft Foundation Class Library 會提供一個稱為一般檔案。RES，其中包含您可以從一般複製的 「 美工圖案 」 資源。RES 並貼到您自己的資源檔。 常見的。RES 包含工具列按鈕、 常見的資料指標、 圖示等。 您可以使用、 修改和重新發佈您的應用程式中的這些資源。 如需常見的詳細資訊。RES，請參閱[美工圖案範例](../visual-cpp-samples.md)。

MFC 應用程式精靈、 Visual c + + 精靈、 資源編輯器和 MFC 架構為您執行許多工作，以管理您的程式碼更容易。 大部分的應用程式特定的程式碼是在文件和檢視類別中。

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)
