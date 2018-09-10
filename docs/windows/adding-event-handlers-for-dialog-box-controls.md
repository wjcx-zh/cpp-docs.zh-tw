---
title: 加入事件處理常式的對話方塊控制項 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], adding event handlers to controls
- controls [C++], event handlers
- dialog box controls [C++], events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5caec6d9d77d743fa1a8455819b813364bde27d0
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317052"
---
# <a name="adding-event-handlers-for-dialog-box-controls-c"></a>加入對話方塊控制項 （c + +） 的事件處理常式

專案對話方塊已有相關的類別，您可以利用一些捷徑時建立事件處理常式。 您可以快速建立預設的控制項通知事件，或是任何適用的 Windows 訊息的處理常式。

### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>若要建立的預設控制項告知事件處理常式

1. 按兩下控制項。 **文字**編輯器隨即開啟。

2. 加入控制項告知處理常式程式碼中的**文字**編輯器。

### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>若要建立任何適用的 Windows 訊息的處理常式

1. 按一下您要處理的通知事件的控制項。

2. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，按一下**控制項事件** 按鈕以顯示與控制項相關聯的一般 Windows 事件的清單。 例如，標準 **[確定]** 按鈕**有關**對話方塊會列出下列通知事件：

   - BN_CLICKED

   - BN_DOUBLECLICKED

   - BN_KILLFOCUS

   - BN_SETFOCUS

   > [!NOTE]
   > 或者，選取  對話方塊中，然後按一下**控制項事件** 按鈕以顯示在對話方塊中的所有控制項通用的 Windows 事件的清單。

3. 在 **屬性** 視窗中，按一下 事件處理，右側資料行，然後選取 建議的通知事件名稱 (例如`OnBnClickedOK`處理 BN_CLICKED)。

   > [!NOTE]
   > 或者，您可以提供您的選擇，而不是選擇預設的事件處理常式名稱的事件處理常式名稱。

   一旦您選取的事件，Visual Studio 會開啟**文字編輯器**並顯示事件處理常式的程式碼。 例如，將下列程式碼加入預設`OnBnClickedOK`:

    ```cpp
    void CAboutDlg::OnBnClickedOk(void)
    {
        // TODO: Add your control notification handler code here
    }
    ```

如果您想要將事件處理常式加入類別以外的其他實作的對話方塊，請使用[事件處理常式精靈](../ide/event-handler-wizard.md)。 如需詳細資訊，請參閱 <<c0> [ 加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[預設控制項事件](../windows/default-control-events.md)  
[定義對話方塊控制項的成員變數](../windows/defining-member-variables-for-dialog-controls.md)  
[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)  
[加入類別](../ide/adding-a-class-visual-cpp.md)  
[新增成員函式](../ide/adding-a-member-function-visual-cpp.md)  
[新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)  
[覆寫虛擬函式](../ide/overriding-a-virtual-function-visual-cpp.md)  
[MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)  