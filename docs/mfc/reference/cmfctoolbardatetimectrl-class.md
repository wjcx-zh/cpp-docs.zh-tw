---
title: "CMFCToolBarDateTimeCtrl Class | Microsoft Docs"
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
  - "OnDrawOnCustomizeList"
  - "CMFCToolBarDateTimeCtrl::OnDraw"
  - "OnDraw"
  - "CMFCToolBarDateTimeCtrl.Serialize"
  - "CMFCToolBarDateTimeCtrl.OnSize"
  - "CMFCToolBarDateTimeCtrl.OnDrawOnCustomizeList"
  - "OnSize"
  - "OnCalculateSize"
  - "CMFCToolBarDateTimeCtrl"
  - "CMFCToolBarDateTimeCtrl::OnCalculateSize"
  - "SetStyle"
  - "CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList"
  - "CMFCToolBarDateTimeCtrl.OnDraw"
  - "CMFCToolBarDateTimeCtrl.SetStyle"
  - "CMFCToolBarDateTimeCtrl::SetStyle"
  - "CMFCToolBarDateTimeCtrl.OnCalculateSize"
  - "CMFCToolBarDateTimeCtrl::Serialize"
  - "CMFCToolBarDateTimeCtrl::OnSize"
  - "Serialize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarDateTimeCtrl class"
  - "OnCalculateSize method"
  - "OnDraw method"
  - "OnDrawOnCustomizeList method"
  - "OnSize method"
  - "Serialize method"
  - "SetStyle method"
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
caps.latest.revision: 30
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarDateTimeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含日期時間選擇器控制項的工具列按鈕。  
  
## 語法  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](../Topic/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl.md)|建構 `CMFCToolBarDateTimeCtrl` 物件。|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](../Topic/CMFCToolBarDateTimeCtrl::CanBeStretched.md)|指定使用者是否可以在自訂中自動縮放的按鈕。  \(覆寫 [CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md)\)。|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](../Topic/CMFCToolBarDateTimeCtrl::CopyFrom.md)|複製到另一個工具列按鈕的屬性設定為目前的按鈕。  \(覆寫 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)\)。|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|保留供未來使用。|  
|[CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)|複製的工具列按鈕上的文字加入至功能表。|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](../Topic/CMFCToolBarDateTimeCtrl::GetByCmd.md)|擷取具有指定的命令 ID. 之應用程式的第一 `CMFCToolBarDateTimeCtrl` 物件|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](../Topic/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl.md)|傳回指向日期時間選擇器控制項。|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](../Topic/CMFCToolBarDateTimeCtrl::GetHwnd.md)|擷取與工具列按鈕的視窗控制代碼。  \(覆寫 [CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md)\)。|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCToolBarDateTimeCtrl::GetTime](../Topic/CMFCToolBarDateTimeCtrl::GetTime.md)|從日期時間選擇器控制項在指定的 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) 結構取得選取的時間來放置。|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](../Topic/CMFCToolBarDateTimeCtrl::GetTimeAll.md)|傳回具有指定的命令 ID. 的時間選擇器控制項按鈕之選項的時間。|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](../Topic/CMFCToolBarDateTimeCtrl::HaveHotBorder.md)|確定按鈕的框線是否顯示，當使用者選取按鈕。  \(覆寫 [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)\)。|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](../Topic/CMFCToolBarDateTimeCtrl::NotifyCommand.md)|指定按鈕是否處理 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 訊息。  \(覆寫 [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](../Topic/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage.md)|呼叫框架，該按鈕會加入 \[**自訂**\] 對話方塊。  \(覆寫 [CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md)\)。|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|呼叫框架計算按鈕的大小指定的裝置內容和停駐狀態的。  \(覆寫 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](../Topic/CMFCToolBarDateTimeCtrl::OnChangeParentWnd.md)|呼叫框架，在按一下插入新的工具列。  \(覆寫 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnClick](../Topic/CMFCToolBarDateTimeCtrl::OnClick.md)|呼叫框架，當使用者按一下控制項。  \(覆寫 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](../Topic/CMFCToolBarDateTimeCtrl::OnCtlColor.md)|呼叫框架，其在父代 \(Parent\) 工具列處理 `WM_CTLCOLOR` 訊息。  \(覆寫 [CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md)\)。|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|使用指定的樣式和選項，會由架構來繪製按鈕。  \(覆寫 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)\)。|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|呼叫框架會在 \[**自訂**\] 對話方塊的 \[**命令**\] 窗格的按鈕。  \(覆寫 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](../Topic/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged.md)|呼叫框架，其在全域已經變更。  \(覆寫 [CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnMove](../Topic/CMFCToolBarDateTimeCtrl::OnMove.md)|呼叫框架，其在父代 \(Parent\) 工具列移動。  \(覆寫 [CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnShow](../Topic/CMFCToolBarDateTimeCtrl::OnShow.md)|呼叫框架，該按鈕會變成可見或不可見的。  \(覆寫 [CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md)\)。|  
|`CMFCToolBarDateTimeCtrl::OnSize`|呼叫框架，其在父代 \(Parent\) 工具列將變更的按鈕的大小調整它的大小或位置和這項變更的原因。  \(覆寫 [CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md)\)。|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](../Topic/CMFCToolBarDateTimeCtrl::OnUpdateToolTip.md)|呼叫框架，其在父代 \(Parent\) 工具列更新它的工具提示文字。  \(覆寫 [CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md)\)。|  
|`CMFCToolBarDateTimeCtrl::Serialize`|從檔案讀取或寫入的這個物件為檔案，覆寫 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)\(\)。|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|設定工具列按鈕的樣式。  \(覆寫 [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)\)。|  
|[CMFCToolBarDateTimeCtrl::SetTime](../Topic/CMFCToolBarDateTimeCtrl::SetTime.md)|設定時間和日期時間選擇器控制項。|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](../Topic/CMFCToolBarDateTimeCtrl::SetTimeAll.md)|設定時間和日期在具有指定的命令 ID. 時間選擇器控制項的所有執行個體。|  
  
## 備註  
 如需如何使用的範例、日期時間選擇器控制項，請參閱 ToolbarDateTimePicker 範例專案。  如需如何將按鈕控制項的相關資訊加入至工具列，請參閱 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## 需求  
 **標題:** afxtoolbardatetimectrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)