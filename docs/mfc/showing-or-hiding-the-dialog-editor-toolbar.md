---
title: "顯示或隱藏對話方塊編輯器工具列 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項 [C++], 顯示或隱藏 [對話方塊] 編輯器工具列"
  - "工具列 [C++], 顯示"
  - "工具列 [C++], 隱藏"
  - "對話方塊編輯器, 顯示或隱藏工具列"
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 顯示或隱藏對話方塊編輯器工具列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

開啟對話方塊編輯器時，對話方塊編輯器工具列會自動出現在您的方案的上方。  
  
### 對話方塊編輯器工具列  
  
|圖示|意義|圖示|意義|  
|--------|--------|--------|--------|  
|![&#91;測試對話方塊&#93; 按鈕](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|測試對話方塊|![&#91;水平均等陳列&#93; 按鈕](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|橫向|  
|![&#91;對齊主控項的左緣&#93; 按鈕](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|對齊主控項的左緣|![&#91;垂直均等陳列&#93; 按鈕](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|向下|  
|![&#91;對齊主控項的右緣&#93; 按鈕](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|對齊主控項的右緣|![&#91;設定成相同寬度&#93; 按鈕](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|設定成相同寬度|  
|![&#91;對齊主控項的上緣&#93; 按鈕](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|對齊主控項的上緣|![&#91;設定成相同高度&#93; 按鈕](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|設定成相同高度|  
|![&#91;對齊主控項的下緣&#93; 按鈕](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|對齊主控項的下緣|![&#91;設定成相同大小&#93; 按鈕](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|設定成相同大小|  
|![&#91;垂直置中&#93; 按鈕](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![&#91;切換格線&#93; 按鈕](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切換格線|  
|![&#91;水平置中&#93; 按鈕](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![&#91;切換輔助線&#93; 按鈕](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切換輔助線|  
  
 \[對話方塊編輯器\] 工具列上包含的按鈕 \(例如，大小和對齊\)，目的是用來在對話方塊上排列控制項。  \[對話方塊編輯器\] 工具列按鈕，是與 \[格式\] 功能表上的命令相對應的。  如需詳細資訊，請參閱[對話方塊編輯器的快速鍵](../mfc/accelerator-keys-for-the-dialog-editor.md)。  
  
 在 \[對話方塊\] 編輯器中時，如果您想切換 \[對話方塊編輯器\] 工具列的顯示狀態，只要從可用工具列和視窗中選擇它即可。  
  
### 若要顯示或隱藏對話方塊編輯器工具列  
  
1.  在 \[檢視\] 功能表上按一下 \[工具列\]，然後從子功能表選擇 \[對話方塊編輯器\]。  
  
    > [!NOTE]
    >  當您在 \[對話方塊\] 編輯器中開啟對話方塊資源時，根據預設會顯示 \[對話方塊編輯器\] 工具列；然而，如果您將工具列關閉，就必須在下次開啟對話方塊資源時叫用它。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Dialog Editor](../mfc/dialog-editor.md)