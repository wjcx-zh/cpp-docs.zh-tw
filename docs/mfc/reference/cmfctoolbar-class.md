---
title: "CMFCToolBar Class | Microsoft Docs"
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
  - "CMFCToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBar class"
ms.assetid: e7679c01-fb94-44c0-98c6-3af955292fb5
caps.latest.revision: 48
caps.handback.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCToolBar` 類別與 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)，不過，提供使用者介面功能提供額外支援。  這些包括一般工具列、工具列具有作用中的影像，大圖示、頁面巡覽區按鈕、鎖定的工具列、Rebar 控制項、文字在影像的下方，背景影像和定位的工具列。  `CMFCToolBar` 類別也包含可停駐工具列和功能表之間的支援工具列和功能表的使用者自訂，拖放，下拉式方塊按鈕、編輯方塊按鈕、色彩選擇器和彙總按鈕。  
  
## 語法  
  
```  
class CMFCToolBar : public CMFCBaseToolBar  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCToolBar::CMFCToolBar`|預設建構函式。|  
|`CMFCToolBar::~CMFCToolBar`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBar::AddBasicCommand](../Topic/CMFCToolBar::AddBasicCommand.md)|將功能表命令加入至永遠顯示命令的清單，當使用者按一下  功能表時。|  
|[CMFCToolBar::AddCommandUsage](../Topic/CMFCToolBar::AddCommandUsage.md)|會將與給定的命令計數器。|  
|[CMFCToolBar::AddToolBarForImageCollection](../Topic/CMFCToolBar::AddToolBarForImageCollection.md)|從使用者介面資源將影像加入至影像的集合在應用程式中。|  
|[CMFCToolBar::AdjustLayout](../Topic/CMFCToolBar::AdjustLayout.md)|重新計算工具列的大小和位置。  \(覆寫 [CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)\)。|  
|[CMFCToolBar::AdjustSize](../Topic/CMFCToolBar::AdjustSize.md)|重新計算工具列大小。|  
|[CMFCToolBar::AllowChangeTextLabels](../Topic/CMFCToolBar::AllowChangeTextLabels.md)|指定文字標籤是否可以顯示在工具列按鈕的影像的下方。|  
|[CMFCToolBar::AreTextLabels](../Topic/CMFCToolBar::AreTextLabels.md)|指定在影像中的文字標籤是在工具列按鈕目前是否顯示。|  
|[CMFCToolBar::AutoGrayInactiveImages](../Topic/CMFCToolBar::AutoGrayInactiveImages.md)|啟用或停用非現用的按鈕影像的自動產生。|  
|[CMFCToolBar::ButtonToIndex](../Topic/CMFCToolBar::ButtonToIndex.md)|傳回指定之物件的索引 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) 位於這個工具列上的。|  
|[CMFCToolBar::CalcFixedLayout](../Topic/CMFCToolBar::CalcFixedLayout.md)|計算工具列的水平大小。  \(覆寫 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)\)。|  
|[CMFCToolBar::CalcSize](../Topic/CMFCToolBar::CalcSize.md)|呼叫框架做為配置計算處理序的一部分。  \(覆寫 [CPane::CalcSize](../Topic/CPane::CalcSize.md)\)。|  
|[CMFCToolBar::CanHandleSiblings](../Topic/CMFCToolBar::CanHandleSiblings.md)|決定工具列及其同層級是否在同一個窗格上。|  
|[CMFCToolBar::CleanUpImages](../Topic/CMFCToolBar::CleanUpImages.md)|釋放為工具列影像配置的系統資源。|  
|[CMFCToolBar::CleanUpLockedImages](../Topic/CMFCToolBar::CleanUpLockedImages.md)|來釋放鎖定的工具列影像配置的系統資源。|  
|[CMFCToolBar::CanBeClosed](../Topic/CMFCToolBar::CanBeClosed.md)|指定使用者是否可以關閉工具列。  \(覆寫 [CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)\)。|  
|[CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md)|決定系統是否可以還原工具列到原來的狀態在自訂之後。|  
|[CMFCToolBar::CanFocus](../Topic/CMFCToolBar::CanFocus.md)|指定窗格是否可以接收焦點。  \(覆寫 [CBasePane::CanFocus](../Topic/CBasePane::CanFocus.md)\)。|  
|[CMFCToolBar::CanHandleSiblings](../Topic/CMFCToolBar::CanHandleSiblings.md)|決定工具列及其同層級是否在同一個窗格上。|  
|[CMFCToolBar::CommandToIndex](../Topic/CMFCToolBar::CommandToIndex.md)|傳回按鈕的索引會在工具列上的這個執行個體具有指定的命令 ID 的 .|  
|[CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md)|建立 `CMFCToolBar` 物件。|  
|[CMFCToolBar::CreateEx](../Topic/CMFCToolBar::CreateEx.md)|建立使用其他樣式選項的 `CMFCToolBar` 物件，例如大型圖示。|  
|[CMFCToolBar::Deactivate](../Topic/CMFCToolBar::Deactivate.md)|停用工具列。|  
|[CMFCToolBar::EnableCustomizeButton](../Topic/CMFCToolBar::EnableCustomizeButton.md)|啟用或停用顯示於工具列尾端的 \[**加入或移除按鈕**\] 按鈕。|  
|[CMFCToolBar::EnableDocking](../Topic/CMFCToolBar::EnableDocking.md)|啟用窗格的停駐到主要畫面格。  \(覆寫 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)\)。|  
|[CMFCToolBar::EnableLargeIcons](../Topic/CMFCToolBar::EnableLargeIcons.md)|啟用或停用  工具列按鈕的大圖示。|  
|[CMFCToolBar::EnableQuickCustomization](../Topic/CMFCToolBar::EnableQuickCustomization.md)|啟用或停用  工具列的快速自訂，以便讓使用者可以按 \[**Alt**\] 鍵和按鈕拖曳至新位置。|  
|[CMFCToolBar::EnableReflections](../Topic/CMFCToolBar::EnableReflections.md)|啟用或停用命令反映。|  
|[CMFCToolBar::EnableTextLabels](../Topic/CMFCToolBar::EnableTextLabels.md)|啟用或停用文字標籤在工具列按鈕影像的下方。|  
|[CMFCToolBar::FromHandlePermanent](../Topic/CMFCToolBar::FromHandlePermanent.md)|擷取指標包含指定的視窗控制代碼的 `CMFCToolBar` 物件。|  
|[CMFCToolBar::GetAllButtons](../Topic/CMFCToolBar::GetAllButtons.md)|傳回在工具列上的  按鈕的唯讀清單。|  
|[CMFCToolBar::GetAllToolbars](../Topic/CMFCToolBar::GetAllToolbars.md)|傳回在應用程式中所有工具列的唯讀清單。|  
|[CMFCToolBar::GetBasicCommands](../Topic/CMFCToolBar::GetBasicCommands.md)|傳回在應用程式定義的基本命令的唯讀清單。|  
|[CMFCToolBar::GetButton](../Topic/CMFCToolBar::GetButton.md)|傳回指向具有指定的工具列按鈕的索引 `CMFCToolBarButton` 物件。|  
|[CMFCToolBar::GetButtonInfo](../Topic/CMFCToolBar::GetButtonInfo.md)|會傳回按鈕的命令 ID、樣式和影像索引位於指定索引的。|  
|[CMFCToolBar::GetButtonSize](../Topic/CMFCToolBar::GetButtonSize.md)|傳回維度在工具列上的每個按鈕。|  
|[CMFCToolBar::GetButtonStyle](../Topic/CMFCToolBar::GetButtonStyle.md)|傳回位於指定索引處的工具列按鈕的目前樣式。|  
|[CMFCToolBar::GetButtonText](../Topic/CMFCToolBar::GetButtonText.md)|傳回具有指定索引的按鈕的文字標籤。|  
|[CMFCToolBar::GetColdImages](../Topic/CMFCToolBar::GetColdImages.md)|傳回指向冷工具列按鈕影像的集合在應用程式中。|  
|[CMFCToolBar::GetColumnWidth](../Topic/CMFCToolBar::GetColumnWidth.md)|傳回工具列按鈕的寬度。|  
|[CMFCToolBar::GetCommandButtons](../Topic/CMFCToolBar::GetCommandButtons.md)|傳回所有具有從工具列的指定命令 ID 在應用程式中按鈕的清單。|  
|[CMFCToolBar::GetCount](../Topic/CMFCToolBar::GetCount.md)|傳回按鈕和分隔符號數目工具列。|  
|[CMFCToolBar::GetCustomizeButton](../Topic/CMFCToolBar::GetCustomizeButton.md)|擷取指標與工具列的 `CMFCCustomizeButton` 物件。|  
|[CMFCToolBar::GetDefaultImage](../Topic/CMFCToolBar::GetDefaultImage.md)|傳回預設影像之索引鍵的工具列按鈕的這個執行個體具有指定的命令 ID 的 .|  
|[CMFCToolBar::GetDisabledImages](../Topic/CMFCToolBar::GetDisabledImages.md)|傳回指向是停用的工具列按鈕使用在應用程式的影像集合。|  
|[CMFCToolBar::GetDisabledMenuImages](../Topic/CMFCToolBar::GetDisabledMenuImages.md)|傳回指向會停用功能表上的  按鈕會使用應用程式的影像集合。|  
|[CMFCToolBar::GetDroppedDownMenu](../Topic/CMFCToolBar::GetDroppedDownMenu.md)|擷取指標目前顯示它的子功能表的功能表按鈕物件。|  
|[CMFCToolBar::GetGrayDisabledButtons](../Topic/CMFCToolBar::GetGrayDisabledButtons.md)|指定要停用按鈕影像是否是標準按鈕影像的呈現暗灰色的版本或接受從停用按鈕影像的集合。|  
|[CMFCToolBar::GetHighlightedButton](../Topic/CMFCToolBar::GetHighlightedButton.md)|會將指標傳至目前反白顯示的工具列按鈕。|  
|[CMFCToolBar::GetHotBorder](../Topic/CMFCToolBar::GetHotBorder.md)|決定工具列按鈕的色彩。|  
|[CMFCToolBar::GetHotTextColor](../Topic/CMFCToolBar::GetHotTextColor.md)|傳回反白顯示的工具列按鈕的文字色彩。|  
|[CMFCToolBar::GetHwndLastFocus](../Topic/CMFCToolBar::GetHwndLastFocus.md)|將控制代碼傳回至具有輸入焦點的視窗，請在工具列之前。|  
|[CMFCToolBar::GetIgnoreSetText](../Topic/CMFCToolBar::GetIgnoreSetText.md)|指定設定的呼叫按鈕標籤是否會被忽略。|  
|[CMFCToolBar::GetImageSize](../Topic/CMFCToolBar::GetImageSize.md)|傳回工具列按鈕影像的目前大小。|  
|[CMFCToolBar::GetImages](../Topic/CMFCToolBar::GetImages.md)|傳回指向儲存在應用程式的預設按鈕影像的集合。|  
|[CMFCToolBar::GetImagesOffset](../Topic/CMFCToolBar::GetImagesOffset.md)|傳回用於索引的位移來尋找這個工具列的工具列按鈕影像在工具列按鈕影像的全域清單。|  
|[CMFCToolBar::GetInvalidateItemRect](../Topic/CMFCToolBar::GetInvalidateItemRect.md)|擷取必須位於指定索引的按鈕重繪工作區的區域。|  
|[CMFCToolBar::GetItemID](../Topic/CMFCToolBar::GetItemID.md)|傳回工具列按鈕的命令 ID 在指定之索引處的。|  
|[CMFCToolBar::GetItemRect](../Topic/CMFCToolBar::GetItemRect.md)|會傳回按鈕的週框 \(Bounding Rectangle\) 中指定之索引處。|  
|[CMFCToolBar::GetLargeColdImages](../Topic/CMFCToolBar::GetLargeColdImages.md)|傳回指向大冷工具列按鈕影像的集合在應用程式中。|  
|[CMFCToolBar::GetLargeDisabledImages](../Topic/CMFCToolBar::GetLargeDisabledImages.md)|傳回指向大停用工具列按鈕影像的集合在應用程式中。|  
|[CMFCToolBar::GetLargeImages](../Topic/CMFCToolBar::GetLargeImages.md)|傳回指向主要工具列按鈕影像的集合在應用程式中。|  
|[CMFCToolBar::GetLockedColdImages](../Topic/CMFCToolBar::GetLockedColdImages.md)|傳回指向鎖定冷影像集合在工具列上的。|  
|[CMFCToolBar::GetLockedDisabledImages](../Topic/CMFCToolBar::GetLockedDisabledImages.md)|傳回指向鎖定的停用影像集合在工具列上的。|  
|[CMFCToolBar::GetLockedImages](../Topic/CMFCToolBar::GetLockedImages.md)|傳回指向鎖定的按鈕影像的集合在工具列上的。|  
|[CMFCToolBar::GetLockedImageSize](../Topic/CMFCToolBar::GetLockedImageSize.md)|傳回鎖定的工具列影像的預設大小。|  
|[CMFCToolBar::GetLockedMenuImages](../Topic/CMFCToolBar::GetLockedMenuImages.md)|傳回指向鎖定的工具列上的  功能表上的影像集合在工具列上的。|  
|[CMFCToolBar::GetMenuButtonSize](../Topic/CMFCToolBar::GetMenuButtonSize.md)|傳回功能表按鈕的大小在應用程式中。|  
|[CMFCToolBar::GetMenuImageSize](../Topic/CMFCToolBar::GetMenuImageSize.md)|傳回功能表在應用程式中的按鈕影像的大小。|  
|[CMFCToolBar::GetMenuImages](../Topic/CMFCToolBar::GetMenuImages.md)|傳回指向功能表在應用程式中的按鈕影像的集合。|  
|[CMFCToolBar::GetOrigButtons](../Topic/CMFCToolBar::GetOrigButtons.md)|擷取工具列的非自訂的按鈕集合。|  
|[CMFCToolBar::GetOrigResetButtons](../Topic/CMFCToolBar::GetOrigResetButtons.md)|擷取工具列的非自訂的重設按鈕的集合。|  
|[CMFCToolBar::GetResourceID](../Topic/CMFCToolBar::GetResourceID.md)|擷取工具列的資源 ID。|  
|[CMFCToolBar::GetRouteCommandsViaFrame](../Topic/CMFCToolBar::GetRouteCommandsViaFrame.md)|判斷哪個物件、父框架或擁有者，將命令加入至工具列。|  
|[CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md)|傳回高度工具列按鈕。|  
|[CMFCToolBar::GetShowTooltips](../Topic/CMFCToolBar::GetShowTooltips.md)|指定工具提示是否根據工具列按鈕顯示。|  
|[CMFCToolBar::GetSiblingToolBar](../Topic/CMFCToolBar::GetSiblingToolBar.md)|擷取工具列的同層級。|  
|[CMFCToolBar::GetUserImages](../Topic/CMFCToolBar::GetUserImages.md)|傳回指向使用者定義的工具列按鈕影像的集合在應用程式中。|  
|[CMFCToolBar::HitTest](../Topic/CMFCToolBar::HitTest.md)|傳回位於指定位置的工具列按鈕的索引。|  
|[CMFCToolBar::InsertButton](../Topic/CMFCToolBar::InsertButton.md)|插入按鈕至工具列。|  
|[CMFCToolBar::InsertSeparator](../Topic/CMFCToolBar::InsertSeparator.md)|插入分隔符號插入工具列。|  
|[CMFCToolBar::InvalidateButton](../Topic/CMFCToolBar::InvalidateButton.md)|失效存在於所提供的索引工具列按鈕的工作區。|  
|[CMFCToolBar::IsAddRemoveQuickCustomize](../Topic/CMFCToolBar::IsAddRemoveQuickCustomize.md)|判斷使用者使用 \[**自訂**\] 功能表選項，即可加入或移除工具列按鈕。|  
|[CMFCToolBar::IsAltCustomizeMode](../Topic/CMFCToolBar::IsAltCustomizeMode.md)|指定 *快取文件層級自訂中* 是否用於拖曳按鈕。|  
|[CMFCToolBar::IsAutoGrayInactiveImages](../Topic/CMFCToolBar::IsAutoGrayInactiveImages.md)|指定非現用 \(非反白顯示的\) 按鈕影像的自動產生是否已啟用。|  
|[CMFCToolBar::IsBasicCommand](../Topic/CMFCToolBar::IsBasicCommand.md)|判斷命令是否在基本的命令清單。|  
|[CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md)|決定工具列是否可以顯示擴充框線按鈕。|  
|[CMFCToolBar::IsButtonHighlighted](../Topic/CMFCToolBar::IsButtonHighlighted.md)|判斷在工具列上的按鈕是否會反白顯示。|  
|[CMFCToolBar::IsCommandPermitted](../Topic/CMFCToolBar::IsCommandPermitted.md)|判斷命令是否允許。|  
|[CMFCToolBar::IsCommandRarelyUsed](../Topic/CMFCToolBar::IsCommandRarelyUsed.md)|判斷是否很少使用命令 \(請參閱 [CMFCToolBar::SetCommandUsageOptions](../Topic/CMFCToolBar::SetCommandUsageOptions.md)\)。|  
|[CMFCToolBar::IsCustomizeMode](../Topic/CMFCToolBar::IsCustomizeMode.md)|指定工具列框架是否在自訂模式。|  
|[CMFCToolBar::IsDragButton](../Topic/CMFCToolBar::IsDragButton.md)|決定工具列按鈕拖曳。|  
|[CMFCToolBar::IsExistCustomizeButton](../Topic/CMFCToolBar::IsExistCustomizeButton.md)|判斷是否包含 \[**自訂**\] 工具列按鈕。|  
|[CMFCToolBar::IsFloating](../Topic/CMFCToolBar::IsFloating.md)|決定工具列是否浮動。|  
|[CMFCToolBar::IsLargeIcons](../Topic/CMFCToolBar::IsLargeIcons.md)|指定應用程式的工具列目前是否顯示大圖示。|  
|[CMFCToolBar::IsLastCommandFromButton](../Topic/CMFCToolBar::IsLastCommandFromButton.md)|判斷這個最近執行命令是從指定的工具列按鈕會傳送。|  
|[CMFCToolBar::IsLocked](../Topic/CMFCToolBar::IsLocked.md)|決定工具列是否已鎖定。|  
|[CMFCToolBar::IsOneRowWithSibling](../Topic/CMFCToolBar::IsOneRowWithSibling.md)|決定工具列及其同層級工具列是否在同一資料列上。|  
|[CMFCToolBar::IsUserDefined](../Topic/CMFCToolBar::IsUserDefined.md)|指定工具列是否為使用者定義。|  
|[CMFCToolBar::LoadBitmap](../Topic/CMFCToolBar::LoadBitmap.md)|從應用程式的資源載入工具列影像。|  
|[CMFCToolBar::LoadBitmapEx](../Topic/CMFCToolBar::LoadBitmapEx.md)|從應用程式的資源載入工具列影像。  包含大型影像。|  
|[CMFCToolBar::LoadParameters](../Topic/CMFCToolBar::LoadParameters.md)|從 Windows 登錄載入全域工具列上選取 。|  
|[CMFCToolBar::LoadState](../Topic/CMFCToolBar::LoadState.md)|從 Windows 登錄裝載工具列的狀態資訊。  \(覆寫 [CPane::LoadState](../Topic/CPane::LoadState.md)\)。|  
|[CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md)|從應用程式的資源載入工具列。|  
|[CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md)|從應用程式的資源載入工具列使用 `CMFCToolBarInfo` Helper 類別可讓應用程式使用大型影像。|  
|[CMFCToolBar::OnChangeHot](../Topic/CMFCToolBar::OnChangeHot.md)|呼叫框架，當使用者選取  工具列上的按鈕。|  
|[CMFCToolBar::OnFillBackground](../Topic/CMFCToolBar::OnFillBackground.md)|會呼叫由 [CBasePane::DoPaint](../Topic/CBasePane::DoPaint.md) 框架填滿工具列背景。|  
|[CMFCToolBar::OnReset](../Topic/CMFCToolBar::OnReset.md)|還原工具列還原為其原始狀態。|  
|[CMFCToolBar::OnSetAccData](../Topic/CMFCToolBar::OnSetAccData.md)|\(覆寫 [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)\)。|  
|[CMFCToolBar::OnSetDefaultButtonText](../Topic/CMFCToolBar::OnSetDefaultButtonText.md)|還原工具列按鈕上的文字為其預設狀態。|  
|`CMFCToolBar::OnUpdateCmdUI`|內部使用。|  
|[CMFCToolBar::RemoveAllButtons](../Topic/CMFCToolBar::RemoveAllButtons.md)|從工具列移除所有按鈕。|  
|[CMFCToolBar::RemoveButton](../Topic/CMFCToolBar::RemoveButton.md)|移除按鈕具有指定索引處的工具列。|  
|[CMFCToolBar::RemoveStateFromRegistry](../Topic/CMFCToolBar::RemoveStateFromRegistry.md)|刪除工具列的狀態資訊從 Windows 登錄。|  
|[CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)|用另一個工具列按鈕取代工具列按鈕。|  
|[CMFCToolBar::ResetAll](../Topic/CMFCToolBar::ResetAll.md)|若要還原所有工具列的原始狀態。|  
|[CMFCToolBar::ResetAllImages](../Topic/CMFCToolBar::ResetAllImages.md)|清除在應用程式中所有工具列影像集合。|  
|[CMFCToolBar::RestoreOriginalState](../Topic/CMFCToolBar::RestoreOriginalState.md)|還原工具列的原始狀態。|  
|[CMFCToolBar::SaveState](../Topic/CMFCToolBar::SaveState.md)|將工具列的狀態資訊儲存在 Windows 登錄中。  \(覆寫 [CPane::SaveState](../Topic/CPane::SaveState.md)\)。|  
|`CMFCToolBar::Serialize`|\(覆寫 `CBasePane::Serialize`\)。|  
|[CMFCToolBar::SetBasicCommands](../Topic/CMFCToolBar::SetBasicCommands.md)|設定永遠顯示命令的清單，當使用者按一下  功能表時。|  
|[CMFCToolBar::SetButtonInfo](../Topic/CMFCToolBar::SetButtonInfo.md)|將工具列按鈕的命令 ID、樣式和影像 ID。|  
|[CMFCToolBar::SetButtonStyle](../Topic/CMFCToolBar::SetButtonStyle.md)|將工具列按鈕的樣式指定索引處的。|  
|[CMFCToolBar::SetButtonText](../Topic/CMFCToolBar::SetButtonText.md)|將工具列按鈕的文字標籤。|  
|[CMFCToolBar::SetButtons](../Topic/CMFCToolBar::SetButtons.md)|將工具列的按鈕。|  
|[CMFCToolBar::SetCommandUsageOptions](../Topic/CMFCToolBar::SetCommandUsageOptions.md)|當有不常用命令未出現在應用程式的功能表，指定。|  
|[CMFCToolBar::SetCustomizeMode](../Topic/CMFCToolBar::SetCustomizeMode.md)|可啟用或停用所有工具列的自訂方式在應用程式。|  
|[CMFCToolBar::SetGrayDisabledButtons](../Topic/CMFCToolBar::SetGrayDisabledButtons.md)|指定在工具列上的按鈕是否顯示為暗灰色，或者停用影像是停用的按鈕來使用。|  
|[CMFCToolBar::SetHeight](../Topic/CMFCToolBar::SetHeight.md)|將工具列的高度。|  
|[CMFCToolBar::SetHotBorder](../Topic/CMFCToolBar::SetHotBorder.md)|指定工具列按鈕的色彩。|  
|[CMFCToolBar::SetHotTextColor](../Topic/CMFCToolBar::SetHotTextColor.md)|設定按鈕的工具列按鈕的文字色彩。|  
|[CMFCToolBar::SetLargeIcons](../Topic/CMFCToolBar::SetLargeIcons.md)|指定工具列按鈕是否顯示大圖示。|  
|[CMFCToolBar::SetLockedSizes](../Topic/CMFCToolBar::SetLockedSizes.md)|設定鎖定的按鈕的大小與工具列上的鎖定的影像。|  
|[CMFCToolBar::SetMenuSizes](../Topic/CMFCToolBar::SetMenuSizes.md)|將工具列按鈕和功能表其影像的大小。|  
|[CMFCToolBar::SetNonPermittedCommands](../Topic/CMFCToolBar::SetNonPermittedCommands.md)|設定使用者無法執行命令的清單。|  
|[CMFCToolBar::SetOneRowWithSibling](../Topic/CMFCToolBar::SetOneRowWithSibling.md)|在同一行上放置工具列及其同層級。|  
|[CMFCToolBar::SetPermament](../Topic/CMFCToolBar::SetPermament.md)|指定使用者是否可以關閉工具列。|  
|[CMFCToolBar::SetRouteCommandsViaFrame](../Topic/CMFCToolBar::SetRouteCommandsViaFrame.md)|指定父視窗或主控框架是否傳送命令加入至工具列。|  
|[CMFCToolBar::SetShowTooltips](../Topic/CMFCToolBar::SetShowTooltips.md)|指定這個框架是否顯示工具提示。|  
|[CMFCToolBar::SetSiblingToolBar](../Topic/CMFCToolBar::SetSiblingToolBar.md)|指定工具列的同層級。|  
|[CMFCToolBar::SetSizes](../Topic/CMFCToolBar::SetSizes.md)|在任何指定工具列按鈕的大小和影像。|  
|[CMFCToolBar::SetToolBarBtnText](../Topic/CMFCToolBar::SetToolBarBtnText.md)|在  工具列按鈕的屬性指定。|  
|[CMFCToolBar::SetTwoRowsWithSibling](../Topic/CMFCToolBar::SetTwoRowsWithSibling.md)|在不同的行上放置工具列及其同層級。|  
|[CMFCToolBar::SetUserImages](../Topic/CMFCToolBar::SetUserImages.md)|設定使用者定義的影像集合在應用程式中。|  
|[CMFCToolBar::StretchPane](../Topic/CMFCToolBar::StretchPane.md)|垂直或水平縮放工具列。\(覆寫 [CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)\)。|  
|[CMFCToolBar::TranslateChar](../Topic/CMFCToolBar::TranslateChar.md)|如果指定的按鍵碼對應到有效的鍵盤快速鍵，執行命令按鈕。|  
|[CMFCToolBar::UpdateButton](../Topic/CMFCToolBar::UpdateButton.md)|更新指定按鈕的狀態。|  
|[CMFCToolBar::WrapToolBar](../Topic/CMFCToolBar::WrapToolBar.md)|將放置在指定的維度中的工具列按鈕。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBar::AllowShowOnList](../Topic/CMFCToolBar::AllowShowOnList.md)|決定工具列是否在 \[**自訂**\] 對話方塊的窗格 \[**工具列**\] 的清單隨即顯示。|  
|[CMFCToolBar::CalcMaxButtonHeight](../Topic/CMFCToolBar::CalcMaxButtonHeight.md)|計算指定按鈕的最大高度工具列上的。|  
|[CMFCToolBar::DoPaint](../Topic/CMFCToolBar::DoPaint.md)|會重新繪製工具列。|  
|[CMFCToolBar::DrawButton](../Topic/CMFCToolBar::DrawButton.md)|會重新繪製工具列按鈕。|  
|[CMFCToolBar::DrawSeparator](../Topic/CMFCToolBar::DrawSeparator.md)|會在工具列的分隔符號。|  
|[CMFCToolBar::OnUserToolTip](../Topic/CMFCToolBar::OnUserToolTip.md)|呼叫框架時，按鈕的工具提示會顯示。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBar::m\_bDontScaleImages](../Topic/CMFCToolBar::m_bDontScaleImages.md)|在高 DPI 模式指定工具列是否會縮放影像。|  
|[CMFCToolBar::m\_dblLargeImageRatio](../Topic/CMFCToolBar::m_dblLargeImageRatio.md)|在指定的維度 \(寬度或高度\) 大型影像和維度的比例規則影像之間。|  
  
## 備註  
 若要合併 `CMFCToolBar` 物件加入至您的應用程式，請遵循下列步驟:  
  
1.  將物件加入至 `CMFCToolBar` 主框架視窗。  
  
2.  當您處理主框架視窗的 `WM_CREATE` 訊息時，請呼叫 [CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md) 或 [CMFCToolBar::CreateEx](../Topic/CMFCToolBar::CreateEx.md) 建立工具列和指定其樣式。  
  
3.  呼叫 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md) 指定停駐樣式。  
  
 您可以使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，要插入使用特殊的按鈕 \(例如，下拉式方塊或下拉式工具列，在父資源保留空的按鈕，並取代假設的按鈕是在執行階段。  如需詳細資訊，請參閱 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
 `CMFCToolBar` 是 MFC 程式庫類別的 [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md)、 [CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md)和 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)基底類別。  
  
## 範例  
 下列範例會在 `CMFCToolBar` 類別會示範如何使用各種方法。  這個範例顯示如何設定工具列的 Windows 標籤的文字，將框線，請將  窗格中的樣式和啟用顯示於工具列尾端的 \[**加入或移除按鈕。**\] 按鈕。  這個程式碼片段是 [IE 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_IEDemo#6](../../mfc/reference/codesnippet/CPP/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#8](../../mfc/reference/codesnippet/CPP/cmfctoolbar-class_2.cpp)]  
  
## 需求  
 **標題:** afxtoolbar.h  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md)   
 [CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)