---
title: "CMFCToolBarMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarMenuButton class"
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCToolBarMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含一個快顯功能表的工具列按鈕。  
  
## 語法  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](../Topic/CMFCToolBarMenuButton::CMFCToolBarMenuButton.md)|建構 `CMFCToolBarMenuButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarMenuButton::CompareWith](../Topic/CMFCToolBarMenuButton::CompareWith.md)|這個執行個體與提供的物件相比較。 `CMFCToolBarButton` \(覆寫 [CMFCToolBarButton::CompareWith](../Topic/CMFCToolBarButton::CompareWith.md)\)。|  
|[CMFCToolBarMenuButton::CopyFrom](../Topic/CMFCToolBarMenuButton::CopyFrom.md)|複製到另一個工具列按鈕的屬性設定為目前的按鈕。  \(覆寫 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)\)。|  
|[CMFCToolBarMenuButton::CreateFromMenu](../Topic/CMFCToolBarMenuButton::CreateFromMenu.md)|初始化從 Windows 功能表控制代碼的工具列上的  功能表上的。|  
|[CMFCToolBarMenuButton::CreateMenu](../Topic/CMFCToolBarMenuButton::CreateMenu.md)|建立包含在工具列上的  功能表上的命令的視窗功能表。  將控制代碼傳回給 Windows 功能表中的。|  
|[CMFCToolBarMenuButton::CreatePopupMenu](../Topic/CMFCToolBarMenuButton::CreatePopupMenu.md)|建立快顯功能表物件 \([CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)\) 顯示工具列上的  功能表上的。|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](../Topic/CMFCToolBarMenuButton::EnableQuickCustomize.md)||  
|[CMFCToolBarMenuButton::GetCommands](../Topic/CMFCToolBarMenuButton::GetCommands.md)|允許在工具列上的  功能表上的命令清單的唯讀存取。|  
|[CMFCToolBarMenuButton::GetImageRect](../Topic/CMFCToolBarMenuButton::GetImageRect.md)|擷取按鈕影像的週框 \(Bounding Rectangle\)。|  
|[CMFCToolBarMenuButton::GetPaletteRows](../Topic/CMFCToolBarMenuButton::GetPaletteRows.md)|為功能表在調色盤模式時，傳回資料列數快顯功能表的。|  
|[CMFCToolBarMenuButton::GetPopupMenu](../Topic/CMFCToolBarMenuButton::GetPopupMenu.md)|傳回指向與按鈕關聯的快顯功能表物件。|  
|[CMFCToolBarMenuButton::HasButton](../Topic/CMFCToolBarMenuButton::HasButton.md)||  
|[CMFCToolBarMenuButton::HaveHotBorder](../Topic/CMFCToolBarMenuButton::HaveHotBorder.md)|確定按鈕的框線是否顯示，當使用者選取按鈕。  \(覆寫 [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)\)。|  
|[CMFCToolBarMenuButton::IsBorder](../Topic/CMFCToolBarMenuButton::IsBorder.md)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](../Topic/CMFCToolBarMenuButton::IsClickedOnMenu.md)||  
|[CMFCToolBarMenuButton::IsDroppedDown](../Topic/CMFCToolBarMenuButton::IsDroppedDown.md)|決定快顯功能表是否已經顯示。|  
|[CMFCToolBarMenuButton::IsEmptyMenuAllowed](../Topic/CMFCToolBarMenuButton::IsEmptyMenuAllowed.md)|呼叫框架會決定使用者是否可以從選取的功能表項目的子功能表。|  
|[CMFCToolBarMenuButton::IsExclusive](../Topic/CMFCToolBarMenuButton::IsExclusive.md)|判斷  按鈕，也就是，是否以獨佔模式快顯功能表是否保持開啟，即使當使用者將游標移至另一個工具列或按鈕的指標。|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](../Topic/CMFCToolBarMenuButton::IsMenuPaletteMode.md)|決定快顯功能表是否在調色盤模式。|  
|[CMFCToolBarMenuButton::IsQuickMode](../Topic/CMFCToolBarMenuButton::IsQuickMode.md)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](../Topic/CMFCToolBarMenuButton::IsTearOffMenu.md)|決定快顯功能表是否具有 Tear\-Off 列。|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](../Topic/CMFCToolBarMenuButton::OnAfterCreatePopupMenu.md)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](../Topic/CMFCToolBarMenuButton::OnBeforeDrag.md)|指定按鈕是否可以拖曳。  \(覆寫 [CMFCToolBarButton::OnBeforeDrag](../Topic/CMFCToolBarButton::OnBeforeDrag.md)\)。|  
|[CMFCToolBarMenuButton::OnCalculateSize](../Topic/CMFCToolBarMenuButton::OnCalculateSize.md)|呼叫框架計算按鈕的大小指定的裝置內容和停駐狀態的。  \(覆寫 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)\)。|  
|[CMFCToolBarMenuButton::OnCancelMode](../Topic/CMFCToolBarMenuButton::OnCancelMode.md)|呼叫由架構處理 [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) 訊息。  \(覆寫 [CMFCToolBarButton::OnCancelMode](../Topic/CMFCToolBarButton::OnCancelMode.md)\)。|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](../Topic/CMFCToolBarMenuButton::OnChangeParentWnd.md)|呼叫框架，在按一下插入新的工具列。  \(覆寫 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)\)。|  
|[CMFCToolBarMenuButton::OnClick](../Topic/CMFCToolBarMenuButton::OnClick.md)|呼叫框架，當使用者按一下滑鼠按鈕。  \(覆寫 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)\)。|  
|[CMFCToolBarMenuButton::OnClickMenuItem](../Topic/CMFCToolBarMenuButton::OnClickMenuItem.md)|呼叫框架，當使用者在快顯功能表的項目。|  
|[CMFCToolBarMenuButton::OnContextHelp](../Topic/CMFCToolBarMenuButton::OnContextHelp.md)|呼叫框架，其在父代 \(Parent\) 工具列處理 `WM_HELPHITTEST` 訊息。  \(覆寫 [CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md)\)。|  
|[CMFCToolBarMenuButton::OnDraw](../Topic/CMFCToolBarMenuButton::OnDraw.md)|使用指定的樣式和選項，會由架構來繪製按鈕。  \(覆寫 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)\)。|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarMenuButton::OnDrawOnCustomizeList.md)|呼叫框架會在 \[**自訂**\] 對話方塊的 \[**命令**\] 窗格的按鈕。  \(覆寫 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)\)。|  
|[CMFCToolBarMenuButton::OpenPopupMenu](../Topic/CMFCToolBarMenuButton::OpenPopupMenu.md)|呼叫由架構，在使用者開啟快顯功能表。|  
|[CMFCToolBarMenuButton::ResetImageToDefault](../Topic/CMFCToolBarMenuButton::ResetImageToDefault.md)|設定為預設值與按鈕關聯的影像。  \(覆寫 [CMFCToolBarButton::ResetImageToDefault](../Topic/CMFCToolBarButton::ResetImageToDefault.md)\)。|  
|[CMFCToolBarMenuButton::SaveBarState](../Topic/CMFCToolBarMenuButton::SaveBarState.md)|將工具列按鈕的狀態。  \(覆寫 [CMFCToolBarButton::SaveBarState](../Topic/CMFCToolBarButton::SaveBarState.md)\)。|  
|[CMFCToolBarMenuButton::Serialize](../Topic/CMFCToolBarMenuButton::Serialize.md)|從檔案讀取或寫入的這個物件為檔案。  \(覆寫 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)\)。|  
|[CMFCToolBarMenuButton::SetACCData](../Topic/CMFCToolBarMenuButton::SetACCData.md)|填入可及性資料所提供的 `CAccessibilityData` 物件從工具列按鈕。  \(覆寫 [CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md)\)。|  
|[CMFCToolBarMenuButton::SetMenuOnly](../Topic/CMFCToolBarMenuButton::SetMenuOnly.md)|指定按鈕是否可以加入至工具列。|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](../Topic/CMFCToolBarMenuButton::SetMenuPaletteMode.md)|指定快顯功能表是否在調色盤模式。|  
|[CMFCToolBarMenuButton::SetMessageWnd](../Topic/CMFCToolBarMenuButton::SetMessageWnd.md)||  
|[CMFCToolBarMenuButton::SetRadio](../Topic/CMFCToolBarMenuButton::SetRadio.md)|強制工具列功能表按鈕所顯示的圖示表示已選取這個核取方塊。|  
|[CMFCToolBarMenuButton::SetTearOff](../Topic/CMFCToolBarMenuButton::SetTearOff.md)|提供快顯功能表指定 Tear\-Off 列 ID。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](../Topic/CMFCToolBarMenuButton::DrawDocumentIcon.md)|在  功能表上繪製按鈕的圖示。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarMenuButton::m\_bAlwaysCallOwnerDraw](../Topic/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw.md)|如果 `TRUE`，架構一定會呼叫 [CFrameWndEx::OnDrawMenuImage](../Topic/CFrameWndEx::OnDrawMenuImage.md) ，在繪製按鈕。|  
  
## 備註  
 `CMFCToolBarMenuButton` 可能會顯示為功能表、有子功能表，按鈕會執行命令或顯示功能表的功能表項目，或只顯示功能表上的  按鈕。  只要指定參數判斷功能表按鈕的行為和外觀 \(例如與建構函式 `CMFCToolbarMenuButton::CMFCToolbarMenuButton`之按鈕的影像、文字、功能表控制代碼和訂單 ID。  
  
 從 `CMFCToolbarMenuButton` 衍生自類別的自訂類別必須使用 [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) 巨集。  當應用程式關閉時， [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 巨集便會產生錯誤。  
  
## 範例  
 下列範例示範如何設定 `CMFCToolBarMenuButton` 物件。  程式碼將示範如何指定下拉式功能表在調色盤模式以及建立的 Tear\-Off 列指定 ID，則當使用者拖曳功能表按鈕功能表列時。  這個程式碼片段是 [文字填補範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#10](../../mfc/reference/codesnippet/CPP/cmfctoolbarmenubutton-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## 需求  
 **標題:** afxtoolbarmenubutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)