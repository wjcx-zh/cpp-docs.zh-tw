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
ms.openlocfilehash: 04d9f2cf615636b151af93a3c3880f7357496048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365269"
---
# <a name="wizards-and-the-resource-editors"></a>精靈和資源編輯器

可視化C++包括用於MFC程式設計的幾種嚮導,以及許多整合資源編輯器。 對於 ActiveX 控件編程[,ActiveX 控制精靈](../mfc/reference/mfc-activex-control-wizard.md)的作用與 MFC 應用程式精靈的用途非常類似。 雖然無需大多數這些工具即可編寫 MFC 應用程式,但這些工具大大簡化了您的工作並加快了速度。

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a>使用 MFC 應用程式精靈建立 MFC 應用程式

使用[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)在 Visual C++中創建 MFC 專案,該專案可以包括 OLE 和資料庫支援。 專案中的檔包含應用程式、文檔、檢視和框架視窗類;標準資源,包括功能表和可選工具列;其他必需的 Windows 檔;與可選的 .rtf 檔包含標準 Windows 幫助主題,您可以修改和增強這些主題以建立程式的幫助檔。

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>使用類檢視管理類和 Windows 訊息

Class View 可説明您為 Windows 消息和指令創建處理程式函數、創建和管理類、創建類成員變數、創建自動化方法和屬性、創建資料庫類等。

> [!NOTE]
> 類視圖還可以説明您覆蓋 MFC 類中的虛擬函數。 選擇要重寫的類和虛擬函數。 該過程的其餘部分類似於消息處理,如以下段落所述。

在 Windows 下執行的應用程式是[訊息驅動的](../mfc/message-handling-and-mapping.md)。 運行程式中發生的使用者操作和其他事件會導致Windows向程式中的視窗發送消息。 例如,如果用戶按下視窗中的滑鼠,則當按下滑鼠左鍵時,Windows 會發送WM_LBUTTONDOWN消息,並在釋放該按鈕時發送WM_LBUTTONUP消息。 當使用者從功能表欄中選擇命令時,Windows 還會發送WM_COMMAND消息。

在 MFC 框架中,各種物件(如文檔、檢視、框架視窗、文檔範本和應用程式物件)可以"處理"消息。 此類物件提供"處理程式函數"作為其成員函數之一,並且框架將傳入消息映射到其處理程式。

程式設計任務的很大一部分是選擇要映射到哪些物件的消息,然後實現該映射。 此,請使用類別檢視和[類別精靈](reference/mfc-class-wizard.md)。

[類嚮導](reference/mfc-class-wizard.md)將建立空消息處理程式成員函數,並且您可以使用原始程式碼編輯器來實現處理程式的正文。 您還可以使用類檢視創建或編輯類(包括您自己的類,而不是從 MFC 類派生的類) 及其成員。 有關使用類別檢視與向專案新增程式碼的精靈的詳細資訊,請參考[使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)。

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>使用資源編輯器建立及編輯資源

使用 VisualC++[資源編輯器](../windows/resource-editors.md)創建和編輯功能表、對話框、自定義控制項、快捷鍵、點陣圖、圖示、遊標、字串和版本資源。 從 Visual C++ 版本 4.0 起,工具列編輯器使創建工具列變得更加容易。

為了説明您更多,Microsoft 基礎類庫提供了一個名為 COMMON 的檔。RES,其中包含可以從 COMMON 複製的「剪貼畫」資源。RES 並貼上到您自己的資源檔中。 常見。RES 包括工具列按鈕、常用游標、圖示等。 您可以在應用程式中使用、修改和重新分發這些資源。 有關 COMMON 的詳細資訊。RES,請參考[剪貼圖範例](../overview/visual-cpp-samples.md)。

MFC 應用程式精靈、可視C++嚮導、資源編輯器和 MFC 框架為您做了大量工作,使管理代碼變得更加容易。 應用程式特定代碼的大部分位於文檔和檢視類中。

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)
