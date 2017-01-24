---
title: "CMFCPopupMenu Class | Microsoft Docs"
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
  - "CMFCPopupMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPopupMenu class"
ms.assetid: 9555dca1-8c9c-44c9-af72-0659ddad128e
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPopupMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 Windows 快顯功能表功能並加入功能擴充它 \(例如 Tear\-Off 功能表和工具提示。  
  
## 語法  
  
```  
class CMFCPopupMenu : public CMiniFrameWnd  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPopupMenu::CMFCPopupMenu](../Topic/CMFCPopupMenu::CMFCPopupMenu.md)|建構 `CMFCPopupMenu` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPopupMenu::ActivatePopupMenu](../Topic/CMFCPopupMenu::ActivatePopupMenu.md)||  
|[CMFCPopupMenu::AlwaysShowEmptyToolsEntry](../Topic/CMFCPopupMenu::AlwaysShowEmptyToolsEntry.md)|設定快顯功能表是否啟用顯示使用者定義的工具的空項目。|  
|[CMFCPopupMenu::AreAllCommandsShown](../Topic/CMFCPopupMenu::AreAllCommandsShown.md)||  
|[CMFCPopupMenu::CheckArea](../Topic/CMFCPopupMenu::CheckArea.md)|判斷某個點的位置 \(相對於快顯功能表。|  
|[CMFCPopupMenu::CloseMenu](../Topic/CMFCPopupMenu::CloseMenu.md)||  
|[CMFCPopupMenu::Create](../Topic/CMFCPopupMenu::Create.md)|建立快顯功能表並將其附加至 `CMFCPopupMenu` 物件。|  
|[CMFCPopupMenu::DefaultMouseClickOnClose](../Topic/CMFCPopupMenu::DefaultMouseClickOnClose.md)||  
|[CMFCPopupMenu::EnableMenuLogo](../Topic/CMFCPopupMenu::EnableMenuLogo.md)|初始化快顯功能表的商標。|  
|[CMFCPopupMenu::EnableMenuSound](../Topic/CMFCPopupMenu::EnableMenuSound.md)|啟用功能表音效。|  
|[CMFCPopupMenu::EnableResize](../Topic/CMFCPopupMenu::EnableResize.md)||  
|[CMFCPopupMenu::EnableScrolling](../Topic/CMFCPopupMenu::EnableScrolling.md)||  
|[CMFCPopupMenu::EnableVertResize](../Topic/CMFCPopupMenu::EnableVertResize.md)||  
|[CMFCPopupMenu::FindSubItemByCommand](../Topic/CMFCPopupMenu::FindSubItemByCommand.md)||  
|[CMFCPopupMenu::GetActiveMenu](../Topic/CMFCPopupMenu::GetActiveMenu.md)|傳回目前作用中的功能表。|  
|[CMFCPopupMenu::GetAnimationSpeed](../Topic/CMFCPopupMenu::GetAnimationSpeed.md)|會傳回快顯功能表的動畫速度。|  
|[CMFCPopupMenu::GetAnimationType](../Topic/CMFCPopupMenu::GetAnimationType.md)|會傳回快顯功能表動畫的目前型別。|  
|[CMFCPopupMenu::GetDropDirection](../Topic/CMFCPopupMenu::GetDropDirection.md)||  
|[CMFCPopupMenu::GetForceMenuFocus](../Topic/CMFCPopupMenu::GetForceMenuFocus.md)|表示焦點是否傳回功能表列，且快顯功能表隨即顯示。|  
|[CMFCPopupMenu::GetForceShadow](../Topic/CMFCPopupMenu::GetForceShadow.md)||  
|[CMFCPopupMenu::GetHMenu](../Topic/CMFCPopupMenu::GetHMenu.md)|將控制代碼傳回給其他的功能表資源。|  
|[CMFCPopupMenu::GetMenuBar](../Topic/CMFCPopupMenu::GetMenuBar.md)|傳回 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 內嵌在快顯功能表內。|  
|[CMFCPopupMenu::GetMenuItem](../Topic/CMFCPopupMenu::GetMenuItem.md)|傳回指向功能表項目在指定之索引處的。|  
|[CMFCPopupMenu::GetMenuItemCount](../Topic/CMFCPopupMenu::GetMenuItemCount.md)|傳回集合中的項目數目快顯功能表的。|  
|[CMFCPopupMenu::GetMessageWnd](../Topic/CMFCPopupMenu::GetMessageWnd.md)|會將指標傳至架構就會傳送快顯功能表訊息的視窗。|  
|[CMFCPopupMenu::GetParentArea](../Topic/CMFCPopupMenu::GetParentArea.md)||  
|[CMFCPopupMenu::GetParentButton](../Topic/CMFCPopupMenu::GetParentButton.md)|會將指標傳至父代 \(Parent\) 工具列按鈕。|  
|[CMFCPopupMenu::GetParentPopupMenu](../Topic/CMFCPopupMenu::GetParentPopupMenu.md)|傳回指向父快顯功能表。|  
|[CMFCPopupMenu::GetParentRibbonElement](../Topic/CMFCPopupMenu::GetParentRibbonElement.md)||  
|[CMFCPopupMenu::GetParentToolBar](../Topic/CMFCPopupMenu::GetParentToolBar.md)|會將指標傳至父代 \(Parent\) 工具列。|  
|[CMFCPopupMenu::GetQuickCustomizeType](../Topic/CMFCPopupMenu::GetQuickCustomizeType.md)||  
|[CMFCPopupMenu::GetSelItem](../Topic/CMFCPopupMenu::GetSelItem.md)|傳回指向目前選取的功能表命令。|  
|[CMFCPopupMenu::HasBeenResized](../Topic/CMFCPopupMenu::HasBeenResized.md)||  
|[CMFCPopupMenu::HideRarelyUsedCommands](../Topic/CMFCPopupMenu::HideRarelyUsedCommands.md)|表示快顯功能表是否能隱藏較不常用的命令。|  
|[CMFCPopupMenu::InCommand](../Topic/CMFCPopupMenu::InCommand.md)||  
|[CMFCPopupMenu::InsertItem](../Topic/CMFCPopupMenu::InsertItem.md)|將新的項目插入至快顯功能表中的指定位置。|  
|[CMFCPopupMenu::InsertSeparator](../Topic/CMFCPopupMenu::InsertSeparator.md)|插入分隔符號插入快顯功能表中的指定位置。|  
|[CMFCPopupMenu::IsAlwaysClose](../Topic/CMFCPopupMenu::IsAlwaysClose.md)||  
|[CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry](../Topic/CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry.md)||  
|[CMFCPopupMenu::IsCustomizePane](../Topic/CMFCPopupMenu::IsCustomizePane.md)|表示快顯功能表是做為 \[**QuickCustomizePane**\]。|  
|[CMFCPopupMenu::IsEscClose](../Topic/CMFCPopupMenu::IsEscClose.md)||  
|[CMFCPopupMenu::IsIdle](../Topic/CMFCPopupMenu::IsIdle.md)|表示快顯功能表目前是否處於閒置狀態。|  
|[CMFCPopupMenu::IsMenuSound](../Topic/CMFCPopupMenu::IsMenuSound.md)||  
|[CMFCPopupMenu::IsQuickCustomize](../Topic/CMFCPopupMenu::IsQuickCustomize.md)|判斷相關聯的 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) 是否在 QuickCustomize 模式。|  
|[CMFCPopupMenu::IsResizeble](../Topic/CMFCPopupMenu::IsResizeble.md)||  
|[CMFCPopupMenu::IsRightAlign](../Topic/CMFCPopupMenu::IsRightAlign.md)|指出功能表是否為靠右對齊或靠左對齊。|  
|[CMFCPopupMenu::IsScrollable](../Topic/CMFCPopupMenu::IsScrollable.md)||  
|[CMFCPopupMenu::IsSendMenuSelectMsg](../Topic/CMFCPopupMenu::IsSendMenuSelectMsg.md)|表示此框架是否告知父框架，當使用者選取命令從快顯功能表。|  
|[CMFCPopupMenu::IsShown](../Topic/CMFCPopupMenu::IsShown.md)|表示快顯功能表目前是否為可見的。|  
|[CMFCPopupMenu::MoveTo](../Topic/CMFCPopupMenu::MoveTo.md)||  
|[CMFCPopupMenu::OnCmdMsg](../Topic/CMFCPopupMenu::OnCmdMsg.md)|\(覆寫 `CFrameWnd::OnCmdMsg`\)。|  
|[CMFCPopupMenu::PostCommand](../Topic/CMFCPopupMenu::PostCommand.md)||  
|[CMFCPopupMenu::PreTranslateMessage](../Topic/CMFCPopupMenu::PreTranslateMessage.md)|\(覆寫 `CFrameWnd::PreTranslateMessage`\)。|  
|[CMFCPopupMenu::RecalcLayout](../Topic/CMFCPopupMenu::RecalcLayout.md)|呼叫框架，其在標準控制列切換為開啟或關閉，或當框架視窗調整大小。  \(覆寫 [CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md)\)。|  
|[CMFCPopupMenu::RemoveAllItems](../Topic/CMFCPopupMenu::RemoveAllItems.md)|清除快顯功能表的所有項目。|  
|[CMFCPopupMenu::RemoveItem](../Topic/CMFCPopupMenu::RemoveItem.md)|從快顯功能表中移除指定的項目。|  
|[CMFCPopupMenu::SaveState](../Topic/CMFCPopupMenu::SaveState.md)||  
|[CMFCPopupMenu::SetAnimationSpeed](../Topic/CMFCPopupMenu::SetAnimationSpeed.md)|設定快顯功能表的動畫速度。|  
|[CMFCPopupMenu::SetAnimationType](../Topic/CMFCPopupMenu::SetAnimationType.md)|設定快顯功能表的動畫型別。|  
|[CMFCPopupMenu::SetAutoDestroy](../Topic/CMFCPopupMenu::SetAutoDestroy.md)||  
|[CMFCPopupMenu::SetDefaultItem](../Topic/CMFCPopupMenu::SetDefaultItem.md)|設定快顯功能表的預設命令。|  
|[CMFCPopupMenu::SetForceMenuFocus](../Topic/CMFCPopupMenu::SetForceMenuFocus.md)|在快顯功能表時，強制輸入焦點回到功能表列。|  
|[CMFCPopupMenu::SetForceShadow](../Topic/CMFCPopupMenu::SetForceShadow.md)|在快顯功能表在主要畫面格時，會強制架構繪製功能表陰影。|  
|[CMFCPopupMenu::SetMaxWidth](../Topic/CMFCPopupMenu::SetMaxWidth.md)|設定快顯功能表的最大寬度。|  
|[CMFCPopupMenu::SetMessageWnd](../Topic/CMFCPopupMenu::SetMessageWnd.md)||  
|[CMFCPopupMenu::SetParentRibbonElement](../Topic/CMFCPopupMenu::SetParentRibbonElement.md)||  
|[CMFCPopupMenu::SetQuickCustomizeType](../Topic/CMFCPopupMenu::SetQuickCustomizeType.md)||  
|[CMFCPopupMenu::SetQuickMode](../Topic/CMFCPopupMenu::SetQuickMode.md)||  
|[CMFCPopupMenu::SetRightAlign](../Topic/CMFCPopupMenu::SetRightAlign.md)|設定快顯功能表的功能表對齊。|  
|[CMFCPopupMenu::SetSendMenuSelectMsg](../Topic/CMFCPopupMenu::SetSendMenuSelectMsg.md)|設定控制項的旗標快顯功能表是否告知其父框架，當使用者選取命令時。|  
|[CMFCPopupMenu::ShowAllCommands](../Topic/CMFCPopupMenu::ShowAllCommands.md)|強制快顯功能表會顯示所有命令。|  
|[CMFCPopupMenu::TriggerResize](../Topic/CMFCPopupMenu::TriggerResize.md)||  
|[CMFCPopupMenu::UpdateAllShadows](../Topic/CMFCPopupMenu::UpdateAllShadows.md)|更新所有開啟的快顯功能表的陰影。|  
|[CMFCPopupMenu::UpdateShadow](../Topic/CMFCPopupMenu::UpdateShadow.md)|更新快顯功能表的陰影。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPopupMenu::CreateTearOffBar](../Topic/CMFCPopupMenu::CreateTearOffBar.md)||  
|[CMFCPopupMenu::OnChangeHot](../Topic/CMFCPopupMenu::OnChangeHot.md)||  
|[CMFCPopupMenu::OnChooseItem](../Topic/CMFCPopupMenu::OnChooseItem.md)||  
  
### 備註  
 通常， MFC 會自動建立快顯功能表。  如果您想要手動建立 `CMFCPopupMenu` 物件，請將一堆積會呼叫 [CMFCPopupMenu::Create](../Topic/CMFCPopupMenu::Create.md)。  
  
## 範例  
 下列範例示範如何設定快顯功能表物件。  在快顯功能表在主要畫面格外觀之外，設定最大寬度，並設定快顯功能表的正確的功能表對齊時，這個範例顯示如何設定標誌和快顯功能表的音效，設定這個動畫速度和型別，繪製功能表陰影。  這個程式碼片段是 [自訂呼叫範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_CustomPages#2](../../mfc/reference/codesnippet/CPP/cmfcpopupmenu-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
## 需求  
 **標題:** afxpopupmenu.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md)