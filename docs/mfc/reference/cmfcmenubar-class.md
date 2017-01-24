---
title: "CMFCMenuBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCMenuBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMenuBar class"
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
caps.latest.revision: 36
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCMenuBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

功能表列實作停駐。  
  
## 語法  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCMenuBar::AdjustLocations](../Topic/CMFCMenuBar::AdjustLocations.md)|\(覆寫 `CMFCToolBar::AdjustLocations`\)。|  
|[CMFCMenuBar::AllowChangeTextLabels](../Topic/CMFCMenuBar::AllowChangeTextLabels.md)|指定文字標籤是否可以顯示在工具列按鈕的影像的下方。  \(覆寫 [CMFCToolBar::AllowChangeTextLabels](../Topic/CMFCToolBar::AllowChangeTextLabels.md)\)。|  
|[CMFCMenuBar::AllowShowOnPaneMenu](../Topic/CMFCMenuBar::AllowShowOnPaneMenu.md)|\(覆寫 `CPane::AllowShowOnPaneMenu`\)。|  
|[CMFCMenuBar::CalcFixedLayout](../Topic/CMFCMenuBar::CalcFixedLayout.md)|計算工具列的水平大小。  \(覆寫 [CMFCToolBar::CalcFixedLayout](../Topic/CMFCToolBar::CalcFixedLayout.md)\)。|  
|[CMFCMenuBar::CalcLayout](../Topic/CMFCMenuBar::CalcLayout.md)|\(覆寫 `CMFCToolBar::CalcLayout`\)。|  
|[CMFCMenuBar::CalcMaxButtonHeight](../Topic/CMFCMenuBar::CalcMaxButtonHeight.md)|計算最大高度工具列上的按鈕。  \(覆寫 [CMFCToolBar::CalcMaxButtonHeight](../Topic/CMFCToolBar::CalcMaxButtonHeight.md)\)。|  
|[CMFCMenuBar::CanBeClosed](../Topic/CMFCMenuBar::CanBeClosed.md)|指定使用者是否可以關閉工具列。  \(覆寫 [CMFCToolBar::CanBeClosed](../Topic/CMFCToolBar::CanBeClosed.md)\)。|  
|[CMFCMenuBar::CanBeRestored](../Topic/CMFCMenuBar::CanBeRestored.md)|決定系統是否可以還原工具列到原來的狀態在自訂之後。  \(覆寫 [CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md)\)。|  
|[CMFCMenuBar::Create](../Topic/CMFCMenuBar::Create.md)|建立功能表控制項並將其附加至 `CMFCMenuBar` 物件。|  
|[CMFCMenuBar::CreateEx](../Topic/CMFCMenuBar::CreateEx.md)|建立含有其他樣式選項的 `CMFCMenuBar` 物件。|  
|[CMFCMenuBar::CreateFromMenu](../Topic/CMFCMenuBar::CreateFromMenu.md)|初始化 `CMFCMenuBar` 物件。  接受做為填入的 `CMFCMenuBar`之樣板的一 `HMENU` 參數。|  
|[CMFCMenuBar::EnableHelpCombobox](../Topic/CMFCMenuBar::EnableHelpCombobox.md)|啟用在功能表列上的右邊的 \[**說明**\] 下拉式方塊。|  
|[CMFCMenuBar::EnableMenuShadows](../Topic/CMFCMenuBar::EnableMenuShadows.md)|指定是否顯示快顯功能表的陰影。|  
|[CMFCMenuBar::GetAvailableExpandSize](../Topic/CMFCMenuBar::GetAvailableExpandSize.md)|\(覆寫 [CPane::GetAvailableExpandSize](../Topic/CPane::GetAvailableExpandSize.md)\)。|  
|[CMFCMenuBar::GetColumnWidth](../Topic/CMFCMenuBar::GetColumnWidth.md)|傳回工具列按鈕的寬度。  \(覆寫 [CMFCToolBar::GetColumnWidth](../Topic/CMFCToolBar::GetColumnWidth.md)\)。|  
|[CMFCMenuBar::GetDefaultMenu](../Topic/CMFCMenuBar::GetDefaultMenu.md)|將控制代碼傳回至資源檔中的原始的功能表。|  
|[CMFCMenuBar::GetDefaultMenuResId](../Topic/CMFCMenuBar::GetDefaultMenuResId.md)|傳回原始功能表的資源識別項在資源檔中。|  
|[CMFCMenuBar::GetFloatPopupDirection](../Topic/CMFCMenuBar::GetFloatPopupDirection.md)||  
|[CMFCMenuBar::GetForceDownArrows](../Topic/CMFCMenuBar::GetForceDownArrows.md)||  
|[CMFCMenuBar::GetHelpCombobox](../Topic/CMFCMenuBar::GetHelpCombobox.md)|會將指標傳至 \[**說明**\] 下拉式方塊。|  
|[CMFCMenuBar::GetHMenu](../Topic/CMFCMenuBar::GetHMenu.md)|將控制代碼傳回給 `CMFCMenuBar` 附加至物件的功能表。|  
|[CMFCMenuBar::GetMenuFont](../Topic/CMFCMenuBar::GetMenuFont.md)|傳回功能表物件的目前全域字型。|  
|[CMFCMenuBar::GetMenuItem](../Topic/CMFCMenuBar::GetMenuItem.md)|傳回工具列按鈕與所提供之項目的索引。|  
|[CMFCMenuBar::GetRowHeight](../Topic/CMFCMenuBar::GetRowHeight.md)|傳回高度工具列按鈕。  \(覆寫 [CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md)\)。|  
|[CMFCMenuBar::GetSystemButton](../Topic/CMFCMenuBar::GetSystemButton.md)||  
|[CMFCMenuBar::GetSystemButtonsCount](../Topic/CMFCMenuBar::GetSystemButtonsCount.md)||  
|[CMFCMenuBar::GetSystemMenu](../Topic/CMFCMenuBar::GetSystemMenu.md)||  
|[CMFCMenuBar::HighlightDisabledItems](../Topic/CMFCMenuBar::HighlightDisabledItems.md)|表示停用是否反白顯示功能表項目。|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](../Topic/CMFCMenuBar::IsButtonExtraSizeAvailable.md)|決定工具列是否可以顯示擴充框線按鈕。  \(覆寫 [CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md)\)。|  
|[CMFCMenuBar::IsHighlightDisabledItems](../Topic/CMFCMenuBar::IsHighlightDisabledItems.md)|表示停用項目是否會反白顯示。|  
|[CMFCMenuBar::IsMenuShadows](../Topic/CMFCMenuBar::IsMenuShadows.md)|表示陰影是否為快顯功能表中繪製。|  
|[CMFCMenuBar::IsRecentlyUsedMenus](../Topic/CMFCMenuBar::IsRecentlyUsedMenus.md)|表示最近使用的命令是否在功能表列顯示。|  
|[CMFCMenuBar::IsShowAllCommands](../Topic/CMFCMenuBar::IsShowAllCommands.md)|表示快顯功能表是否會顯示所有命令。|  
|[CMFCMenuBar::IsShowAllCommandsDelay](../Topic/CMFCMenuBar::IsShowAllCommandsDelay.md)|指出功能表是否在短暫的延遲之後顯示所有命令。|  
|[CMFCMenuBar::LoadState](../Topic/CMFCMenuBar::LoadState.md)|從登錄載入 `CMFCMenuBar` 物件的狀態。|  
|[CMFCMenuBar::OnChangeHot](../Topic/CMFCMenuBar::OnChangeHot.md)|呼叫框架，當使用者選取  工具列上的按鈕。  \(覆寫 [CMFCToolBar::OnChangeHot](../Topic/CMFCToolBar::OnChangeHot.md)\)。|  
|[CMFCMenuBar::OnDefaultMenuLoaded](../Topic/CMFCMenuBar::OnDefaultMenuLoaded.md)|呼叫框架，其在框架視窗從資源檔載入預設功能表。|  
|[CMFCMenuBar::OnSendCommand](../Topic/CMFCMenuBar::OnSendCommand.md)|\(覆寫 `CMFCToolBar::OnSendCommand`\)。|  
|[CMFCMenuBar::OnSetDefaultButtonText](../Topic/CMFCMenuBar::OnSetDefaultButtonText.md)|呼叫，便會由架構功能表中自訂和使用者模式下執行時變更功能表項目的文字。|  
|[CMFCMenuBar::OnToolHitTest](../Topic/CMFCMenuBar::OnToolHitTest.md)|\(覆寫 `CMFCToolBar::OnToolHitTest`\)。|  
|[CMFCMenuBar::PreTranslateMessage](../Topic/CMFCMenuBar::PreTranslateMessage.md)|\(覆寫 `CMFCToolBar::PreTranslateMessage`\)。|  
|[CMFCMenuBar::RestoreOriginalstate](../Topic/CMFCMenuBar::RestoreOriginalstate.md)|呼叫，便會由架構功能表中自訂和使用者模式下執行時功能表列選取 \[**重設**\] 。|  
|[CMFCMenuBar::SaveState](../Topic/CMFCMenuBar::SaveState.md)|`CMFCMenuBar` 儲存物件的狀態為註冊的。|  
|[CMFCMenuBar::SetDefaultMenuResId](../Topic/CMFCMenuBar::SetDefaultMenuResId.md)|設定資源檔的原始的功能表。|  
|[CMFCMenuBar::SetForceDownArrows](../Topic/CMFCMenuBar::SetForceDownArrows.md)||  
|[CMFCMenuBar::SetMaximizeMode](../Topic/CMFCMenuBar::SetMaximizeMode.md)|呼叫框架，如同的 MDI 子視窗變更它的顯示模式。  如果 MDI 子視窗最大化或最近不再最大化，則這個方法會更新功能表列。|  
|[CMFCMenuBar::SetMenuButtonRTC](../Topic/CMFCMenuBar::SetMenuButtonRTC.md)|設定所產生之執行階段類別資訊，讓使用者動態地建立功能表按鈕時。|  
|[CMFCMenuBar::SetMenuFont](../Topic/CMFCMenuBar::SetMenuFont.md)|將所有功能表的字型在應用程式。|  
|[CMFCMenuBar::SetRecentlyUsedMenus](../Topic/CMFCMenuBar::SetRecentlyUsedMenus.md)|指定功能表列顯示最近使用的功能表命令。|  
|[CMFCMenuBar::SetShowAllCommands](../Topic/CMFCMenuBar::SetShowAllCommands.md)|指定功能表列上是否會顯示所有命令。|  
  
