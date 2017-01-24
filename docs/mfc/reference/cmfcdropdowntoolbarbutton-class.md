---
title: "CMFCDropDownToolbarButton Class | Microsoft Docs"
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
  - "CMFCDropDownToolbarButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownToolbarButton class"
  - "OnCancelMode method"
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
caps.latest.revision: 31
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDropDownToolbarButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

的行為與一般按鈕的工具列按鈕的類型，當按一下。  不過，它會開啟一個下拉式工具列 \([CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) ，如果使用者按下並按住下拉工具列按鈕。  
  
## 語法  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../Topic/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton.md)|建構 `CMFCDropDownToolbarButton` 物件。|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCDropDownToolbarButton::CopyFrom](../Topic/CMFCDropDownToolbarButton::CopyFrom.md)|複製到另一個工具列按鈕的屬性設定為目前的按鈕。  \(覆寫 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)\)。|  
|`CMFCDropDownToolbarButton::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCDropDownToolbarButton::DropDownToolbar](../Topic/CMFCDropDownToolbarButton::DropDownToolbar.md)|開啟下拉式工具列。|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](../Topic/CMFCDropDownToolbarButton::ExportToMenuButton.md)|複製的工具列按鈕上的文字加入至功能表。  \(覆寫 [CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)\)。|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](../Topic/CMFCDropDownToolbarButton::GetDropDownToolBar.md)|擷取與按鈕關聯的下拉工具列。|  
|`CMFCDropDownToolbarButton::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCDropDownToolbarButton::IsDropDown](../Topic/CMFCDropDownToolbarButton::IsDropDown.md)|判斷下拉式工具列是否目前開啟。|  
|[CMFCDropDownToolbarButton::IsExtraSize](../Topic/CMFCDropDownToolbarButton::IsExtraSize.md)|判斷按鈕是否可以顯示具有擴充的框線。  \(覆寫 [CMFCToolBarButton::IsExtraSize](../Topic/CMFCToolBarButton::IsExtraSize.md)\)。|  
|[CMFCDropDownToolbarButton::OnCalculateSize](../Topic/CMFCDropDownToolbarButton::OnCalculateSize.md)|呼叫框架計算按鈕的大小指定的裝置內容和停駐狀態的。  \(覆寫 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)\)。|  
|`CMFCDropDownToolbarButton::OnCancelMode`|呼叫由架構處理 [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) 訊息。  \(覆寫 `CMCToolBarButton::OnCancelMode`\)。|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](../Topic/CMFCDropDownToolbarButton::OnChangeParentWnd.md)|呼叫框架，在按一下插入新的工具列。  \(覆寫 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)\)。|  
|[CMFCDropDownToolbarButton::OnClick](../Topic/CMFCDropDownToolbarButton::OnClick.md)|呼叫框架，當使用者按一下滑鼠按鈕。  \(覆寫 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)\)。|  
|[CMFCDropDownToolbarButton::OnClickUp](../Topic/CMFCDropDownToolbarButton::OnClickUp.md)|呼叫框架，使用者放開滑鼠按鈕。  \(覆寫 [CMFCToolBarButton::OnClickUp](../Topic/CMFCToolBarButton::OnClickUp.md)\)。|  
|[CMFCDropDownToolbarButton::OnContextHelp](../Topic/CMFCDropDownToolbarButton::OnContextHelp.md)|呼叫框架，其在父代 \(Parent\) 工具列處理 `WM_HELPHITTEST` 訊息。  \(覆寫 [CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md)\)。|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](../Topic/CMFCDropDownToolbarButton::OnCustomizeMenu.md)|當應用程式會在父代 \(Parent\) 工具列時，就會使用捷徑功能表修改所提供的功能表。  \(覆寫 [CMFCToolBarButton::OnCustomizeMenu](../Topic/CMFCToolBarButton::OnCustomizeMenu.md)\)。|  
|[CMFCDropDownToolbarButton::OnDraw](../Topic/CMFCDropDownToolbarButton::OnDraw.md)|使用指定的樣式和選項，會由架構來繪製按鈕。  \(覆寫 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)\)。|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](../Topic/CMFCDropDownToolbarButton::OnDrawOnCustomizeList.md)|呼叫框架會在 \[**自訂**\] 對話方塊的 \[**命令**\] 窗格的按鈕。  \(覆寫 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)\)。|  
|[CMFCDropDownToolbarButton::Serialize](../Topic/CMFCDropDownToolbarButton::Serialize.md)|從檔案讀取或寫入的這個物件為檔案。  \(覆寫 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)\)。|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](../Topic/CMFCDropDownToolbarButton::SetDefaultCommand.md)|設定這個框架的預設命令使用者何時按一下  按鈕。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCDropDownToolbarButton::m\_uiShowBarDelay](../Topic/CMFCDropDownToolbarButton::m_uiShowBarDelay.md)|指定使用者必須按住滑鼠按鈕時，在下拉式工具列顯示之前。|  
  
## 備註  
 `CMFCDropDownToolBarButton` 與一般按鈕在於它具有小型的向上按鈕的右下角。  在使用者選取按鈕從工具列上的下拉式之後，架構會顯示於最上層的工具列按鈕 \(具有小型的向上按鈕的圖示會顯示在右下角\)。  
  
 如需如何實作一個下拉式工具列的詳細資訊，請參閱 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)。  
  
 `CMFCDropDownToolBarButton` 物件可以匯出至 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) 物件並顯示為具有快顯功能表中的功能表按鈕。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## 需求  
 **標題:** afxdropdowntoolbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)