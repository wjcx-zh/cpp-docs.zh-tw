---
title: "建立新的工具列按鈕 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor, creating buttons
- toolbar buttons (in Toolbar editor), button image
- toolbar buttons (in Toolbar editor), creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b89d88d931603f1f8dfd65f08cb78210eac19a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-new-toolbar-button"></a>建立新的工具列按鈕
### <a name="to-create-a-new-toolbar-button"></a>若要建立新的工具列按鈕  
  
1.  在[資源檢視](../windows/resource-view-window.md)展開 [資源] 資料夾 (例如，Project1.rc)。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  展開**工具列**資料夾，然後選取要編輯的工具列。  
  
3.  指定 ID 空白右端的工具列按鈕。 您可以藉由編輯**識別碼**屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)。 比方說，您可能想要讓工具列按鈕的功能表選項相同的識別碼。 在此情況下，使用下拉式清單方塊來選取**識別碼**功能表選項。  
  
     -或-  
  
     選取 [空白] 按鈕 （工具列檢視窗格） 中的工具列的右端並開始繪製。 指派的預設按鈕的命令識別碼 (ID_BUTTON\<n >)。  
  
 您也可以複製並貼到做為新按鈕的工具列上的映像。  
  
#### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要將影像加入做為按鈕的工具列  
  
1.  在[資源檢視](../windows/resource-view-window.md)，工具列按兩下以開啟它。  
  
2.  接下來，開啟您想要加入至您的工具列影像。  
  
    > [!NOTE]
    >  如果您在 Visual Studio 中開啟映像，它會在編輯器中開啟映像。 您也可以在其他圖形的程式中開啟映像。  
  
3.  從**編輯**功能表上，選擇**複製**。  
  
4.  切換至該工具列，即可在來源視窗頂端的索引標籤。  
  
5.  從**編輯**功能表上，選擇**貼上**。  
  
     影像會出現在工具列上，為新按鈕。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>需求  
 MFC 或 ATL  
  
## <a name="see-also"></a>請參閱  
 [工具列按鈕屬性](../windows/toolbar-button-properties.md)   
 [建立、 移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [工具列編輯器](../windows/toolbar-editor.md)

