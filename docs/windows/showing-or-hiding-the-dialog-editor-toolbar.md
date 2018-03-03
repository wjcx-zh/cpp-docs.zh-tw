---
title: "顯示或隱藏對話方塊編輯器工具列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog editor, showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbb77c6851b9e8b93c1b3bbd0b1d30bcf65e3d42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar"></a>顯示或隱藏對話方塊編輯器工具列
當您開啟對話方塊編輯器時，對話方塊編輯器工具列會自動出現在您的方案的頂端。  
  
### <a name="dialog-editor-toolbar"></a>對話方塊編輯器工具列  
  
|圖示|意義|圖示|意義|  
|----------|-------------|----------|-------------|  
|![測試對話方塊按鈕](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|文字方塊|![水平均等陳列 按鈕](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|橫向|  
|![對齊靠左 按鈕](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|對齊主控項的左緣|![[垂直均等陳列] 按鈕](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|下移|  
|![對齊緣 按鈕](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|對齊主控項的右緣|![讓相同寬度 按鈕](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|設定成相同寬度|  
|![對齊上緣 按鈕](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|對齊主控項的上緣|![讓相同高度 按鈕](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|設定成相同高度|  
|![靠下對齊按鈕](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|靠下對齊|![讓相同大小 按鈕](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|設定成相同大小|  
|![垂直置中 按鈕](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切換格線 按鈕](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切換格線|  
|![水平置中 按鈕](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切換輔助線按鈕](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切換輔助線|  
  
 對話方塊編輯器工具列會包含按鈕排列控制項在對話方塊中，例如大小和對齊的配置。 對話方塊編輯器工具列按鈕對應至 [格式] 功能表上的命令。 如需詳細資訊，請參閱[對話方塊編輯器的快速鍵](../windows/accelerator-keys-for-the-dialog-editor.md)。  
  
 當您在對話方塊編輯器中，您可以從可用工具列和視窗的清單中選取來切換對話方塊編輯器工具列的顯示。  
  
### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>若要顯示或隱藏對話方塊編輯器工具列  
  
1.  在**檢視**功能表上，按一下**工具列**然後選擇 **對話方塊編輯器**從子功能表。  
  
    > [!NOTE]
    >  對話方塊編輯器工具列會顯示根據預設，當您在對話方塊編輯器中，開啟對話方塊資源不過，如果您明確地關閉工具列，您必須在的下次您開啟對話方塊資源叫用它。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [在對話方塊上的控制項的排列方式](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [如何： 建立資源](../windows/how-to-create-a-resource.md)   
 [資源檔](../windows/resource-files-visual-studio.md)   
 [對話方塊編輯器](../windows/dialog-editor.md)

