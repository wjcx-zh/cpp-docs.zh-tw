---
title: "影像功能表 (圖示影像編輯器) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "影像功能表"
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 影像功能表 (圖示影像編輯器)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\[影像\] 功能表 \(當 \[影像編輯器\] 在作用中時才會出現\) 所包含的命令，可以用來編輯影像、管理調色盤及設定影像編輯器視窗選項。  此外，在使用圖示和游標時，可使用用來使用裝置影像的命令。  
  
 **反轉色彩**  
 反轉色彩。  如需詳細資訊，請參閱[反轉選取範圍內的色彩](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)。  
  
 **水平翻轉**  
 水平翻轉影像或選取範圍。  如需詳細資訊，請參閱[翻轉影像](../mfc/flipping-an-image-image-editor-for-icons.md)。  
  
 **垂直翻轉**  
 垂直翻轉影像或選取範圍。  如需詳細資訊，請參閱[翻轉影像](../mfc/flipping-an-image-image-editor-for-icons.md)。  
  
 **旋轉 90 度**  
 旋轉影像或選取範圍 90 度。  如需詳細資訊，請參閱[翻轉影像](../mfc/flipping-an-image-image-editor-for-icons.md)。  
  
 **顯示色彩視窗**  
 開啟[色彩視窗](../windows/colors-window-image-editor-for-icons.md)，您可在其中選擇要用於影像的色彩。  如需詳細資訊，請參閱[使用色彩](../mfc/working-with-color-image-editor-for-icons.md)。  
  
 **將選取範圍當做筆刷使用**  
 可讓您從影像的一部分建立自訂筆刷。  您的選取範圍即成為自訂筆刷，將色彩散佈於影像的選取範圍內。  選取範圍的複本會沿著拖曳路徑留存。  拖曳的速度越慢，製作的複本越多。  如需詳細資訊，請參閱[建立自訂筆刷](../mfc/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 **複製和建立選取範圍外框**  
 建立一份目前選取範圍的複本，並建立此複本的外框。  如果背景色彩包含在目前的選取範圍內，當您選取[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)時，背景色彩將會排除在外。  
  
 **調整色彩**  
 開啟[自訂色彩選取器](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)，其可讓您自訂用於影像的色彩。  如需詳細資訊，請參閱[自訂或變更色彩](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  
  
 **載入調色盤**  
 開啟[載入調色盤對話方塊](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)，其可讓您載入先前儲存為 .pal 檔的調色盤色彩。  
  
 **儲存調色盤**  
 將調色盤色彩儲存為 .pal 檔。  
  
 **不透明處理**  
 當選取時，會使目前的選取範圍不透明。  當清除時，會使目前的選取範圍透明。  如需詳細資訊，請參閱[選擇不透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
 **工具列編輯器**  
 開啟[新增工具列資源對話方塊](../mfc/new-toolbar-resource-dialog-box.md)。  
  
 **格線設定**  
 開啟[格線設定對話方塊](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)，您可在其中指定影像的格線。  
  
 **新增影像類型**  
 開啟[新增 \<Device\> 影像類型對話方塊](../mfc/new-device-image-type-dialog-box-image-editor-for-icons.md)。  單一圖示資源可包含數個不同大小的影像；視窗可使用適當的圖示大小，視其顯示的方式而定。  新的裝置類型不會修改圖示的大小，而會在圖示內建立新的影像。  僅套用至圖示和游標。  
  
 **目前的圖示\/游標影像類型**  
 開啟子功能表，其列出最先可用的游標或圖示影像 \(前面九個\)。  子功能表上的最後一個命令 \[其他...\] 會[開啟 \<Device\> 影像對話方塊](../mfc/open-device-image-dialog-box-image-editor-for-icons.md)。  
  
 **刪除影像類型**  
 刪除所選取的裝置影像。  
  
 **工具**  
 啟動子功能表，此子功能表包含[影像編輯器工具列](../mfc/toolbar-image-editor-for-icons.md)上的所有工具。  
  
## 需求  
 None  
  
## 請參閱  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)