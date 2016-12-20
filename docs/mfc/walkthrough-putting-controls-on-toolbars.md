---
title: "逐步解說：將控制項放在工具列上 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "自訂對話方塊, 加入控制項"
  - "工具列, 加入控制項"
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：將控制項放在工具列上
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明如何將包含視窗控制項的工具列按鈕加入至工具列。  在 MFC 中，工具列按鈕必須是 [CMFCToolBarButton Class](../mfc/reference/cmfctoolbarbutton-class.md)衍生類別，例如 [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)、 [CMFCToolBarEditBoxButton Class](../mfc/reference/cmfctoolbareditboxbutton-class.md)、 [CMFCDropDownToolbarButton Class](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)或 [CMFCToolBarMenuButton Class](../mfc/reference/cmfctoolbarmenubutton-class.md)。  
  
## 將控制項加入至工具列  
 若要將控制項加入至工具列，請依照下列步驟執行:  
  
1.  為在父工具列資源的按鈕保留假的資源 ID 。  如需如何利用 Visual Studio 的工具列編輯器建立按鈕的詳細資訊，請參閱 [Toolbar Editor](../mfc/toolbar-editor.md) 主題。  
  
2.  為在父工具列的所有點陣圖之按鈕保留工具列按鈕影像 \(按鈕圖示\)。  
  
3.  在處理 `AFX_WM_RESETTOOLBAR` 訊息的訊息處理常式，請執行下列步驟:  
  
    1.  使用 `CMFCToolbarButton` 衍生類別建構按鈕控制項。  
  
    2.  使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md) 以新的控制項取代假的按鈕。  因為 `ReplaceButton` 複製按鈕物件並維護複本，您可以在堆疊上的建構按鈕物件。  
  
> [!NOTE]
>  如果您啟用應用程式的自訂，您可能必須使用 \[**自訂**\] 對話方塊的 \[**工具列**\] 索引標籤上之 \[**重設**\] 按鈕重設工具列以看到在重新編譯之後出現在應用程式中更新後的控制項。  工具列狀態在 Windows 登錄中被儲存，且 `ReplaceButton` 方法在啟動期間執行後，註冊資訊會被載入並套用在應用程式。  
  
## 工具列控制項和自訂  
 \[**自訂**\] 對話方塊的 \[**命令**\] 索引標籤包含可在應用程式取得的命令清單。  根據預設，\[**自訂**\] 對話方塊在每個功能表類別來管理應用程式選單並建立標準工具列按鈕的清單。  若要保留工具列控制項提供的擴充功能，您必須在 \[**自訂**\] 對話方塊以自訂控制項取代標準工具列按鈕。  
  
 當您啟用自訂時，便會使用 [CMFCToolBarsCustomizeDialog Class](../mfc/reference/cmfctoolbarscustomizedialog-class.md) 類別建立自訂處理常式的 `OnViewCustomize` \[**自訂**\] 對話方塊。  在您呼叫 [CMFCToolBarsCustomizeDialog::Create](../Topic/CMFCToolBarsCustomizeDialog::Create.md)以顯示 \[**自訂**\] 對話方塊之前，呼叫 [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md) 以新的控制項取代標準按鈕。  
  
## 範例：建立搜尋下拉式方塊  
 本節說明如何建立會顯示在工具列並包含最近使用的搜尋字串之 `Find` 下拉式方塊控制項。  使用者可以在控制項中輸入字串然後按 ENTER 鍵搜尋檔案，或按 Esc 鍵將焦點移到主框架。  這個範例假設文件會顯示在 [CEditView Class](../mfc/reference/ceditview-class.md)的衍生檢視。  
  
### 建立搜尋控制項  
 首先，請建立 `Find` 下拉式方塊控制項：  
  
1.  將按鈕和其命令加入至應用程式資源：  
  
    1.  在應用程式資源中，將具有 `ID_EDIT_FIND` 命令 ID 的新按鈕加入至應用程式的工具列與任何和工具列相關的點陣圖。  
  
    2.  建立一個具有 ID\_EDIT\_FIND 命令 ID 之新的功能表項目。  
  
    3.  將新的字串「Find the text\\nFind」加入至字串資料表並將`ID_EDIT_FIND_COMBO` 命令 ID 指派給它。  這個 ID 將當做 `Find` 下拉式方塊按鈕的命令 ID。  
  
        > [!NOTE]
        >  因為 `ID_EDIT_FIND` 是由 `CEditView` 管理的標準命令，您不需要為實作這個命令的特殊處理常式。不過，您必須實作新命令 `ID_EDIT_FIND_COMBO` 的處理常式。  
  
