---
title: "CMFCToolBarEditBoxButton Class | Microsoft Docs"
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
  - "OnDraw"
  - "CMFCToolBarEditBoxButton::OnDrawOnCustomizeList"
  - "CMFCToolBarEditBoxButton.SetACCData"
  - "CMFCToolBarEditBoxButton::OnDraw"
  - "OnCalculateSize"
  - "SetACCData"
  - "CMFCToolBarEditBoxButton"
  - "CMFCToolBarEditBoxButton::SetACCData"
  - "CMFCToolBarEditBoxButton::Serialize"
  - "CMFCToolBarEditBoxButton.OnDraw"
  - "CMFCToolBarEditBoxButton.OnDrawOnCustomizeList"
  - "CMFCToolBarEditBoxButton::OnCalculateSize"
  - "Serialize"
  - "CMFCToolBarEditBoxButton.Serialize"
  - "CMFCToolBarEditBoxButton.OnCalculateSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarEditBoxButton class"
  - "OnCalculateSize method"
  - "OnDraw method"
  - "OnDrawOnCustomizeList method"
  - "Serialize method"
  - "SetACCData method"
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarEditBoxButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含編輯控制項的工具列按鈕 \([CEdit Class](../../mfc/reference/cedit-class.md)\)。  
  
## 語法  
  