## 備註  
 是功能表列實作內建功能的 `CMFCMenuBar` 類別。  它類似工具列，不過，它無法關閉\-它永遠顯示。  
  
 `CMFCMenuBar` 支援顯示最近使用的功能表項目物件的選項。  啟用此選項， `CMFCMenuBar` 顯示可用命令的子集中第一個檢視的。  之後，最近使用命令與命令時的原始子集中顯示。  此外，使用者可以展開此功能表檢視所有可用的命令。  因此，在中，只有在最新的後，每個可用的命令設定通常會顯示，否則顯示。  
  
 若要使用 `CMFCMenuBar` 物件，請將它內嵌在主視窗框架物件。  在處理 `WM_CREATE` 訊息時，請呼叫 `CMFCMenuBar::Create` 或 `CMFCMenuBar::CreateEx`。  不論您使用建立函式，則會將指標主框架視窗。  然後呼叫 [CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md)啟用停駐。  藉由呼叫 [CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md)修正此功能表。  
  
## 範例  
 下列範例會在 `CMFCMenuBar` 類別會示範如何使用各種方法。  這個範例顯示如何設定窗格的樣式，以啟用自訂按鈕，可以讓說明啟用  方塊中，快顯功能表的陰影和更新的功能表列。  這個程式碼片段是 [IE 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/CPP/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/CPP/cmfcmenubar-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)  
  
## 需求  
 **標題:** afxmenubar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)