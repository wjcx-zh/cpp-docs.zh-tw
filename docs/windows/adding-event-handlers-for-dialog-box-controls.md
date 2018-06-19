---
title: 加入對話方塊控制項的事件處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, adding event handlers to controls
- controls [C++], event handlers
- dialog box controls, events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f05a9bc05dea6d217505e2e098dc2fde0d251894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863695"
---
# <a name="adding-event-handlers-for-dialog-box-controls"></a>加入對話方塊控制項的事件處理常式
針對已在類別和相關聯的專案對話方塊中，您可以利用一些捷徑時建立事件處理常式。 您可以快速建立預設控制項通知事件，或有任何適用的 Windows 訊息的處理常式。  
  
#### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>若要建立預設控制項通知事件的處理常式  
  
1.  按兩下控制項。 開啟文字編輯器。  
  
2.  在文字編輯器中加入控制項告知處理常式程式碼。  
  
#### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>若要建立任何適用的 Windows 訊息的處理常式  
  
1.  按一下您要處理通知事件的控制項。  
  
2.  在[屬性視窗](/visualstudio/ide/reference/properties-window)，按一下 [**控制項事件**] 按鈕以顯示與控制項相關聯的一般 Windows 事件的清單。 比方說，標準**確定**按鈕**有關**對話方塊會列出下列通知事件：  
  
 **BN_CLICKED**  
  
 **BN_DOUBLECLICKED**  
  
 **BN_KILLFOCUS**  
  
 **BN_SETFOCUS**  
  
    > [!NOTE]
    >  或者，選取對話方塊中，按一下 [**控制項事件**] 按鈕以顯示在對話方塊中的所有控制項通用的 Windows 事件的清單。  
  
3.  在**屬性**視窗中，按一下右邊的資料行來處理，事件旁邊，然後選取 建議的通知事件名稱 (例如， **OnBnClickedOK**控點**BN_CLICKED**).  
  
    > [!NOTE]
    >  或者，您可以提供您的選擇，而不是選擇預設事件處理常式名稱的事件處理常式名稱。  
  
     一旦您選取的事件，Visual Studio 會開啟文字編輯器，並顯示事件處理常式的程式碼。 例如，下列程式碼會加入預設**OnBnClickedOK**:  
  
 ```  
    void CAboutDlg::OnBnClickedOk(void)  
 { *// TODO: Add your control notification handler code here  
 }  
 ```  
  
 如果您想要將事件處理常式加入類別以外實作對話方塊中，請使用[事件處理常式精靈](../ide/event-handler-wizard.md)。 如需詳細資訊，請參閱[加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [預設控制項事件](../windows/default-control-events.md)   
 [定義對話方塊控制項的成員變數](../windows/defining-member-variables-for-dialog-controls.md)   
 [對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)

