---
title: "CMFCTasksPane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPane class"
ms.assetid: b456328e-2525-4642-b78b-9edd1a1a7d3f
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCTasksPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 `CMFCTasksPane` 類別會實作可點選式項目 \(工作\) 清單。  
  
## 語法  
  
```  
class CMFCTasksPane : public CDockablePane  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPane::CMFCTasksPane](../Topic/CMFCTasksPane::CMFCTasksPane.md)|建構 `CMFCTasksPane` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPane::AddGroup](../Topic/CMFCTasksPane::AddGroup.md)|將新的工作群組加入至工作窗格控制項。|  
|[CMFCTasksPane::AddLabel](../Topic/CMFCTasksPane::AddLabel.md)|將新的靜態標籤加入至指定的工作群組。|  
|[CMFCTasksPane::AddMRUFilesList](../Topic/CMFCTasksPane::AddMRUFilesList.md)|將最近使用的 \(MRU\) 檔案清單所指定的工作加入到群組。|  
|[CMFCTasksPane::AddPage](../Topic/CMFCTasksPane::AddPage.md)|將新頁面加入工作窗格。|  
|[CMFCTasksPane::AddSeparator](../Topic/CMFCTasksPane::AddSeparator.md)||  
|[CMFCTasksPane::AddTask](../Topic/CMFCTasksPane::AddTask.md)|將新工作加入至指定的工作群組。|  
|[CMFCTasksPane::AddWindow](../Topic/CMFCTasksPane::AddWindow.md)|將子視窗加入工作窗格。|  
|[CMFCTasksPane::CollapseAllGroups](../Topic/CMFCTasksPane::CollapseAllGroups.md)||  
|[CMFCTasksPane::CollapseGroup](../Topic/CMFCTasksPane::CollapseGroup.md)|以程式設計方式摺疊群組。|  
|[CMFCTasksPane::CreateDefaultMiniframe](../Topic/CMFCTasksPane::CreateDefaultMiniframe.md)|\(覆寫 [CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md)。\)|  
|[CMFCTasksPane::CreateMenu](../Topic/CMFCTasksPane::CreateMenu.md)|由架構呼叫來建立 \[**其他工作窗格**\] 功能表按鈕的功能表。|  
|[CMFCTasksPane::EnableAnimation](../Topic/CMFCTasksPane::EnableAnimation.md)|啟用或停用摺疊或展開工作群組時的動畫。|  
|[CMFCTasksPane::EnableGroupCollapse](../Topic/CMFCTasksPane::EnableGroupCollapse.md)|指定是否可以摺疊工作群組。|  
|[CMFCTasksPane::EnableHistoryMenuButtons](../Topic/CMFCTasksPane::EnableHistoryMenuButtons.md)|啟用或停用 \[**下一步**\] 和 \[**上一步**\] 瀏覽按鈕中的下拉式功能表。|  
|[CMFCTasksPane::EnableNavigationToolbar](../Topic/CMFCTasksPane::EnableNavigationToolbar.md)|啟用或停用導覽工具列。|  
|[CMFCTasksPane::EnableOffsetCustomControls](../Topic/CMFCTasksPane::EnableOffsetCustomControls.md)||  
|[CMFCTasksPane::EnableScrollButtons](../Topic/CMFCTasksPane::EnableScrollButtons.md)|啟用捲動按鈕而非捲軸。|  
|[CMFCTasksPane::EnableWrapLabels](../Topic/CMFCTasksPane::EnableWrapLabels.md)|啟用或停用標籤的自動換行。|  
|[CMFCTasksPane::EnableWrapTasks](../Topic/CMFCTasksPane::EnableWrapTasks.md)|啟用或停用工作的自動換行。|  
|[CMFCTasksPane::GetActivePage](../Topic/CMFCTasksPane::GetActivePage.md)|傳回使用中頁面以零為基底的索引。|  
|[CMFCTasksPane::GetGroupCaptionHeight](../Topic/CMFCTasksPane::GetGroupCaptionHeight.md)|傳回群組標題的高度。|  
|[CMFCTasksPane::GetGroupCaptionHorzOffset](../Topic/CMFCTasksPane::GetGroupCaptionHorzOffset.md)|傳回群組標題距離工作窗格的左邊緣和右邊緣的目前位移。|  
|[CMFCTasksPane::GetGroupCaptionVertOffset](../Topic/CMFCTasksPane::GetGroupCaptionVertOffset.md)|傳回群組標題距離工作窗格的上邊緣和下邊緣的目前位移。|  
|[CMFCTasksPane::GetGroupCount](../Topic/CMFCTasksPane::GetGroupCount.md)|傳回群組總數。|  
|[CMFCTasksPane::GetGroupLocation](../Topic/CMFCTasksPane::GetGroupLocation.md)|傳回特定群組的內部群組索引。|  
|[CMFCTasksPane::GetGroupVertOffset](../Topic/CMFCTasksPane::GetGroupVertOffset.md)|傳回群組的垂直位移。|  
|[CMFCTasksPane::GetHorzMargin](../Topic/CMFCTasksPane::GetHorzMargin.md)|傳回工作窗格與用戶端區域邊緣之間的水平間距。|  
|[CMFCTasksPane::GetNextPages](../Topic/CMFCTasksPane::GetNextPages.md)||  
|[CMFCTasksPane::GetPageByGroup](../Topic/CMFCTasksPane::GetPageByGroup.md)|擷取指定之群組的頁面索引。|  
|[CMFCTasksPane::GetPagesCount](../Topic/CMFCTasksPane::GetPagesCount.md)|傳回頁數。|  
|[CMFCTasksPane::GetPreviousPages](../Topic/CMFCTasksPane::GetPreviousPages.md)||  
|[CMFCTasksPane::GetScrollBarCtrl](../Topic/CMFCTasksPane::GetScrollBarCtrl.md)|\(覆寫 [CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)。\)|  
|[CMFCTasksPane::GetTask](../Topic/CMFCTasksPane::GetTask.md)|擷取工作。|  
|[CMFCTasksPane::GetTaskCount](../Topic/CMFCTasksPane::GetTaskCount.md)|傳回指定群組中工作項目的數目。|  
|[CMFCTasksPane::GetTaskGroup](../Topic/CMFCTasksPane::GetTaskGroup.md)|傳回給定之群組索引的工作群組。|  
|[CMFCTasksPane::GetTaskLocation](../Topic/CMFCTasksPane::GetTaskLocation.md)|傳回特定工作的群組與索引。|  
|[CMFCTasksPane::GetTasksHorzOffset](../Topic/CMFCTasksPane::GetTasksHorzOffset.md)|傳回工作距離其父群組的左邊緣和右邊緣的水平位移。|  
|[CMFCTasksPane::GetTasksIconHorzOffset](../Topic/CMFCTasksPane::GetTasksIconHorzOffset.md)||  
|[CMFCTasksPane::GetTasksIconVertOffset](../Topic/CMFCTasksPane::GetTasksIconVertOffset.md)||  
|[CMFCTasksPane::GetVertMargin](../Topic/CMFCTasksPane::GetVertMargin.md)|傳回工作窗格與用戶端區域邊緣之間的垂直間距。|  
|[CMFCTasksPane::IsAccessibilityCompatible](../Topic/CMFCTasksPane::IsAccessibilityCompatible.md)|\(覆寫 `CDockablePane::IsAccessibilityCompatible`。\)|  
|[CMFCTasksPane::IsAnimationEnabled](../Topic/CMFCTasksPane::IsAnimationEnabled.md)|指出是否啟用動畫。|  
|[CMFCTasksPane::IsBackButtonEnabled](../Topic/CMFCTasksPane::IsBackButtonEnabled.md)|指出是否啟用上一頁按鈕。|  
|[CMFCTasksPane::IsForwardButtonEnabled](../Topic/CMFCTasksPane::IsForwardButtonEnabled.md)|指出是否啟用下一頁按鈕。|  
|[CMFCTasksPane::IsGroupCollapseEnabled](../Topic/CMFCTasksPane::IsGroupCollapseEnabled.md)||  
|[CMFCTasksPane::IsHistoryMenuButtonsEnabled](../Topic/CMFCTasksPane::IsHistoryMenuButtonsEnabled.md)|指出 \[**下一步**\] 和 \[**上一步**\] 瀏覽按鈕是否有下拉式功能表。|  
|[CMFCTasksPane::IsNavigationToolbarEnabled](../Topic/CMFCTasksPane::IsNavigationToolbarEnabled.md)|指出是否啟用導覽工具列。|  
|[CMFCTasksPane::IsToolBox](../Topic/CMFCTasksPane::IsToolBox.md)||  
|[CMFCTasksPane::IsWrapLabelsEnabled](../Topic/CMFCTasksPane::IsWrapLabelsEnabled.md)|指出工作窗格的標籤中是否自動換行。|  
|[CMFCTasksPane::IsWrapTasksEnabled](../Topic/CMFCTasksPane::IsWrapTasksEnabled.md)|指出工作窗格的工作中是否自動換行。|  
|[CMFCTasksPane::LoadState](../Topic/CMFCTasksPane::LoadState.md)|\(覆寫 [CDockablePane::LoadState](http://msdn.microsoft.com/zh-tw/96110136-4f46-4764-8a76-3b4abaf77917)。\)|  
|[CMFCTasksPane::OnCancel](../Topic/CMFCTasksPane::OnCancel.md)||  
|[CMFCTasksPane::OnClickTask](../Topic/CMFCTasksPane::OnClickTask.md)|使用者按一下工作窗格中的項目時由架構呼叫。|  
|[CMFCTasksPane::OnOK](../Topic/CMFCTasksPane::OnOK.md)||  
|[CMFCTasksPane::OnPressBackButton](../Topic/CMFCTasksPane::OnPressBackButton.md)|使用者按一下上一頁按鈕時由架構呼叫。|  
|[CMFCTasksPane::OnPressForwardButton](../Topic/CMFCTasksPane::OnPressForwardButton.md)|使用者按一下上一步瀏覽按鈕時由架構呼叫。|  
|[CMFCTasksPane::OnPressHomeButton](../Topic/CMFCTasksPane::OnPressHomeButton.md)|使用者按一下首頁瀏覽按鈕時由架構呼叫|  
|[CMFCTasksPane::OnPressOtherButton](../Topic/CMFCTasksPane::OnPressOtherButton.md)||  
|[CMFCTasksPane::OnSetAccData](../Topic/CMFCTasksPane::OnSetAccData.md)|\(覆寫 [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md).\)|  
|[CMFCTasksPane::OnUpdateCmdUI](../Topic/CMFCTasksPane::OnUpdateCmdUI.md)|\(覆寫 [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/zh-tw/5dd61606-1c12-40d4-b024-f3839aa5e2e0)。\)|  
|[CMFCTasksPane::PreTranslateMessage](../Topic/CMFCTasksPane::PreTranslateMessage.md)|\(覆寫 [CDockablePane::PreTranslateMessage](http://msdn.microsoft.com/zh-tw/49a242cc-b158-400e-9e01-0345ec9c3ffd)。\)|  
|[CMFCTasksPane::RecalcLayout](../Topic/CMFCTasksPane::RecalcLayout.md)|\(覆寫 [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md).\)|  
|[CMFCTasksPane::RemoveAllGroups](../Topic/CMFCTasksPane::RemoveAllGroups.md)|移除指定之頁面上的所有群組。|  
|[CMFCTasksPane::RemoveAllPages](../Topic/CMFCTasksPane::RemoveAllPages.md)|從工作窗格中移除所有頁面，預設 \(第一頁\) 頁面除外。|  
|[CMFCTasksPane::RemoveAllTasks](../Topic/CMFCTasksPane::RemoveAllTasks.md)|從群組中移除所有工作。|  
|[CMFCTasksPane::RemoveGroup](../Topic/CMFCTasksPane::RemoveGroup.md)|移除群組。|  
|[CMFCTasksPane::RemovePage](../Topic/CMFCTasksPane::RemovePage.md)|從工作窗格移除指定的頁面。|  
|[CMFCTasksPane::RemoveTask](../Topic/CMFCTasksPane::RemoveTask.md)|從工作群組中移除工作。|  
|[CMFCTasksPane::SaveState](../Topic/CMFCTasksPane::SaveState.md)|\(覆寫 [CDockablePane::SaveState](http://msdn.microsoft.com/zh-tw/c5c24249-8d0d-46cb-96d9-9f5c6dc191db)。\)|  
|[CMFCTasksPane::Serialize](../Topic/CMFCTasksPane::Serialize.md)|\(覆寫 [CDockablePane::Serialize](http://msdn.microsoft.com/zh-tw/09787e59-e446-4e76-894b-206d303dcfd6)。\)|  
|[CMFCTasksPane::SetActivePage](../Topic/CMFCTasksPane::SetActivePage.md)|啟動工作窗格中指定的頁面。|  
|[CMFCTasksPane::SetCaption](../Topic/CMFCTasksPane::SetCaption.md)|設定工作窗格的標題名稱。|  
|[CMFCTasksPane::SetGroupCaptionHeight](../Topic/CMFCTasksPane::SetGroupCaptionHeight.md)|設定群組標題的高度。|  
|[CMFCTasksPane::SetGroupCaptionHorzOffset](../Topic/CMFCTasksPane::SetGroupCaptionHorzOffset.md)|設定群組標題的水平位移。|  
|[CMFCTasksPane::SetGroupCaptionVertOffset](../Topic/CMFCTasksPane::SetGroupCaptionVertOffset.md)|設定群組標題的垂直位移。|  
|[CMFCTasksPane::SetGroupName](../Topic/CMFCTasksPane::SetGroupName.md)|設定群組名稱。|  
|[CMFCTasksPane::SetGroupTextColor](../Topic/CMFCTasksPane::SetGroupTextColor.md)|設定群組標題的文字色彩。|  
|[CMFCTasksPane::SetGroupVertOffset](../Topic/CMFCTasksPane::SetGroupVertOffset.md)|設定群組的垂直位移。|  
|[CMFCTasksPane::SetHorzMargin](../Topic/CMFCTasksPane::SetHorzMargin.md)|設定工作窗格與用戶端區域邊緣之間的水平間距。|  
|[CMFCTasksPane::SetIconsList](../Topic/CMFCTasksPane::SetIconsList.md)|設定與工作相關聯的影像清單。|  
|[CMFCTasksPane::SetPageCaption](../Topic/CMFCTasksPane::SetPageCaption.md)|設定工作窗格頁面的標題文字。|  
|[CMFCTasksPane::SetTaskName](../Topic/CMFCTasksPane::SetTaskName.md)|設定工作的名稱。|  
|[CMFCTasksPane::SetTasksIconHorzOffset](../Topic/CMFCTasksPane::SetTasksIconHorzOffset.md)||  
|[CMFCTasksPane::SetTasksIconVertOffset](../Topic/CMFCTasksPane::SetTasksIconVertOffset.md)||  
|[CMFCTasksPane::SetTaskTextColor](../Topic/CMFCTasksPane::SetTaskTextColor.md)|設定工作的文字色彩。|  
|[CMFCTasksPane::SetTasksHorzOffset](../Topic/CMFCTasksPane::SetTasksHorzOffset.md)|設定工作距離其父群組的左邊緣和右邊緣的水平位移。|  
|[CMFCTasksPane::SetVertMargin](../Topic/CMFCTasksPane::SetVertMargin.md)|設定工作窗格與用戶端區域邊緣之間的垂直間距。|  
|[CMFCTasksPane::SetWindowHeight](../Topic/CMFCTasksPane::SetWindowHeight.md)|設定視窗的高度。|  
|[CMFCTasksPane::ShowCommandMessageString](../Topic/CMFCTasksPane::ShowCommandMessageString.md)||  
|[CMFCTasksPane::ShowTask](../Topic/CMFCTasksPane::ShowTask.md)|顯示或隱藏工作。|  
|[CMFCTasksPane::ShowTaskByCmdId](../Topic/CMFCTasksPane::ShowTaskByCmdId.md)|根據其命令識別碼顯示或隱藏工作。|  
|[CMFCTasksPane::Update](../Topic/CMFCTasksPane::Update.md)|更新屬於工作窗格的 GUI 項目。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTasksPane::OnActivateTasksPanePage](../Topic/CMFCTasksPane::OnActivateTasksPanePage.md)|啟動新工作窗格頁面時，由架構呼叫。|  
  
## 備註  
 `CMFCTasksPane` 類別會實作下列功能：  
  
-   項目可以組成群組，而且每個項目群組可以有相關聯的標題。  
  
-   可摺疊或展開項目群組。  
  
-   圖示可以指派給工作窗格中的每個項目。  
  
-   個別項目可以與使用者按一下項目時執行的命令識別碼相關聯。  按一下發生時，`WM_COMMAND` 訊息會傳送至工作窗格控制項的擁有者。  
  
 若要在您的應用程式中使用 `CMFCTasksPane` 控制項，請遵循下列步驟：  
  
1.  內嵌 `CMFCTasksPane` 物件到主框架視窗類別。  
  
2.  處理 `WM_CREATE` 訊息資訊時，呼叫 `Create` 方法。  您可以使用一般 [CControlBar](../../mfc/reference/ccontrolbar-class.md) 樣式。  如需詳細資訊，請參閱`CControlBar::Create`。  
  
3.  呼叫 [CMFCTasksPane::AddGroup](../Topic/CMFCTasksPane::AddGroup.md) 方法來加入各種群組。  
  
4.  呼叫 [CMFCTasksPane::AddTask](../Topic/CMFCTasksPane::AddTask.md)、[CMFCTasksPane::AddLabel](../Topic/CMFCTasksPane::AddLabel.md) 或 [CMFCTasksPane::AddMRUFilesList](../Topic/CMFCTasksPane::AddMRUFilesList.md) 成員函式，將新的項目 \(工作\) 加入每個群組。  
  
5.  呼叫 [CMFCTasksPane::EnableGroupCollapse](../Topic/CMFCTasksPane::EnableGroupCollapse.md) 來指定是否可以摺疊項目群組。  
  
 下圖顯示典型的工作窗格控制項。  第一個群組是*特殊*群組，它的標題是較深的色彩。  第三個群組會摺疊。  最後一個群組會與工作窗格的底端對齊，並且沒有標題，而群組中的最後一個工作是簡單的標籤：  
  
 ![工作窗格範例](../Image/NextTaskPane.png "NextTaskPane")  
  
 您可以藉由調整各種邊界和位移來自訂工作窗格的外觀。  下圖將釐清這些變數的意義：  
  
 ![自訂工作群組](../Image/NextTaskGrpCustom.png "NextTaskGrpCustom")  
  
## 範例  
 下列範例示範如何建構 `CMFCTasksPane` 物件，以及使用 `CMFCTasksPane` 類別中的各種方法。  此範例示範如何啟用工作群組的摺疊、啟用 \[**下一步**\] 和 \[**上一頁**\] 瀏覽按鈕上的下拉式功能表、啟用捲動按鈕而非捲軸、啟用標籤中文字的自動換行、設定工作窗格的標題名稱、設定群組標題的文字色彩，以及設定水平和垂直邊界。  
  
 [!code-cpp[NVC_MFC_RibbonApp#28](../../mfc/reference/codesnippet/CPP/cmfctaskspane-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)  
  
## 需求  
 **標頭：**afxTasksPane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md)   
 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)