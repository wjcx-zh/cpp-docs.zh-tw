---
title: "工具箱、對話方塊編輯器索引標籤 | Microsoft Docs"
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
  - "工具箱 [C++], [對話方塊編輯器] 索引標籤"
  - "控制項 [C++], 類型"
  - "對話方塊中的 SysLink 控制項"
  - "自訂控制項 [Visual Studio], 對話方塊"
  - "控制項 [C++], 標準"
  - "對話方塊編輯器, 建立控制項"
  - "控制項 [C++], 加入對話方塊"
ms.assetid: 253885c2-dcb9-4d8e-ac9b-805ea31cbf5e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 工具箱、對話方塊編輯器索引標籤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您在對話方塊編輯器中工作時，\[對話方塊編輯器\] 索引標籤會出現在 [&#91;工具箱&#93; 視窗](../Topic/Toolbox.md)中。 若要將控制項加入新的對話方塊中，請將控制項從 \[工具箱\] 拖曳至您所建立的對話方塊 \(如需詳細資訊，請參閱[將控制項加入對話方塊中](../mfc/adding-a-control-to-a-dialog-box.md)\)。 然後移動控制項，或變更其大小和形狀。  
  
 \[工具箱\] 中提供的標準控制項為：  
  
-   [Button 控制項](../mfc/reference/cbutton-class.md)  
  
-   [核取方塊控制項](../mfc/reference/button-styles.md)  
  
-   [下拉式方塊控制項](../mfc/reference/ccombobox-class.md)  
  
-   [編輯控制項](../mfc/reference/cedit-class.md)  
  
-   群組方塊  
  
-   [清單方塊控制項](../mfc/reference/clistbox-class.md)  
  
-   [選項按鈕控制項](../mfc/reference/button-styles.md)  
  
-   [靜態文字控制項](../mfc/reference/cstatic-class.md)  
  
-   [圖片控制項](../mfc/reference/cpictureholder-class.md)  
  
-   [Rich Edit 2.0 控制項](../mfc/using-cricheditctrl.md)  
  
-   [捲軸控制項](../mfc/reference/cscrollbar-class.md)  
  
 \[工具箱\] 提供的 [Windows 通用控制項](../mfc/controls-mfc.md)可提升應用程式的功能。 包括：  
  
-   [Slider 控制項](../mfc/slider-control-styles.md)  
  
-   [微調控制項](../mfc/using-cspinbuttonctrl.md)  
  
-   [進度控制項](../mfc/styles-for-the-progress-control.md)  
  
-   [熱鍵控制項](../mfc/using-a-hot-key-control.md)  
  
-   [清單控制項](../mfc/list-control-and-list-view.md)  
  
-   [樹狀結構控制項](../mfc/tree-control-styles.md)  
  
-   [索引標籤控制項](../mfc/tab-controls-and-property-sheets.md)  
  
-   [動畫控制項](../mfc/using-an-animation-control.md)  
  
-   [日期時間選擇器控制項](../mfc/creating-the-date-and-time-picker-control.md)  
  
-   [月曆控制項](../mfc/month-calendar-control-examples.md)  
  
-   [IP 位址控制項](../mfc/reference/cipaddressctrl-class.md)  
  
-   [擴充的下拉式方塊控制項](../mfc/creating-an-extended-combo-box-control.md)  
  
-   [自訂控制項](../mfc/custom-controls-in-the-dialog-editor.md)  
  
 您可以選取 \[工具箱\] 中的**自訂控制項**圖示，將它拖曳到您的對話方塊中，將自訂控制項加入對話方塊中。 若要加入 Syslink 控制項，請加入自訂控制項，然後將控制項的 \[類別\] 屬性變更為 \[Syslink\]。 這會重新整理屬性，並顯示 Syslink 控制項屬性。 如需 MFC 包裝函式類別的相關資訊，請參閱 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)。  
  
 您也可以[將 ActiveX 控制項加入對話方塊中](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
 您也可以自訂 \[工具箱\] 視窗，讓它更好用。 如需詳細資訊，請參閱[管理 &#91;工具箱&#93; 中的項目和索引標籤](http://msdn.microsoft.com/zh-tw/21285050-cadd-455a-b1f5-a2289a89c4db)。 例如，您可以將控制項放置於 \[工具箱\] 視窗中，以方便存取。 如需詳細資訊，請參閱[自訂 &#91;工具箱&#93; 對話方塊](http://msdn.microsoft.com/zh-tw/bd07835f-18a8-433e-bccc-7141f65263bb)。  
  
 如需使用 RichEdit 1.0 控制項與 MFC 的詳細資訊，請參閱[使用 RichEdit 1.0 控制項與 MFC](../mfc/using-the-richedit-1-0-control-with-mfc.md)。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [控制項](../mfc/controls-mfc.md)   
 [控制項類別](../mfc/control-classes.md)   
 [對話方塊類別](../mfc/dialog-box-classes.md)   
 [捲軸樣式](../mfc/reference/scroll-bar-styles.md)   
 [Rich Edit 控制項範例](../mfc/rich-edit-control-examples.md)   
 [Adding Event Handlers for Dialog Box Controls](../mfc/adding-event-handlers-for-dialog-box-controls.md)   
 [對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)