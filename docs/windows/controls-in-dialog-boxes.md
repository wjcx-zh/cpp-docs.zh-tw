---
title: "在對話方塊中的控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls, about dialog box controls
- dialog box controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02ca3523de9341c14d2e2a9837ba84f5625a3379
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="controls-in-dialog-boxes"></a>對話方塊中的控制項
您可以將控制項加入對話方塊方塊中，使用[對話方塊編輯器索引標籤](../windows/dialog-editor-tab-toolbox.md)中[工具箱視窗](/visualstudio/ide/reference/toolbox)，可讓您選擇您想要並將它拖曳至 對話方塊的控制項。 根據預設，[工具箱] 視窗設定為自動隱藏。 對話方塊編輯器開啟時，它會為方案的左邊界的索引標籤出現。 不過，您可以釘選 [工具箱] 視窗進入位置，即可**自動隱藏**視窗右上角的按鈕。 如需有關如何控制這個視窗行為的詳細資訊，請參閱[視窗管理](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。  
  
 將控制項加入對話方塊中，重新定位現有的控制項，或將控制項從一個對話方塊移到另一個，最快速的方式是使用拖放方法。 控制項的位置述虛線，直到卸除在對話方塊中。 時，您將控制項加入對話方塊中的拖放方法，此控制項提供標準高度適用於該類型的控制項。  
  
 當您將控制項加入對話方塊中，或重新定位時，它的最後位置可能取決於輔助線或邊界，還是您擁有開啟版面配置方格。  
  
 一旦您已將控制項加入至對話方塊中，您可以變更屬性，例如在其標題[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以選取多個控制項，並同時變更其屬性。  
  
-   [新增、編輯或刪除控制項](adding-editing-or-deleting-controls.md)  
  
-   [選取控制項](../windows/selecting-controls.md)  
  
-   [調整個別控制項的大小](../windows/sizing-individual-controls.md)  
  
-   [讓控制項同寬、同高或相同大小](../windows/making-controls-the-same-width-height-or-size.md)  
  
-   [設定下拉式方塊和下拉式清單的大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)  
  
-   [將值新增至下拉式方塊控制項](../windows/adding-values-to-a-combo-box-control.md)  
  
-   [設定水平捲軸的寬度](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)  
  
-   [控制項在對話方塊上的排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)  
  
-   [在對話方塊編輯器中自訂控制項](custom-controls-in-the-dialog-editor.md)  
  
-   [定義助憶鍵 (便捷鍵)](../windows/defining-mnemonics-access-keys.md)  
  
-   [指定對話方塊的位置和大小](../windows/specifying-the-location-and-size-of-a-dialog-box.md)  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [加入對話方塊控制項的事件處理常式](../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)   
 [對話方塊編輯器](../windows/dialog-editor.md)

