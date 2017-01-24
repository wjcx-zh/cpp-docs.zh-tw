---
title: "CMFCPropertyGridCtrl Class | Microsoft Docs"
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
  - "CMFCPropertyGridCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridCtrl class"
  - "CMFCPropertyGridCtrl::accHitTest method"
  - "CMFCPropertyGridCtrl::accLocation method"
  - "CMFCPropertyGridCtrl::get_accChild method"
  - "CMFCPropertyGridCtrl::get_accDefaultAction method"
  - "CMFCPropertyGridCtrl::get_accDescription method"
  - "CMFCPropertyGridCtrl::get_accName method"
  - "CMFCPropertyGridCtrl::get_accRole method"
  - "CMFCPropertyGridCtrl::get_accState method"
  - "CMFCPropertyGridCtrl::get_accValue method"
  - "CMFCPropertyGridCtrl::PreTranslateMessage method"
ms.assetid: 95877cae-2311-4a2a-9031-0c8c3cf0a5f9
caps.latest.revision: 35
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertyGridCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 支援能夠顯示屬性會依字母順序或階層順序的可編輯的屬性方格控制項。  
  
## 語法  
  
```  
class CMFCPropertyGridCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](../Topic/CMFCPropertyGridCtrl::CMFCPropertyGridCtrl.md)|建構 `CMFCPropertyGridCtrl` 物件。|  
|`CMFCPropertyGridCtrl::~CMFCPropertyGridCtrl`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCPropertyGridCtrl::accHitTest`|呼叫由架構擷取子項目或子物件在畫面上的指定點。  \(覆寫 [CWnd::accHitTest](../Topic/CWnd::accHitTest.md)\)。|  
|`CMFCPropertyGridCtrl::accLocation`|呼叫由架構擷取指定物件的目前螢幕位置。  \(覆寫 [CWnd::accLocation](../Topic/CWnd::accLocation.md)\)。|  
|[CMFCPropertyGridCtrl::accSelect](../Topic/CMFCPropertyGridCtrl::accSelect.md)|呼叫框架修改選取範圍或移動指定物件的鍵盤焦點。  \(覆寫 [CWnd::accSelect](../Topic/CWnd::accSelect.md)\)。|  
|[CMFCPropertyGridCtrl::AddProperty](../Topic/CMFCPropertyGridCtrl::AddProperty.md)|將新的屬性加入屬性方格控制項。|  
|[CMFCPropertyGridCtrl::AlwaysShowUserToolTip](../Topic/CMFCPropertyGridCtrl::AlwaysShowUserToolTip.md)||  
|[CMFCPropertyGridCtrl::CloseColorPopup](../Topic/CMFCPropertyGridCtrl::CloseColorPopup.md)|關閉色彩選取對話方塊。|  
|[CMFCPropertyGridCtrl::Create](../Topic/CMFCPropertyGridCtrl::Create.md)|建立屬性方格控制項並將其附加至屬性方格控制項物件。|  
|[CMFCPropertyGridCtrl::DeleteProperty](../Topic/CMFCPropertyGridCtrl::DeleteProperty.md)|刪除屬性方格控制項的指定屬性。|  
|[CMFCPropertyGridCtrl::DrawControlBarColors](../Topic/CMFCPropertyGridCtrl::DrawControlBarColors.md)||  
|[CMFCPropertyGridCtrl::EnableDescriptionArea](../Topic/CMFCPropertyGridCtrl::EnableDescriptionArea.md)|啟用或停用在屬性清單中顯示的描述區域。|  
|[CMFCPropertyGridCtrl::EnableHeaderCtrl](../Topic/CMFCPropertyGridCtrl::EnableHeaderCtrl.md)|啟用或停用標題控制項在屬性方格控制項的上方。|  
|[CMFCPropertyGridCtrl::EnsureVisible](../Topic/CMFCPropertyGridCtrl::EnsureVisible.md)|移動一個屬性方格控制項並展開屬性項目，直到指定的屬性是可見的。|  
|[CMFCPropertyGridCtrl::ExpandAll](../Topic/CMFCPropertyGridCtrl::ExpandAll.md)|若要展開或摺疊所有屬性方格控制項節點。|  
|[CMFCPropertyGridCtrl::FindItemByData](../Topic/CMFCPropertyGridCtrl::FindItemByData.md)|擷取與使用者定義的 `DWORD` 值的屬性。|  
|`CMFCPropertyGridCtrl::get_accChild`|呼叫由架構擷取一 `IDispatch` 介面位址指定的子系。  \(覆寫 [CWnd::get\_accChild](../Topic/CWnd::get_accChild.md)\)。|  
|[CMFCPropertyGridCtrl::get\_accChildCount](../Topic/CMFCPropertyGridCtrl::get_accChildCount.md)|呼叫由架構擷取屬於這個物件的子系數目。  \(覆寫 [CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md)\)。|  
|`CMFCPropertyGridCtrl::get_accDefaultAction`|呼叫由架構擷取描述物件的預設動作的字串。  \(覆寫 [CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md)\)。|  
|`CMFCPropertyGridCtrl::get_accDescription`|呼叫由架構擷取描述指定物件之視覺外觀的字串。  \(覆寫 [CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md)\)。|  
|[CMFCPropertyGridCtrl::get\_accFocus](../Topic/CMFCPropertyGridCtrl::get_accFocus.md)|呼叫由架構擷取具有鍵盤焦點的物件。  \(覆寫 [CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md)\)。|  
|[CMFCPropertyGridCtrl::get\_accHelp](../Topic/CMFCPropertyGridCtrl::get_accHelp.md)|呼叫由架構擷取物件的 `Help` 屬性字串。  \(覆寫 [CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md)\)。|  
|[CMFCPropertyGridCtrl::get\_accHelpTopic](../Topic/CMFCPropertyGridCtrl::get_accHelpTopic.md)|呼叫由架構擷取 `WinHelp`檔案的完整路徑與指定的物件和適當主題的識別項在該檔案中。  \(覆寫 [CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md)\)。|  
|[CMFCPropertyGridCtrl::get\_accKeyboardShortcut](../Topic/CMFCPropertyGridCtrl::get_accKeyboardShortcut.md)|呼叫由架構擷取指定物件的快速鍵或存取該登錄機碼。  \(覆寫 [CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md)\)。|  
|`CMFCPropertyGridCtrl::get_accName`|呼叫由架構擷取指定物件的名稱。  \(覆寫 [CWnd::get\_accName](../Topic/CWnd::get_accName.md)\)。|  
|`CMFCPropertyGridCtrl::get_accRole`|呼叫由架構擷取描述指定之物件的相關資訊。  \(覆寫 [CWnd::get\_accRole](../Topic/CWnd::get_accRole.md)\)。|  
|[CMFCPropertyGridCtrl::get\_accSelection](../Topic/CMFCPropertyGridCtrl::get_accSelection.md)|呼叫由架構來擷取這個的選項之子系的物件。  \(覆寫 [CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md)\)。|  
|`CMFCPropertyGridCtrl::get_accState`|呼叫由架構擷取指定物件的目前狀態。  \(覆寫 [CWnd::get\_accState](../Topic/CWnd::get_accState.md)\)。|  
|`CMFCPropertyGridCtrl::get_accValue`|呼叫由架構擷取指定物件的值。  \(覆寫 [CWnd::get\_accValue](../Topic/CWnd::get_accValue.md)\)。|  
|[CMFCPropertyGridCtrl::GetBkColor](../Topic/CMFCPropertyGridCtrl::GetBkColor.md)|擷取目前的屬性方格控制項的背景色彩。|  
|[CMFCPropertyGridCtrl::GetBoldFont](../Topic/CMFCPropertyGridCtrl::GetBoldFont.md)|擷取目前屬性方格控制項中的文字以粗體樣式的 Windows 字型。|  
|[CMFCPropertyGridCtrl::GetCurSel](../Topic/CMFCPropertyGridCtrl::GetCurSel.md)|擷取目前選取的屬性。|  
|[CMFCPropertyGridCtrl::GetCustomColors](../Topic/CMFCPropertyGridCtrl::GetCustomColors.md)|擷取在屬性方格控制項項目目前定義的自訂色彩。|  
|[CMFCPropertyGridCtrl::GetDescriptionHeight](../Topic/CMFCPropertyGridCtrl::GetDescriptionHeight.md)|擷取描述區域的高度位於屬性方格控制項的下方。|  
|[CMFCPropertyGridCtrl::GetDescriptionRows](../Topic/CMFCPropertyGridCtrl::GetDescriptionRows.md)|擷取資料列的目前屬性方格控制項的描述範圍的。|  
|[CMFCPropertyGridCtrl::GetHeaderCtrl](../Topic/CMFCPropertyGridCtrl::GetHeaderCtrl.md)|擷取這個架構使用顯示目前屬性方格控制項的內部 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) 物件。|  
|[CMFCPropertyGridCtrl::GetHeaderHeight](../Topic/CMFCPropertyGridCtrl::GetHeaderHeight.md)|擷取屬性方格控制項標題的高度。|  
|[CMFCPropertyGridCtrl::GetLeftColumnWidth](../Topic/CMFCPropertyGridCtrl::GetLeftColumnWidth.md)|擷取目前的屬性方格控制項的左欄的寬度，包含每個屬性的名稱。|  
|[CMFCPropertyGridCtrl::GetListRect](../Topic/CMFCPropertyGridCtrl::GetListRect.md)|擷取屬性方格控制項的週框 \(Bounding Rectangle\)。|  
|[CMFCPropertyGridCtrl::GetProperty](../Topic/CMFCPropertyGridCtrl::GetProperty.md)|擷取指標對應於屬性方格控制項中的指定索引處的屬性物件。|  
|[CMFCPropertyGridCtrl::GetPropertyColumnWidth](../Topic/CMFCPropertyGridCtrl::GetPropertyColumnWidth.md)|擷取包含屬性值資料行的目前寬度。|  
|[CMFCPropertyGridCtrl::GetPropertyCount](../Topic/CMFCPropertyGridCtrl::GetPropertyCount.md)|擷取中的屬性數目屬性方格控制項。|  
|[CMFCPropertyGridCtrl::GetRowHeight](../Topic/CMFCPropertyGridCtrl::GetRowHeight.md)|擷取資料列的高度 \(以屬性方格控制項。|  
|[CMFCPropertyGridCtrl::GetScrollBarCtrl](../Topic/CMFCPropertyGridCtrl::GetScrollBarCtrl.md)|擷取指向儲存在屬性方格控制項中捲軸控制項。  \(覆寫 [CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)\)。|  
|[CMFCPropertyGridCtrl::GetTextColor](../Topic/CMFCPropertyGridCtrl::GetTextColor.md)|擷取屬性項目文字的色彩在目前屬性方格控制項。|  
|`CMFCPropertyGridCtrl::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCPropertyGridCtrl::HitTest](../Topic/CMFCPropertyGridCtrl::HitTest.md)|擷取指標對應於屬性方格控制項中項目的屬性設定為物件，如果指定的點在項目。  這個方法也會指出在含有點的屬性方格控制項的區域。|  
|[CMFCPropertyGridCtrl::InitHeader](../Topic/CMFCPropertyGridCtrl::InitHeader.md)|初始化這個架構使用顯示目前屬性方格控制項的內部 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) 物件。|  
|[CMFCPropertyGridCtrl::IsAlphabeticMode](../Topic/CMFCPropertyGridCtrl::IsAlphabeticMode.md)|表示屬性方格控制項是否在字母的模式。|  
|[CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip](../Topic/CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip.md)||  
|[CMFCPropertyGridCtrl::IsDescriptionArea](../Topic/CMFCPropertyGridCtrl::IsDescriptionArea.md)|指示屬性方格控制項的描述範圍是否已經顯示。|  
|[CMFCPropertyGridCtrl::IsGroupNameFullWidth](../Topic/CMFCPropertyGridCtrl::IsGroupNameFullWidth.md)|表示每個屬性群組名稱是否透過目前的屬性方格控制項的寬度會顯示。|  
|[CMFCPropertyGridCtrl::IsHeaderCtrl](../Topic/CMFCPropertyGridCtrl::IsHeaderCtrl.md)|指示標題控制項是否已經顯示。|  
|[CMFCPropertyGridCtrl::IsMarkModifiedProperties](../Topic/CMFCPropertyGridCtrl::IsMarkModifiedProperties.md)|表示屬性方格控制項顯示如何修改的屬性。|  
|[CMFCPropertyGridCtrl::IsShowDragContext](../Topic/CMFCPropertyGridCtrl::IsShowDragContext.md)|表示此框架是否重新繪製目前的屬性方格控制項的名稱和值資料行中，當使用者調整資料行大小。|  
|[CMFCPropertyGridCtrl::IsVSDotNetLook](../Topic/CMFCPropertyGridCtrl::IsVSDotNetLook.md)|表示屬性方格控制項的外觀是否在中使用 \[.NET 的樣式。|  
|[CMFCPropertyGridCtrl::MarkModifiedProperties](../Topic/CMFCPropertyGridCtrl::MarkModifiedProperties.md)|指定如何顯示修改的屬性。|  
|`CMFCPropertyGridCtrl::PreTranslateMessage`|由類別 [CWinApp](../../mfc/reference/cwinapp-class.md) 將 Windows 訊息，然後才會傳送至 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前。  \(覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\)。|  
|[CMFCPropertyGridCtrl::RemoveAll](../Topic/CMFCPropertyGridCtrl::RemoveAll.md)|從屬性方格控制項中所有屬性的物件。|  
|[CMFCPropertyGridCtrl::ResetOriginalValues](../Topic/CMFCPropertyGridCtrl::ResetOriginalValues.md)|若要還原所有屬性的原始值。|  
|[CMFCPropertyGridCtrl::SetAlphabeticMode](../Topic/CMFCPropertyGridCtrl::SetAlphabeticMode.md)|設定或重設依字母順序排列的方式。|  
|[CMFCPropertyGridCtrl::SetBoolLabels](../Topic/CMFCPropertyGridCtrl::SetBoolLabels.md)|指定布林值的標籤文字。|  
|[CMFCPropertyGridCtrl::SetCurSel](../Topic/CMFCPropertyGridCtrl::SetCurSel.md)|在 \[屬性\] 方格控制項的屬性。|  
|[CMFCPropertyGridCtrl::SetCustomColors](../Topic/CMFCPropertyGridCtrl::SetCustomColors.md)|提供各種屬性方格控制項項目指定自訂色彩。|  
|[CMFCPropertyGridCtrl::SetDescriptionRows](../Topic/CMFCPropertyGridCtrl::SetDescriptionRows.md)|在目前的屬性方格控制項的描述部分指定資料列的顯示。|  
|[CMFCPropertyGridCtrl::SetGroupNameFullWidth](../Topic/CMFCPropertyGridCtrl::SetGroupNameFullWidth.md)|指定是否顯示全型分類名稱屬性群組在目前屬性方格控制項。|  
|[CMFCPropertyGridCtrl::SetListDelimiter](../Topic/CMFCPropertyGridCtrl::SetListDelimiter.md)|定義要用來做為分隔符號的屬性 \(Attribute\) 值清單的字元。|  
|[CMFCPropertyGridCtrl::SetShowDragContext](../Topic/CMFCPropertyGridCtrl::SetShowDragContext.md)|指定這個框架是否重新繪製目前的屬性方格控制項的名稱和值資料行中，當使用者調整資料行大小。|  
|[CMFCPropertyGridCtrl::SetVSDotNetLook](../Topic/CMFCPropertyGridCtrl::SetVSDotNetLook.md)|設定屬性方格控制項中顯示為對 .NET 的樣式。|  
|[CMFCPropertyGridCtrl::UpdateColor](../Topic/CMFCPropertyGridCtrl::UpdateColor.md)|設定目前選取的色彩屬性的色彩值。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertyGridCtrl::AdjustLayout](../Topic/CMFCPropertyGridCtrl::AdjustLayout.md)|重新繪製屬性方格控制項及其屬性。|  
|[CMFCPropertyGridCtrl::CompareProps](../Topic/CMFCPropertyGridCtrl::CompareProps.md)|會呼叫由屬性方格控制項排序屬性。|  
|[CMFCPropertyGridCtrl::EditItem](../Topic/CMFCPropertyGridCtrl::EditItem.md)|呼叫框架，當使用者開始修改屬性。|  
|[CMFCPropertyGridCtrl::EndEditItem](../Topic/CMFCPropertyGridCtrl::EndEditItem.md)|呼叫框架，當使用者停止修改屬性。|  
|[CMFCPropertyGridCtrl::Init](../Topic/CMFCPropertyGridCtrl::Init.md)|呼叫框架初始化屬性方格控制項。|  
|[CMFCPropertyGridCtrl::OnChangeSelection](../Topic/CMFCPropertyGridCtrl::OnChangeSelection.md)|呼叫由架構，在變更目前的選取範圍。|  
|[CMFCPropertyGridCtrl::OnClickButton](../Topic/CMFCPropertyGridCtrl::OnClickButton.md)|呼叫框架，當屬性在按一下  按鈕。|  
|[CMFCPropertyGridCtrl::OnDrawBorder](../Topic/CMFCPropertyGridCtrl::OnDrawBorder.md)|呼叫由架構在屬性方格控制項周圍繪製框線。|  
|[CMFCPropertyGridCtrl::OnDrawDescription](../Topic/CMFCPropertyGridCtrl::OnDrawDescription.md)|呼叫框架繪製描述區域和顯示描述文字。|  
|[CMFCPropertyGridCtrl::OnDrawList](../Topic/CMFCPropertyGridCtrl::OnDrawList.md)|呼叫由架構會顯示於屬性方格控制項的屬性清單。|  
|[CMFCPropertyGridCtrl::OnDrawProperty](../Topic/CMFCPropertyGridCtrl::OnDrawProperty.md)|呼叫由架構會顯示屬性。|  
|[CMFCPropertyGridCtrl::OnPropertyChanged](../Topic/CMFCPropertyGridCtrl::OnPropertyChanged.md)|呼叫框架，當屬性的值變更為。|  
|[CMFCPropertyGridCtrl::OnSelectCombo](../Topic/CMFCPropertyGridCtrl::OnSelectCombo.md)|呼叫框架，當包含下拉式方塊控制項的屬性已選取。|  
|[CMFCPropertyGridCtrl::ValidateItemData](../Topic/CMFCPropertyGridCtrl::ValidateItemData.md)|呼叫由架構驗證屬性資料。|  
  
## 備註  
 `CMFCPropertyGridCtrl` 類別顯示包含 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md) 從類別衍生的可編輯屬性的屬性方格控制項。  每個屬性都代表型別，也可以包含子項目。  屬性方格控制項支援可調整大小的區域中可能會顯示選取屬性的說明的底部。  
  
 若要使用屬性方格控制項，請 `CMFCPropertyGridCtrl` 建構物件 [CMFCPropertyGridCtrl::Create](../Topic/CMFCPropertyGridCtrl::Create.md) 再呼叫方法。  使用 [CMFCPropertyGridCtrl::AddProperty](../Topic/CMFCPropertyGridCtrl::AddProperty.md) 方法將屬性加入至清單。  
  
## 選取屬性  
 而是表示值，屬性項目可以啟動讓使用者選取色彩、檔案或字型的對話方塊。  
  
 下表列出四個選取屬性型別:  
  
|類別|描述|  
|--------|--------|  
|[CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)|用來指定 String， Boolean，日期的值等的通用屬性。|  
|[CMFCPropertyGridColorProperty Class](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)|用來選取色彩值的屬性。|  
|[CMFCPropertyGridFileProperty Class](../../mfc/reference/cmfcpropertygridfileproperty-class.md)|用來選取檔案的屬性。|  
|[CMFCPropertyGridFontProperty Class](../../mfc/reference/cmfcpropertygridfontproperty-class.md)|用來選取字型的屬性。|  
  
## 插圖  
 下圖說明顯示屬性以兩種方式的其中一個屬性方格控制項。  第一個圖中以階層方式顯示屬性，第二個字母顯示屬性。  
  
 ![屬性清單 PropertySheet](../../mfc/reference/media/proplist.png "PropList")  
  
## 範例  
 您可以使用類別，在 `CMFCPropertyGridCtrl` 的各種方法。下列範例將示範如何設定屬性方格控制項物件。  範例會示範如何啟用標題控制項，可描述區域，並將屬性方格控制項的外觀。  這個範例也會示範如何設定控制項的字母順序模式，讓它根據它們的屬性名稱中控制項的排序所有屬性以及如何設定的屬性方格控制項中各個項目的自訂色彩。  這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#14](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#14)]  
[!CODE [NVC_MFC_NewControls#16](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#16)]  
[!CODE [NVC_MFC_NewControls#20](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#20)]  
[!CODE [NVC_MFC_NewControls#21](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#21)]  
[!CODE [NVC_MFC_NewControls#24](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#24)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)  
  
## 需求  
 **標題:** afxpropertygridctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)