2.  建立一個衍生自 [CComboBox Class](../mfc/reference/ccombobox-class.md) 的新類別：`CFindComboBox`。  
  
3.  在 `CFindComboBox`類別中，覆寫 `PreTranslateMessage` 虛擬方法。  這個方法會啟用下拉式方塊處理 [WM\_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) 訊息。  如果使用者點擊 Esc 鍵 \(`VK_ESCAPE`\)，會將焦點移回主框架視窗。  如果使用者點擊 ENTER 鍵 \(`VK_ENTER`\)，會將包含 `ID_EDIT_FIND_COMBO` 命令 ID 的 `WM_COMMAND` 訊息張貼到主框架視窗內。  
  
4.  為 `Find` 下拉式方塊按鈕建立類別，衍生自 [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  在此範例中，它的名稱是 `CFindComboButton`。  
  
5.  `CMFCToolbarComboBoxButton` 的建構函式接受三個參數：按鈕的命令 ID、按鈕影像索引和下拉式方塊樣式。  設定這些參數如下：  
  
    1.  傳遞 `ID_EDIT_FIND_COMBO` 做為命令 ID。  
  
    2.  使用 [CCommandManager::GetCmdImage](http://msdn.microsoft.com/zh-tw/4094d08e-de74-4398-a483-76d27a742dca) 和 `ID_EDIT_FIND` 取得影像索引。  
  
    3.  如需可用下拉式方塊樣式的清單，請參閱 [下拉式方塊樣式](../mfc/reference/combo-box-styles.md)。  
  
6.  在 `CFindComboButton` 類別中，覆寫 `CMFCToolbarComboBoxButton::CreateCombo` 方法。  您應該建立 `CFindComboButton` 物件並將其指標傳回給它。  
  
7.  使用 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 巨集讓下拉式按鈕永存。  工作區管理員會自動載入並保存在 Windows 登錄中的按鈕之狀態。  
  
8.  實作您的文件檢視中的 `ID_EDIT_FIND_COMBO` 處理常式。  使用 [CMFCToolBar::GetCommandButtons](../Topic/CMFCToolBar::GetCommandButtons.md) 和 `ID_EDIT_FIND_COMBO` 擷取所有 `Find` 下拉式方塊按鈕。  由於自訂，一個具有相同命令 ID 的按鈕可以有許多複本。  
  
9. 在 ID\_EDIT\_FIND 訊息處理常式 `OnFind`，請使用 [CMFCToolBar::IsLastCommandFromButton](../Topic/CMFCToolBar::IsLastCommandFromButton.md) 來判斷尋找命令是否從 `Find` 下拉式方塊按鈕傳送。  如果是，請尋找文字並將搜尋字串加入至下拉式方塊。  
  
### 將尋找控制項加入至主要工具列  
 若要將下拉式方塊按鈕加入至工具列，請依照下列步驟執行：  
  
1.  實作主框架視窗的 `AFX_WM_RESETTOOLBAR` 訊息處理常式 `OnToolbarReset` 。  
  
    > [!NOTE]
    >  在應用程式啟動期間工具列初始化時，或當工具列自訂期間重設時，架構會傳送訊息至主框架視窗。  無論如何，您必須以自訂 `Find` 下拉式方塊按鈕取代標準工具列按鈕。  
  
2.  在 `AFX_WM_RESETTOOLBAR` 處理常式，請檢查工具列 ID，也就是 `AFX_WM_RESETTOOLBAR` 訊息的 `WPARAM` 。  如果工具列 ID 與包含 `Find` 下拉式方塊按鈕的工具列相同，請呼叫 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md) 以取代 `Find` 按鈕 \(即按鈕具有 `CFindComboButton` 物件的命令 ID  `ID_EDIT_FIND)` 。  
  
    > [!NOTE]
    >  因為 `ReplaceButton` 複製按鈕物件並維護複本，您可以在堆疊上建構 `CFindComboBox` 物件。  
  
### 將尋找控制項加入至自訂對話方塊  
 在自訂處理常式 `OnViewCustomize`，呼叫 [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md) 以 `CFindComboButton` 物件取代 `Find` 按鈕 \(即按鈕具有命令 ID `ID_EDIT_FIND)`。  
  
## 請參閱  
 [階層架構圖表](../mfc/hierarchy-chart.md)   
 [類別](../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton Class](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog Class](../mfc/reference/cmfctoolbarscustomizedialog-class.md)