```  
class CMFCToolBarEditBoxButton : public CMFCToolBarButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](../Topic/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton.md)|建構 `CMFCToolBarEditBoxButton` 物件。|  
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarEditBoxButton::CanBeStretched](../Topic/CMFCToolBarEditBoxButton::CanBeStretched.md)|指定使用者是否可以在自訂中自動縮放的按鈕。  \(覆寫 [CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md)\)。|  
|[CMFCToolBarEditBoxButton::CopyFrom](../Topic/CMFCToolBarEditBoxButton::CopyFrom.md)|複製到另一個工具列按鈕的屬性設定為目前的按鈕。  \(覆寫 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)\)。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](../Topic/CMFCToolBarEditBoxButton::CreateEdit.md)|建立按鈕的新的編輯控制項。|  
|`CMFCToolBarEditBoxButton::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCToolBarEditBoxButton::GetByCmd](../Topic/CMFCToolBarEditBoxButton::GetByCmd.md)|擷取具有指定的命令 ID. 之應用程式的第一 `CMFCToolBarEditBoxButton` 物件|  
|[CMFCToolBarEditBoxButton::GetContentsAll](../Topic/CMFCToolBarEditBoxButton::GetContentsAll.md)|擷取具有指定的命令 ID. 第一個編輯方塊工具列控制項的文字。|  
|[CMFCToolBarEditBoxButton::GetContextMenuID](../Topic/CMFCToolBarEditBoxButton::GetContextMenuID.md)|擷取與按鈕關聯的捷徑功能表的資源 ID。|  
|[CMFCToolBarEditBoxButton::GetEditBorder](../Topic/CMFCToolBarEditBoxButton::GetEditBorder.md)|擷取編輯方塊按鈕的編輯部分的週框 \(Bounding Rectangle\)。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](../Topic/CMFCToolBarEditBoxButton::GetEditBox.md)|會將指標傳至按鈕中內嵌的編輯控制項。|  
|[CMFCToolBarEditBoxButton::GetHwnd](../Topic/CMFCToolBarEditBoxButton::GetHwnd.md)|擷取與工具列按鈕的視窗控制代碼。  \(覆寫 [CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md)\)。|  
|[CMFCToolBarEditBoxButton::GetInvalidateRect](../Topic/CMFCToolBarEditBoxButton::GetInvalidateRect.md)|擷取按鈕的工作區的本機必須重繪。  \(覆寫 [CMFCToolBarButton::GetInvalidateRect](../Topic/CMFCToolBarButton::GetInvalidateRect.md)\)。|  
|`CMFCToolBarEditBoxButton::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCToolBarEditBoxButton::HaveHotBorder](../Topic/CMFCToolBarEditBoxButton::HaveHotBorder.md)|確定按鈕的框線是否顯示，當使用者按一下  按鈕。  \(覆寫 [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)\)。|  
|[CMFCToolBarEditBoxButton::IsFlatMode](../Topic/CMFCToolBarEditBoxButton::IsFlatMode.md)|判斷編輯方塊按鈕是否有平面樣式。|  
|[CMFCToolBarEditBoxButton::NotifyCommand](../Topic/CMFCToolBarEditBoxButton::NotifyCommand.md)|指定按鈕是否處理 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 訊息。  \(覆寫 [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)\)。|  
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](../Topic/CMFCToolBarEditBoxButton::OnAddToCustomizePage.md)|呼叫框架，該按鈕會加入 \[**自訂**\] 對話方塊。  \(覆寫 [CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md)\)。|  
|`CMFCToolBarEditBoxButton::OnCalculateSize`|呼叫框架計算按鈕的大小指定的裝置內容和停駐狀態的。  \(覆寫 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)\)。|  
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](../Topic/CMFCToolBarEditBoxButton::OnChangeParentWnd.md)|呼叫框架，在按一下插入新的工具列。  \(覆寫 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)\)。|  
|[CMFCToolBarEditBoxButton::OnClick](../Topic/CMFCToolBarEditBoxButton::OnClick.md)|呼叫框架，當使用者按一下滑鼠按鈕。  \(覆寫 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)\)。|  
|[CMFCToolBarEditBoxButton::OnCtlColor](../Topic/CMFCToolBarEditBoxButton::OnCtlColor.md)|呼叫框架，其在父代 \(Parent\) 工具列處理 `WM_CTLCOLOR` 訊息。  \(覆寫 [CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md)\)。|  
|`CMFCToolBarEditBoxButton::OnDraw`|使用指定的樣式和選項，會由架構來繪製按鈕。  \(覆寫 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)\)。|  
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|呼叫框架會在 \[**自訂**\] 對話方塊的 \[**命令**\] 窗格的按鈕。  \(覆寫 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)\)。|  
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](../Topic/CMFCToolBarEditBoxButton::OnGlobalFontsChanged.md)|呼叫框架，其在全域已經變更。  \(覆寫 [CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md)\)。|  
|[CMFCToolBarEditBoxButton::OnMove](../Topic/CMFCToolBarEditBoxButton::OnMove.md)|呼叫框架，其在父代 \(Parent\) 工具列移動。  \(覆寫 [CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md)\)。|  
|[CMFCToolBarEditBoxButton::OnShow](../Topic/CMFCToolBarEditBoxButton::OnShow.md)|呼叫框架，該按鈕會變成可見或不可見的。  \(覆寫 [CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md)\)。|  
|[CMFCToolBarEditBoxButton::OnSize](../Topic/CMFCToolBarEditBoxButton::OnSize.md)|呼叫框架，其在父代 \(Parent\) 工具列將變更的按鈕的大小調整它的大小或位置和這項變更的原因。  \(覆寫 [CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md)\)。|  
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](../Topic/CMFCToolBarEditBoxButton::OnUpdateToolTip.md)|呼叫框架，其在父代 \(Parent\) 工具列更新它的工具提示文字。  \(覆寫 [CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md)\)。|  
|`CMFCToolBarEditBoxButton::Serialize`|從檔案讀取或寫入的這個物件為檔案。  \(覆寫 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)\)。|  
|`CMFCToolBarEditBoxButton::SetACCData`|填入可及性資料所提供的 `CAccessibilityData` 物件從工具列按鈕。  \(覆寫 [CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md)\)。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](../Topic/CMFCToolBarEditBoxButton::SetContents.md)|設定按鈕的編輯控制項的文字。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](../Topic/CMFCToolBarEditBoxButton::SetContentsAll.md)|尋找具有指定的命令 ID 的編輯控制項按鈕，並將該按鈕編輯控制項的文字。|  
|[CMFCToolBarEditBoxButton::SetContextMenuID](../Topic/CMFCToolBarEditBoxButton::SetContextMenuID.md)|指定與按鈕相關聯的捷徑功能表的資源 ID。|  
|[CMFCToolBarEditBoxButton::SetFlatMode](../Topic/CMFCToolBarEditBoxButton::SetFlatMode.md)|在應用程式指定編輯方塊按鈕平面樣式外觀。|  
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](../Topic/CMFCToolBarEditBoxButton::SetStyle.md)|指定按鈕的樣式。  \(覆寫 [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)\)。|  
  
## 備註  
 若要將編輯方塊按鈕加入至工具列，請依照下列步驟執行:  
  
 1.  為按鈕保留虛擬資源 ID 在父代 \(Parent\) 工具列資源。  
  
 2.  建構 `CMFCToolBarEditBoxButton` 物件。  
  
 3.  您可以使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，在處理 `AFX_WM_RESETTOOLBAR` 訊息的訊息處理常式，以新的下拉式方塊按鈕取代空的按鈕。  
  
 如需詳細資訊，請參閱 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## 範例  
 下列範例會在 `CMFCToolBarEditBoxButton` 類別會示範如何使用各種方法。  這個範例示範如何指定使用者可以在自訂中自動縮放的按鈕時，指定按鈕的框線顯示，當使用者在應用程式中按一下  按鈕，將文字方塊控制項中的文字，指定編輯方塊按鈕平面樣式外觀，並指定工具列編輯方塊控制項的樣式時。  
  
 [!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/CPP/cmfctoolbareditboxbutton-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)  
  
## 需求  
 **標題:** afxtoolbareditboxbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)