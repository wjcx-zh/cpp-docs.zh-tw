---
title: 對話方塊控制項和程式碼之間切換 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog editor, accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog editor, switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ffcb4621bf0005e6b22991da7a2dde9372afa6c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891918"
---
# <a name="switching-between-dialog-box-controls-and-code"></a>在對話方塊控制項和程式碼之間切換
在 MFC 應用程式，您可以按兩下對話方塊控制項跳至其處理常式程式碼，或快速建立虛設常式處理常式函式。  
  
 選取的控制項，請按一下**控制項事件**按鈕或**訊息**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)若要檢視 Windows 訊息和事件的完整清單適用於選取的項目。 從要建立或編輯處理常式函式的清單中選擇。  
  
### <a name="to-jump-to-code-from-the-dialog-editor"></a>跳至程式碼從對話方塊編輯器  
  
1.  若要移至它的最近實作訊息處理函式宣告在對話方塊內的控制項上按兩下。 （對於 ATL 為基礎的對話方塊類別中，您一律跳到建構函式定義。）  
  
### <a name="to-view-events-for-a-control"></a>若要檢視控制項的事件  
  
1.  選取的控制項，請按一下**控制項事件**按鈕[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
    > [!NOTE]
    >  按一下**控制項事件**按鈕時*對話方塊*具有焦點會公開一份所有控制項在對話方塊方塊中，接著，您可以展開要編輯的個別控制項的事件。  
  
     當單一控制項取得焦點在對話方塊中時，您可以以滑鼠右鍵按一下它，並選取**加入事件處理常式**從捷徑功能表。 這可讓您指定要加入處理常式的類別。 如需詳細資訊，請參閱[加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。  
  
### <a name="to-view-messages-for-a-dialog-box"></a>若要檢視訊息 對話方塊  
  
1.  選取對話方塊中，按一下 [**訊息**按鈕[屬性] 視窗](/visualstudio/ide/reference/properties-window)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊編輯器](../windows/dialog-editor.md)

