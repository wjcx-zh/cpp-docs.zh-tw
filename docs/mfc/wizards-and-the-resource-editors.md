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
ms.openlocfilehash: fb1a523ca82cd8e1a4256da657efe9702517beda
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907359"
---
# <a name="wizards-and-the-resource-editors"></a>精靈和資源編輯器

視覺C++效果包含數個在 MFC 程式設計中使用的嚮導，以及許多整合式資源編輯器。 針對 ActiveX 控制項程式設計， [Activex Control Wizard](../mfc/reference/mfc-activex-control-wizard.md)的用途與 MFC 應用程式 wizard 的目的非常類似。 雖然您可以撰寫 MFC 應用程式，而不需要大部分的這些工具，但這些工具會大幅簡化並加快您的工作速度。

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a>使用 MFC 應用程式精靈來建立 MFC 應用程式

使用[Mfc 應用程式精靈](../mfc/reference/mfc-application-wizard.md)，在 Visual C++中建立 mfc 專案，其中可能包含 OLE 和資料庫支援。 專案中的檔案包含您的應用程式、檔、視圖和框架視窗類別;標準資源，包括功能表和選擇性工具列;其他必要的 Windows 檔案;和選擇性的 .rtf 檔案，其中包含標準 Windows 說明主題，您可以修訂並增強以建立程式的說明檔。

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>使用類別檢視來管理類別和 Windows 訊息

類別檢視可協助您建立 Windows 訊息和命令的處理常式函式、建立和管理類別、建立類別成員變數、建立自動化方法和屬性、建立資料庫類別等等。

> [!NOTE]
>  類別檢視也可協助您覆寫 MFC 類別中的虛擬函式。 選取要覆寫的類別和虛擬函式。 程式的其餘部分與訊息處理類似，如下段所述。

在 Windows 下執行的應用程式是[訊息驅動](../mfc/message-handling-and-mapping.md)的。 執行程式中發生的使用者動作和其他事件，會使 Windows 將訊息傳送至程式中的視窗。 例如，如果使用者在視窗中按一下滑鼠，當按下滑鼠左鍵時，Windows 就會傳送 WM_LBUTTONDOWN 訊息，並在放開按鈕時傳送 WM_LBUTTONUP 訊息。 當使用者從功能表列選取命令時，Windows 也會傳送 WM_COMMAND 訊息。

在 MFC 架構中，各種物件（例如檔、視圖、框架視窗、檔範本和應用程式物件）都可以「處理」訊息。 這類物件會提供「處理函式」做為其中一個成員函式，而架構會將內送訊息對應至其處理常式。

程式設計工作的一大部分是選擇哪些訊息要對應至哪些物件，然後再執行該對應。 若要這樣做，您可以使用類別檢視和[類別 Wizard](reference/mfc-class-wizard.md)。

[類別 Wizard](reference/mfc-class-wizard.md)會建立空的訊息處理常式成員函式，而您會使用原始程式碼編輯器來執行處理常式的主體。 您也可以使用類別檢視來建立或編輯類別（包括您自己的類別，而不是衍生自 MFC 類別）及其成員。 如需有關使用類別檢視以及將程式碼加入至專案之嚮導的詳細資訊，請參閱[使用程式碼嚮導加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)。

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>使用資源編輯器來建立和編輯資源

使用視覺效果C++ [資源編輯器](../windows/resource-editors.md)來建立和編輯功能表、對話方塊、自訂控制項、快速鍵、點陣圖、圖示、游標、字串和版本資源。 從 Visual C++ 4.0 版，工具列編輯器可讓您更輕鬆地建立工具列。

為了協助您更多，MFC 程式庫提供名為 COMMON 的檔案。RES，其中包含您可以從通用複製的「美工圖案」資源。RES 並貼到您自己的資源檔中。 一些.RES 包括工具列按鈕、通用游標、圖示等。 您可以在應用程式中使用、修改和轉散發這些資源。 如需一般的詳細資訊。RES，請參閱美工圖案[範例](../overview/visual-cpp-samples.md)。

MFC 應用程式精靈、Visual C++ wizard、資源編輯器和 mfc 架構會為您執行許多工作，並讓您更輕鬆地管理程式碼。 您的應用程式專屬程式碼大部分都在您的檔和視圖類別中。

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)
